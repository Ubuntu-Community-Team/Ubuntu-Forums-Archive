---
title: "HP mini card reader not recognized"
date: 2010-12-01
forum: Hardware
---

### Post by stwert on 2010-12-01
I recently bought an HP mini 110-3018CA and am trying to get the internal card reader to be recognized (or get cards to be recognized). I tried booting with a card in, but that didn't seem to work. Nothing listed in /media/. lspci showed some USB controllers, but I don't know if they're the card reader or what.

I've searched the forums briefly, but couldn't find much. If there's already another thread on this, could you point me?

Thanks for the help!

---

### Post by stwert on 2010-12-07
Any help on this would be fantastic, as basically the only reason I bought a netbook was to use as a SD backup system while on vacation. I'm leaving soon, so this is somewhat urgent. Otherwise I'll have to reload the very crappy Win 7 starter.

If I need to buy an external SD reader, I could do that, but I want to know if this is a known problem, or even fixable. Should I provide other info?
Thanks!

---

### Post by floydwilde on 2010-12-18
I have a similar model, HP Mini 110-3100 according to dmidecode.  Everything seems to work fine, accept the SD card reader.  I didn't see anything happen when I plugged in a card, and I don't see anything with fdisk.  

I plugged in a 4GB USB key, and that popped up the file manager and I see it come up as sdb.   

So anyway, I'm not fussed, it's handy to copy images from a digital camera over, will keep looking and tinkering for a solution.

---

### Post by cfeagans on 2010-12-20
I'm basically experiencing the same thing on an HP Mini 110. Apparently the SD Card reader works on proprietary drivers that no on has yet reverse engineered. 

As a fairly effective work around, I'm using a 5-in-1 card reader that looks like a USB flash drive. It'll accept both the full-size SD cards and the micro-SD size.

I use mainly the micro-SD, and this fits very nicely in the end of the Card Reader. 

But I still Google every week or so to see if there are any drivers for the SD Card reader. This probably the only difficulty I've encountered with running Ubuntu on it. Everything else works like it was a netbook designed with Linux in mind.

---

### Post by kostkon on 2010-12-20
The card reader of HP Mini 210 works just fine though. I just tested it using a memory stick, after reading your posts here.

---

### Post by MagliteL13 on 2010-12-22
I experience the same thing.  I've tried all different types of cards (SD, MMC, MS) formated to several different file systems, and of varying size and class and nothing seems to work.  Any help would be much appreciated.

---

### Post by MagliteL13 on 2010-12-23
Soooo, it took a little searching, but after finding out what type of card reader (Realtek rts5159), I was able to download the driver and install with no problems. 
My card reader now works as it should with no problems.  I have an HP Mini 110.

Download the driver:
[http://tinyurl.com/2bj95k]("http://tinyurl.com/2bj95k")

Extract the file.
Go to the folder.

'make'
'sudo make install'
'sudo depmod'

reboot computer.

Hopefully this will work for someone else as well. :)

---

### Post by Macausarzs on 2011-01-16
> **MagliteL13 said:**
> Soooo, it took a little searching, but after finding out what type of card reader (Realtek rts5159), I was able to download the driver and install with no problems. 
My card reader now works as it should with no problems.  I have an HP Mini 110.

Download the driver:
[http://tinyurl.com/2bj95k](http://tinyurl.com/2bj95k)

Extract the file.
Go to the folder.

'make'
'sudo make install'
'sudo depmod'

reboot computer.

Hopefully this will work for someone else as well. :)

The method is workable for me. Thank you so much.

---

### Post by TerrorBite on 2011-02-23
I was able to get my system working using this method as well, though I got the card reader working without a reboot using an additional command.

1. Downloaded the driver from the link given in the post above (the final download URL was [ftp://WebUser:7p5XTFw@202.134.71.21/pc/crc/rts_pstor.tar.bz2](ftp://WebUser:7p5XTFw@202.134.71.21/pc/crc/rts_pstor.tar.bz2))
2. Extracted the driver and cd'd to the directory
3. Ran 'make' and 'sudo make install'
4. Ran 'sudo depmod' to recalculate driver dependencies, then 'sudo modprobe rts_pstor' to load and initialise the driver.

Linux immediately recognised the card reader and mounted the card that was inserted into it. No reboot required.

Thanks MagliteL13!

---

### Post by cmani on 2011-03-29
Hi,

When i do "make" from the extracted folder of rts_pstor.tar.bz2 i am getting the following error on ubuntu 10.10 netbook remix version

sed "s/RTSX_MK_TIME/`date +%y.%m.%d.%H.%M`/" timestamp.in > timestamp.h
cp -f ./define.release ./define.h
make -C /lib/modules/2.6.35-28-generic/build/ SUBDIRS= modules
/usr/src/linux-headers-2.6.35-28-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-28-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
/usr/src/linux-headers-2.6.35-28-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: not found
make[3]: *** [scripts/basic/fixdep] Error 127
make[2]: *** [scripts_basic] Error 2
make[1]: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2

Pl. help me to get fixed.

---

### Post by livekeen on 2011-03-31
> **cmani said:**
> Hi,

When i do "make" from the extracted folder of rts_pstor.tar.bz2 i am getting the following error on ubuntu 10.10 netbook remix version

sed "s/RTSX_MK_TIME/`date +%y.%m.%d.%H.%M`/" timestamp.in > timestamp.h
cp -f ./define.release ./define.h
make -C /lib/modules/2.6.35-28-generic/build/ SUBDIRS= modules
/usr/src/linux-headers-2.6.35-28-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-28-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
/usr/src/linux-headers-2.6.35-28-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: not found
make[3]: *** [scripts/basic/fixdep] Error 127
make[2]: *** [scripts_basic] Error 2
make[1]: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2

Pl. help me to get fixed.

I have the exact same problem, if anyone understands what this means, I'd love to know as well!! Thanks in advance!

---

### Post by Greblok on 2011-04-24
> **TerrorBite said:**
> I was able to get my system working using this method as well, though I got the card reader working without a reboot using an additional command.

Thank you!!! 
Worked like a charm on my HP Mini 110 3110 with Ubuntu Netbook Remix 10.10,
no reboot required. :)

---

### Post by greg.harvey on 2011-05-02
I am *not* finding the card reader in the 210 is fine. In fact, I have a HP Mini 210 2001sa, brand new, and the card reader is undetected. It's not even showing up in lshw. I'll try the Realtek driver tomorrow, but I don't even know if the installed device is the Realtek still. I hope so!

---

### Post by silverglade00 on 2011-05-02
```
sudo apt-get install build-essential
``` should get rid of the make errors

---

