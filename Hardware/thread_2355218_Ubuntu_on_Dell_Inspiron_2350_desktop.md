---
title: "Ubuntu on Dell Inspiron 2350 desktop"
date: 2017-03-10
forum: Hardware
---

### Post by ulissipus on 2017-03-10
Anyone has Ubuntu on Dell Inspiron 2350 Desktop? Does the machine behave correctly? Mine - DELL Inspiron 2350 Desktop 23" - 4th generation Intel Core - i7 4710MQ processor (6M cache up to 3.50GHZ - 12GB dual channel DDR3L 1600MHz (8GBx1 + 4GBx1) - runs on Windows 10. I want to make it run on Ubuntu 16.04LTS but would like to make sure it would be all right. 
I moved to Ubuntu in my Toshiba laptop, it works beautifully were it not for the fact that it does heat up a bit.

---

### Post by ajgreeny on 2017-03-10
Try it live on your Dell machine first to see if everything works as it should.

Does it use UEFI or legacy BIOS? Both should work but if you wish to dual boot you must install Ubuntu in the same mode as Win 10.
As it's a desktop machine I presume it has no wifi which can sometimes be a problem, but cable connected ethernet should work out of the box, and with the specs that you have mentioned so far I think all should be good.

What graphics does it have? If it uses an integrated Intel system there should be no problem with that.

---

### Post by oldfred on 2017-03-10
I have a similar generation SFF Dell:
```

System:    Host: fred-Inspiron-3647 Kernel: 4.4.0-14-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: Inspiron 3647
           Mobo: Dell model: 02YRK5 v: A02 Bios: Dell v: A08 date: 06/29/2015
CPU:       Dual core Intel Core i3-4160 (-HT-MCP-) cache: 3072 KB
 
```

It came with Windows 8, upgraded to Windows 10 when I found I needed Windows to watch DVD recorded shows with Xfinity.

But I originally installed 15.10, then 16.04 without any issues. 
All installs are UEFI.
Do not remember what UEFI settings I changed, but every system, old BIOS or new UEFI seemed to need some settings changed to work or work well.

---

### Post by ulissipus on 2017-03-11
Will follow your suggestion and try it live first. My ultimate aim is getting rid of Microsoft, but I do depend very much on this machine.

It has wifi, by the way, but I have it connected with an ethernet cable.

As to graphics, it is Intel? 4th Generation Intel (R) Core (TM)...

Thank you very much for your reply.

---

### Post by ulissipus on 2017-03-11
Thanks, OldFred. I am quite at loss as to UEFI install though. All my previous installs were from a flash drive with an ISO.

Will go through the thread on UEFI boot install.

Thanks again.

---

### Post by oldfred on 2017-03-11
With new UEFI, you should get two boot options for flash drive from UEFI boot menu.
One usually is UEFI:flash and the the other 'flash'  which is the BIOS boot option. 'Flash' will be label, brand or model of flash drive.

If you want to make sure you can only boot in UEFI mode, standard installers also add BIOS boot, doing it yourself, you just skip that step. Or they use dd and create a hybrid bootable DVD/flash drive.

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

