---
title: "USB drive problem with Edgy"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by Spoon_boy on 2006-11-15
Hi everybody,
I have some problem with my USB drive. I use Edgy (upgrade from Dapper) on an ASUS laptop, and I use a Nexus 128MB usb drive. The problem is that it always shows that the drive has only 66MB left, 59MB is in use, while I know that it is empty. I even give "sudo rm -rf" to the drive to make sure it is emptied. And, when I tried to copy some files into it totaling more than 66MB, it gives me "not enough free space".  While, when I use my friend's laptop with Windows, it displays the free space correctly, and has no problem copying files into it.
This happens all the time, and I have no idea what is wrong here. 
Anybody knows what is wrong here? Shed some light please.

Thank you.

---

### Post by ceefour on 2006-11-30
Have you tried emptying Trash?

Try show hidden files and if there's .TrashXXX in your usb drive.

I have my own problem is that Kubuntu Edgy doesn't mount my USB drive upon first boot, I've to log out, then log in, and it mounts. Weird.

And my Sony Ericsson K600i is not recognized inside VMware. (it used to be recognized on Dapper). And USB drive support is also flaky inside VMware. (has never been got that correctly)

Maybe this works for me: (but not for you,h eheehe, offtopic)
[https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/35004](https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/35004)
[https://launchpad.net/distros/ubuntu/+ticket/2363](https://launchpad.net/distros/ubuntu/+ticket/2363)

---

### Post by teitunge on 2006-11-30
Yes. I have the same problem with usb-devices as ceefour. It´s my headset. If I plug it in after the boot-up, I will have to restart gnome for it to mount. Weird. Anyone know if there is a fix for this?

---

