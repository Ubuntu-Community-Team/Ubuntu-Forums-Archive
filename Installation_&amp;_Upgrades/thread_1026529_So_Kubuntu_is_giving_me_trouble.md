---
title: "So Kubuntu is giving me trouble"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Evil Ninja on 2008-12-31
So I've tried everything I can think of to fix this. Maybe it was when the disc was writing. Maybe the disc itself is messed. Maybe because I just picked restart. Maybe...no. No, no and no. So now I come here for the infinite knowledge of Linux which you all so lovingly possess.

So I pop the LiveCD into my laptop (Kubuntu 8.10, 64-bit) and it loads until I get to a screen that looks like so...

```
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) [     69.243555] end_request: I/O error, dev sr0, sector 1424640
[     69.243623] Buffer I/O error on device sr0, logical block 178080
```

I have yet to see a desktop. I'm running Ubuntu 8.10, 64-bit.

---

### Post by taurus on 2008-12-31
Did you check the disc (scan cd for defects at the initial screen) before you tried to boot from it?  How fast did you burn it?

---

### Post by Evil Ninja on 2008-12-31
> **taurus said:**
> Did you check the disc (scan cd for defects at the initial screen) before you tried to boot from it?  How fast did you burn it?

I did  and it come up to the same screen. I burnt it at x16.

---

### Post by taurus on 2008-12-31
1.  Do a checksum of the ISO image that you have just downloaded.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Burn it at a slow speed like 4x.

3.  Run a scan cd for defects at the initial screen to make sure the cd is all good.

---

### Post by AlanR8 on 2008-12-31
You could also try using the 32 bit version.......

---

### Post by Evil Ninja on 2008-12-31
> **taurus said:**
> 1.  Do a checksum of the ISO image that you have just downloaded.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Burn it at a slow speed like 4x.

3.  Run a scan cd for defects at the initial screen to make sure the cd is all good.

Will do, will be back.

> **AlanR8 said:**
> You could also try using the 32 bit version.......

The laptop has 4GB of RAM.

---

### Post by albinootje on 2008-12-31
> **Evil Ninja said:**
> 
(initramfs) [     69.243555] end_request: I/O error, dev sr0, sector 1424640
[     69.243623] Buffer I/O error on device sr0, logical block 178080[/CODE]


Those errors are from your cdrom- or dvd-drive.
Can you make a bootable Ubuntu installation usb-stick instead ?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Evil Ninja on 2008-12-31
> **albinootje said:**
> Those errors are from your cdrom- or dvd-drive.
Can you make a bootable Ubuntu installation usb-stick instead ?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'd need a USB stick that could fit the distro, but sure I'll try that today.

---

### Post by Evil Ninja on 2008-12-31
That worked! Thanks.

---

