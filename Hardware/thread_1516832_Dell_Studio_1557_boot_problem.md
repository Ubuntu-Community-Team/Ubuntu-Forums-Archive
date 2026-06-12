---
title: "Dell Studio 1557 boot problem"
date: 2010-06-24
forum: Hardware
---

### Post by Rapture1781 on 2010-06-24
Hi,
I'm an italian boy and my english is not good.

I bought a Dell Studio 1557 and I have a problem with boot.

Sometimes when I switch it on, it stops here:

[IMG]http://img18.imageshack.us/img18/1505/img0665b.jpg[/IMG]


Why??
What have I to do?

Thank you....

---

### Post by dino99 on 2010-06-24
dont worry you are not alone with this issue :p

i guess that is with Lucid and kernel 32, right ?

boot either into recovery mode or edit the boot line (e) and remove (quiet splash), then boot

then open synaptic repo and add these ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

update, upgrade, reboot

then check that the driver is activated: system admin hardware driver

---

