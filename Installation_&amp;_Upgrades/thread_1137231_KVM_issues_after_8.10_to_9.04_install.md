---
title: "KVM issues after 8.10 to 9.04 install"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by vetch101 on 2009-04-25
Hi everyone,

(Dernit - the system seems to have accidentally prefixed my thread with an emoticon - sorry about that...)

Since installing 9.04, I've had [some problems]("http://ubuntuforums.org/showthread.php?p=7144973#post7144973") with kernel 2.6.28.11 corrupting my LVMs, so I've dropped back to 2.6.27.11... It is now throwing these messages that I never had before...

[   67.059665] kvm: 5966: cpu0 unhandled wrmsr: 0xc0010117 data 0
[   67.069594] kvm: 5966: cpu0 unhandled rdmsr: 0xc0010117
[   67.070051] kvm: 5966: cpu0 unhandled rdmsr: 0xc0010117
[   67.244228] kvm: 5994: cpu0 unhandled wrmsr: 0xc0010117 data 0
[   67.254873] kvm: 5994: cpu0 unhandled rdmsr: 0xc0010117
[   67.255008] kvm: 5994: cpu0 unhandled rdmsr: 0xc0010117
[   67.375782] kvm: 6015: cpu0 unhandled wrmsr: 0xc0010117 data 0
[   67.401318] kvm: 6015: cpu0 unhandled rdmsr: 0xc0010117
[   67.401767] kvm: 6015: cpu0 unhandled rdmsr: 0xc0010117

Does anyone have any ideas?

Also - does anyone know how to configure the virtlib templates to passthrough USB to the client OSes...
I believe it wasn't possible with the Intrepid kernel, but allegedly it should be achievable with the Jaunty install...

Cheers,

Jx

---

### Post by vetch101 on 2009-04-25
Oh - apparently it's "benign"...

[https://lists.ubuntu.com/archives/kernel-bugs/2009-April/050104.html](https://lists.ubuntu.com/archives/kernel-bugs/2009-April/050104.html)

Cheers,

Jx

---

### Post by freakalad on 2009-06-30
I can confirm this same issue.
I don't think it's all that harmless

Upgraded from Hardy-64 to Jaunty-64; kept my old data, but installed fresh OS over it, keeping my home 7 other partitions as-is without formatting

Since then, if I import the XML-dumps of my old system images (virsh create ...), the guests load & start up OK, but are removed once the clients shut down.

If I create a new libvirt entry, retaining the NIC's MAC address (as found in the XML-dump), and pointing the HDD to the pre-existing image, the client systems fail: windoze throws a BSoD & Ubuntu clients simply keep rebooting.

I've had the following errors in dmesg:
```

[ 4723.508751] kvm: 14021: cpu0 unhandled wrmsr: 0xc0010117 data 0
[ 4724.518623] kvm: 14021: cpu0 unhandled rdmsr: 0xc0010117
[ 4724.518653] kvm: 14021: cpu0 unhandled rdmsr: 0xc0010117

```
and
```

[ 1649.821417] kvm: 9763: cpu0 unhandled wrmsr: 0xc0010117 data 0
[ 1649.831818] kvm: 9763: cpu0 unhandled rdmsr: 0xc0010117
[ 1649.831845] kvm: 9763: cpu0 unhandled rdmsr: 0xc0010117

```

some logging info from /var/log/libvirt/qemu/w2k3.log
```

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin /usr/bin/kvm -S -M pc -m 512 -smp 1 
-name w2k3 -uuid 562fef3d-6e18-ffb1-3e79-4c0c9b11eb2f -monitor pty -pidfile /var/run/libvirt/qemu//w2k3.pid -no
-acpi -boot c -drive file=/media/vm/w2k3.img,if=ide,index=0,boot=on -net nic,macaddr=00:16:3e:67:da:63,vlan=0 -
net tap,fd=20,script=,vlan=0,ifname=vnet0 -serial none -parallel none -usb -vnc 127.0.0.1:1 
char device redirected to /dev/pts/1
info cpus
* CPU #0: pc=0x00000000000ffff0 thread_id=14023
cont
system_powerdown

```

and

some logging info from /var/log/libvirt/qemu/jaunty64.log
```

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin /usr/bin/kvm -S -M pc -m 512 -smp 1 
-name jaunty64 -uuid b10cfa26-a76f-33c2-6154-ae1e371a39ac -monitor pty -pidfile /var/run/libvirt/qemu//jaunty64
.pid -boot c -drive file=/media/vm/jaunty64.img,if=ide,index=0,boot=on -net nic,macaddr=00:16:3e:3e:69:df,vlan=
0 -net tap,fd=19,script=,vlan=0,ifname=vnet1 -serial none -parallel none -usb -vnc 0.0.0.0:2 
char device redirected to /dev/pts/2
info cpus
* CPU #0: pc=0x00000000000ffff0 thread_id=13602
cont
system_powerdown

```

Think this is a KVM thing, since the reboot cycle thing happens when running KVM from CLI:
```
sudo kvm -hda ./jaunty64.img
```

---

### Post by freakalad on 2009-06-30
Client system seems to be OK when installed from scratch.
Quickly installed a Linux Mint client, & it seems fine

---

