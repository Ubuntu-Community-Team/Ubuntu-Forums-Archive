---
title: "VM Network Problems"
date: 2008-11-07
forum: General Help
---

### Post by Titan8990 on 2008-11-07
I have tried both Qemu/KVM and VirtualBox and I am still unable to get networking to work properly. My current set up is from the Virtualbox wiki page: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox). I have also tried the one for Qemu/KVM. When I set br0 to use a static IP it does not transfer over to my VM. If I use DHCP with br0 the VM gets assigned a private class A address when it should be getting a private class C. When it is configured to DHCP it is able to ping some things on my network but nothing can ping it.

Here is what my /etc/network/interfaces currently looks like:

```
jordan@bourne:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto br0
iface br0 inet dhcp
        bridge_ports eth1 vbox0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


auto eth2
iface eth2 inet dhcp

```

The error I get in Virtual Box:

[ATTACH]91561[/ATTACH]

Vbox settings:

[ATTACH]91562[/ATTACH]

With Qemu:

```
#!/bin/bash

qemu -localtime -m 256 -cdrom xorg.iso -boot c -usb -net nic bt3.img

```

```
Warning: vlan 0 is not connected to host network
```


Thanks in advance for any assistance you can provide.

---

### Post by Titan8990 on 2008-11-08
bump

---

### Post by Titan8990 on 2008-11-10
bump

---

### Post by Titan8990 on 2008-11-11
^

---

