---
title: "Make a Kernel default?"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Ratscallion on 2009-10-16
Hello. I recently upgraded to the kernel version ending in 15, but, when I boot to this kernel, my wireless doesn't work.. However, booting to the previous version I have installed works fine.

My question to you is: Is there a way that I can either:

[LIST]
[*]Delete the new kernel altogether? I'm upgrading to Karmic when it comes out so it shouldn't be a problem for too long
[*]Set the previous kernel to the default one to boot? Surely, this would be simplest. It'd probably be something in GRUB, but I'd have no clue :S
[/LIST]
Thanks in advance.

---

### Post by MaxIBoy on 2009-10-16
Edit the file /boot/grub/menu.lst (with root access) and move the entry for the desired kernel up in the list.

Also, find the existing bug on launchpad (or create one if it's not reported,) and describe your problem so the developers know that there's a bug to be fixed. Do you know what your wireless hardware is?

---

### Post by Ratscallion on 2009-10-16
Erm..
```
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
Right.. Moving it up the list makes it default?

---

### Post by sisco311 on 2009-10-16
Just install [StartUpManager]("https://help.ubuntu.com/community/StartUpManager"), go to System > Administration > StartUp-Manager and select the default OS.

---

### Post by Ratscallion on 2009-10-16
> **sisco311 said:**
> Just install [StartUpManager]("https://help.ubuntu.com/community/StartUpManager"), go to System > Administration > StartUp-Manager and select the default OS.
Awesome, thanks.. I've done all that can be done.. Now I just have to see if it'll work.. Thanks.

---

### Post by MaxIBoy on 2009-10-16
Are these helpful:
[https://answers.launchpad.net/ubuntu/+question/81267](https://answers.launchpad.net/ubuntu/+question/81267)
[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

---

### Post by Ratscallion on 2009-10-17
Thanks sisco311 and MaxIBoy! It's working perfectly now! :D

---

