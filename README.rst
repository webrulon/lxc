LXC - Linux Containers
======================

`LXC`_ can be thought of as the middle ground between a chroot on steriods and
a full fledged virtual machine. LXC is a userspace interface to the Linux
kernel containment features (such as namespaces and control groups), allowing
sandboxing processes from one another and controlling their resource
allocations. 

This appliance includes all the standard features in `TurnKey Core`_, and on
top of that:

- Includes `TurnKey LXC template`_:

    - Download and create a container of any TurnKey appliance.
    - Insert specified inithooks.conf into container for preseeding.
    - Supports configuration of network link (e.g., br0, natbr0, none).
    - Supports configuration of apt proxy.
    - Generic enough to be used on any LXC enabled distribution.

- Easily expose NAT containers services:

    - `nginx-proxy`_: Expose a containers web services to the network by
      creating an nginx site configuration to proxy all web requests
      (ports 80, 443, 12320, 12321, 12322) destined for a specific
      domain to the container on the corresponding ports.
    - `iptables-nat`_: Expose a containers non-web (e.g., SSH) service
      to the network by configuring iptables on the host to forward the
      traffic it recieves on port X to the container on port Y.

- LXC appliance configurations:

    - Preconfigured network bridge interface (br0).
    - Preconfigured network NAT bridge interface (natbr0).
    - Preconfigured dnsmasq on natbr0 providing DHCP and DNS services.
      Containers can be referenced by hostname or hostname.local.lxc
    - Includes apt-cacher-ng, binding to natbr0 interface.
    - Includes TurnKey web control panel (convenience).
    - Includes example inithooks configuration for preseeding (convenience).
    - IP forwarding and control groups enabled.

See the `Usage documentation`_ for further details.

Credentials *(passwords set at first boot)*
-------------------------------------------

-  Webmin, SSH: username **root**

.. _LXC: http://linuxcontainers.org
.. _TurnKey Core: http://www.turnkeylinux.org/core
.. _TurnKey LXC template: https://github.com/turnkeylinux-apps/lxc/blob/master/overlay/usr/share/lxc/templates/lxc-turnkey
.. _nginx-proxy: https://github.com/turnkeylinux-apps/lxc/blob/master/overlay/usr/local/bin/nginx-proxy
.. _iptables-nat: https://github.com/turnkeylinux-apps/lxc/blob/master/overlay/usr/local/bin/iptables-nat
.. _Usage documentation: https://github.com/turnkeylinux-apps/lxc/tree/master/docs

