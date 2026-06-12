---
title: "HP 2400 scanner, 14.04 (64 bits)"
date: 2014-04-27
forum: Hardware
---

### Post by spacemen12 on 2014-04-27
Hi all,
    I have found an old thread that deal with that issue, but it does not solve my problem with 14.04.

    Here is the old thread [http://ubuntuforums.org/showthread.php?t=1089594&page=2](http://ubuntuforums.org/showthread.php?t=1089594&page=2)

    Basically, I can't scan. Everything is recognized, but when I press scan, the scan program crashes (all of them simple scan, Skanlite, and Xsane).

    Can you help me?

Best regards,

---

### Post by spacemen12 on 2014-05-03
Here is the dmesg when I plug it in

```
[  402.291783] usb 2-1.4: new full-speed USB device number 3 using ehci-pci
[  402.390908] usb 2-1.4: New USB device found, idVendor=03f0, idProduct=0a01
[  402.390916] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=12
[  402.390920] usb 2-1.4: Product: hp scanjet scanner
[  402.390924] usb 2-1.4: Manufacturer: Hewlett-Packard
[  402.390926] usb 2-1.4: SerialNumber: CN5BMSR0S0
[  402.412420] WARNING! power/level is deprecated; use power/control instead
```

When I run simple scan, it crashed when I press the scan button
```
me@myComputer:~$ simple-scan 
Segmentation fault (core dumped)
```

After simple scan crashed here is what is in dmesg
```
[  533.066841] scan-thread[5158]: segfault at 7f52c0f3d010 ip 00007f52c0cc58d4 sp 00007f52e560e7e0 error 4 in libsane-genesys.so.1.0.23[7f52c0ca7000+61000]
```

Any help would be appreciated.

---

### Post by tgalati4 on 2014-05-03
If this was a dual-boot system, then you could boot into an older version of Ubuntu and test the scanner.  Does the scanner work in Windows?

Try an older live DVD of Ubuntu and boot from that to see if the scanner works.

---

### Post by spacemen12 on 2014-05-04
Hi, the scanner works in windows 7 after downloading the hp software.

---

### Post by mynot1950 on 2014-05-12
My HP Scanjet 2400 works in Windows 7 and Ubuntu 12.04 and Linux Mint 14 but does NOT work in Ubuntu 14.04 nor Linux Mint 16.
It looks like I need to revert to an older Distro.

---

### Post by mynot1950 on 2014-05-12
Sorry - Double post

---

### Post by spacemen12 on 2014-05-15
Hi,
    What package did you use to make it work in 12.04? Maybe they could be easily adapted to 14.04?

Best regards,

---

### Post by mynot1950 on 2014-05-17
I am only a Newbie..... so the package was only what was loaded from the Live CD

---

### Post by mynot1950 on 2014-06-02
I got my HP scanjet 2400 to work in Ubuntu 14.04 (64 bit)
I downloaded the drivers at this address
[http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php)
I extracted the file and you get 2 more files.... open up the document to follow directions, although the exact wording was altered slightly to account for different place where my files were stored.
Also I had to enter the word "sudo" before all terminal entries to act as superuser.
Anyway, it worked.
Hope this helps

---

### Post by ckrles on 2014-06-26
same problem here. I installed Linux Mint 17 Qiana (Ubuntu 14.04 Lts 64 bits). I can print, but I can't scan. I installed the drivers according to manufacturer's website. Simple scan ans Xsane detect the scanner name but they don't work. Xsane says "invalid argument" and Simple scan suggests me to choose another scanner, but the only it offers me is not detected.

My scanner is Brother DCP-7055.

any ideas?

I could run it on another Ubuntu 12.04 lts 32 bits pc, but I can't in Ubuntu 14.04 Lts

I openend a thread [http://ubuntuforums.org/showthread.php?t=2231550&p=13058999#post13058999](http://ubuntuforums.org/showthread.php?t=2231550&p=13058999#post13058999)

---

