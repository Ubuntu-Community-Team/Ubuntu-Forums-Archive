---
title: "Swapped HD ATA to UEFI, incorrect password on Acer"
date: 2016-06-13
forum: Hardware
---

### Post by jon-zendatta on 2016-06-13
Hello World
laptop1:  Acer E1-501, has Ubuntu 15.04 installed on a UEFI WD10JPVX HD. Due to an unknown power failure I need this data retrieved on another laptop.
laptop 2: Acer 5740, has Ubuntu 15.04 installed on a ATA   Hitachi HTS545050B9A300  HD. 
I swapped the UEFI HD over, but now during boot it states incorrect password. I have never changed my UEFI password. Does this mean failed Drive? Or is the second laptop incompatible with UEFI.

Cheers:KS

---

### Post by oldfred on 2016-06-13
That sounds more like an UEFI error.

With Acer you have to set (at least temporarily) an UEFI password, and then set "trust" on the grub & shim .efi files.
Some threads, discuss downgrading UEFI, but others say very newest UEFI from Acer works. Make sure you have latest UEFI from Acer.

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
           
 Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

Your 15.04 is obsolete, so if any Ubuntu issues you probably will not be able to fix them.
Better to backup & install current version or see if upgrade in place works.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by weatherman2 on 2016-06-13
Can't you boot "live" from a USB stick with the new hard drive installed, then mount it and copy files off that way?

---

