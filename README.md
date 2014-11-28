# Introduction
It's not uncommon to need to be connected to a bunch of overlapping
VPNs, network namespaces offer an easy way out of that problem.
Additionally user namespaces offer the ability to run a VPN entirely as
a user while still sharing the filesystem with the outside allowing all
your usual commands to work.

Also, it was a fun way to show how easy it is to work with namespaces
using the tools provided alongside LXC.

# How
The start-vpn script creates a new user namespace where your user is
root, then does a few trick so openvpn and byobu can happily run.
openvpn is then started and a byobu server started so you can easily
attach inside the container.

# Dependencies
 * socat
 * openvpn
 * byobu
 * uidmap
 * lxc
 * A 3.13 or higher kernel with usernamespaces enabled

# Using

    git clone git://github.com/stgraber/vpn-container
    cd vpn-container
    ./start-vpn \<VPN NAME\> \<VPN CONFIG\>

The vpn name is used for the socket/pid files and for the container's
hostname (so you can easily see what VPN you're working on).

The vpn config is a standard OpenVPN configuration file.

# Contributing
Contributions are always appreciated!

The project is licensed under the GNU GPL version 2 (and not any latter version).
Contributors must sign-off on their commits, indicating that they agree with
the Developer Certificate of Ownership (developercertificate.org).

Please try to follow the existing code style and for the shell scripts,
stick with POSIX shell.
