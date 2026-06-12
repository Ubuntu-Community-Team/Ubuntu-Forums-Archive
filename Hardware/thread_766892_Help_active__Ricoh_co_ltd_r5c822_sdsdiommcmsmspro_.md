---
title: "Help active  Ricoh co ltd r5c822 sd/sdio/mmc/ms/mspro host adapter"
date: 2008-04-25
forum: Hardware
---

### Post by rodrigo.galvez on 2008-04-25
Sorry but my English is not as good as i wish but i hope you understand me to help me 

I have a laptop hp dv6648se with ubuntu 8.04 and i cant active my internal Media Reader, i have a XD card .

Information: 
Command lspci:
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

I try to active the modules doing this:
$ sudo modprobe tifm_7xx1
$ sudo modprobe tifm_core
$ sudo modprobe tifm_sd

and edit de module file:
sudo gedit /etc/modules
and add some lines, so the file saved was this:
/etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
tifm_7xx1

tifm_core

tifm_sd

i restart but it dosent works to.
so i find that i have to do this:

lsb_release -a:

LSB Version: core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:core-3.2-ia32:core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-3.2-noarch
Distributor ID: Ubuntu
Description: Ubuntu 8.04
Release: 8.04
Codename: hardy

"then this"
sudo dpkg -S /etc/lsb-release   
"but i dont understand what for is it"

then i check the System log, and found this:

Apr 24 07:16:48 oblivion-laptop kernel: [ 39.565764] sdhci: Secure Digital Host Controller Interface driver
Apr 24 07:16:48 oblivion-laptop kernel: [ 39.565767] sdhci: Copyright(c) Pierre Ossman
Apr 24 07:16:48 oblivion-laptop kernel: [ 40.755400] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 12)
Apr 24 07:16:48 oblivion-laptop kernel: [ 40.755439] ricoh-mmc: Controller is now disabled.
Apr 24 07:16:48 oblivion-laptop kernel: [ 40.755557] sdhci: SDHCI controller found at 0000:07:09.1 [1180:0822] (rev 22)
Apr 24 07:16:48 oblivion-laptop kernel: [ 40.755599] ACPI: PCI Interrupt 0000:07:09.1[B] -> GSI 21 (level, low) -> IRQ 18
Apr 24 07:16:48 oblivion-laptop kernel: [ 40.755614] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.

i dont know what to do to solve my problem help please

---

### Post by rodrigo.galvez on 2008-04-28
I found This but I dont understand at all...

[http://lkml.org/lkml/2007/10/1/375](http://lkml.org/lkml/2007/10/1/375)

i am not sure if this is to make available my hadware... ??

Could someone help me???

---

### Post by rodrigo.galvez on 2008-04-28
I found this other nad i think here is the answer but i dont understand at all
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/111089](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/111089)

do i have to put onthe console:
setpci -s '03:01.0' 0xCA=0x57 #enables you to write to the device
setpci -s '03:01.0' 0xCB=0x02 #set register to disable MMC
setpci -s '03:01.0' 0xCA=0x00 #disables write to device

but instead of 03:01.0 i have to put  07:09.2

because of this:
Apr 24 07:16:48 oblivion-laptop kernel: [ 40.755400] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 12)

is this correct???

---

### Post by deviouscontrol on 2008-04-28
I don't have the exact same hardware as you, but I figured any help is better than no help. 

I have a different Ricoh Card Reader, only SD but I got mine working by installing this

[http://sourceforge.net/projects/sdricohcs/](http://sourceforge.net/projects/sdricohcs/)

and doing a make, make install

---

### Post by syko21 on 2008-04-28
xD is a proprietary format and as such it needs to be hacked in order to work properly. Unfortunately no one has done this (I have the same device, dv6000t) and so the xD part of the card reader will remain non-functional. SD should work fine out of the box though.

---

### Post by andreselsuave on 2008-04-29
I have the same problem with my Ricoh card reader. I've tested some solutions and anyone of them hasn't worked ... :(
I'm very dissappointed... anyone knows how to fix this? 

Thanks!

---

### Post by PhilCash on 2008-06-18
I just got my card reader going after a lot of research, by fluke...
Try inserting a card with data on it into the reader and leaving it there while you reboot. This seemed to prompt Ubuntu to load the required driver on my system, maybe it will work for you too.

Good luck,
Phil

---

### Post by sergiom99 on 2008-06-18
by data you mean "any data"? (Pics?)
thanks.

---

### Post by Llewxam on 2008-06-21
well i am having more or less the same issues. mine is mostly with the ms pro duo cards. can't for the life of me get it to work and i tried various things. it does work in vista (bleh) on a friend's laptop (hp pav 6748us) which is the same model as mine.

---

### Post by syko21 on 2008-06-21
I was attempting to install a new kernel, 2.6.25, and in the middle of the configuration i saw an experimental module for sony memory sticks. I don't have any to test it with so I could not confirm whether or not the module worked. Anyone here ever try compiling their own kernel before?

---

### Post by Llewxam on 2008-06-21
> **syko21 said:**
> I was attempting to install a new kernel, 2.6.25, and in the middle of the configuration i saw an experimental module for sony memory sticks. I don't have any to test it with so I could not confirm whether or not the module worked. Anyone here ever try compiling their own kernel before?

what's the module name? and is there a possibility to find said module on its own? 'cause if that is so it could probably work/help resolve this issue.

---

### Post by syko21 on 2008-06-21
After you do make menuconfig go to device drivers. Scroll down and its called "Sony MemoryStick card support (EXPERIMENTAL)".
Heres what the kernel says about the module
```

CONFIG_MEMSTICK:                                                                                                   
                                                                                                                    
Sony MemoryStick is a proprietary storage/extension card protocol.                                                 
                                                                                                                    
If you want MemoryStick support, you should say Y here and also                                                    
to the specific driver for your MemoryStick interface.                                                             
                                                                                                                    
Symbol: MEMSTICK [=y]                                                                                              
Prompt: Sony MemoryStick card support (EXPERIMENTAL)                                                               
  Defined at drivers/memstick/Kconfig:5                                                              
  Location:    -> Device Drivers

```

---

### Post by sergiom99 on 2008-06-21
I tried booting with an MS card but it didnt worked out.

---

### Post by SandersOnSite on 2008-09-06
> **deviouscontrol said:**
> I don't have the exact same hardware as you, but I figured any help is better than no help. 

I have a different Ricoh Card Reader, only SD but I got mine working by installing this

[http://sourceforge.net/projects/sdricohcs/](http://sourceforge.net/projects/sdricohcs/)

and doing a make, make install

[http://ubuntuforums.org/attachment.php?attachmentid=66496&d=1208680680](http://ubuntuforums.org/attachment.php?attachmentid=66496&d=1208680680)

Stolen from another post (sorry no time to get proper credit - but thanks to OP) -

already made deb package for easy install.

---

