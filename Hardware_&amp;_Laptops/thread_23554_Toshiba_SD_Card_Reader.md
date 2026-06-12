---
title: "Toshiba SD Card Reader"
date: 2005-04-02
forum: Hardware &amp; Laptops
---

### Post by DrMoxie on 2005-04-02
Not a deal breaking dilemma but I have a Toshiba Satellite 2400-S251 with an internal SD card reader.  It shows up as a SD TypA Controller in the device manager and as a PCI device in /sys/devices.  The trouble is that I cannot access any cards.  I'm a bit stumped.  

I'm a n00b, so thanks in advance!

---

### Post by briguy on 2005-04-07
Put a card in the slot, then type "dmesg" in terminal.  The last lines should tell you which device it is - on mine it was /dev/hde1.  Then type "sudo mkdir /media/smart", which will create a directory to mount it to.  Finally, put the following line in your /etc/fstab file:

/dev/hde1	/media/smart 	vfat	noauto,user,sync,exec 0 0

replacing the /dev/hde1 with the device you read from the dmesg output.  Now when you put a card in, it will automagically mount and open up a nautilus window with the contents!

This worked on my laptop using a PCMCIA card reader, it should be similar on your machine.

---

### Post by DrMoxie on 2005-04-08
Thanks for the rundown on this.  It doesn't seem to even initialize, nothing shows up in dmesg and even the little light on it doesn't blink.  I think that I'll pick up a 5 in 1 reader and use your instructions to get it working though.  Thanks again for the help, it made how the hardware works with the OS a little more transparent.  :-)

---

### Post by caspian on 2005-04-27
[QUOTE=DrMoxie]Thanks for the rundown on this.  It doesn't seem to even initialize, nothing shows up in dmesg and even the little light on it doesn't blink.  I think that I'll pick up a 5 in 1 reader and use your instructions to get it working though.  Thanks again for the help, it made how the hardware works with the OS a little more transparent.  :-)[/QUOTE]
 I'm sorry to revive a "dead" thread, but I've got the same problem here. I've got a Toshiba Tecra M2 -- I think I could get it working if I could just know the name of the partition (i.e., /dev/hde1, /dev/sda1, etc...)

I tried dmesg with the card in and with the card out... and I got the same output from dmesg both times. Is there something else I should try? Does the Toshiba SD card reader need special drivers?

Thanks.

---

### Post by DrMoxie on 2005-04-27
I'm thinking that it needs drivers written for it, I remember reading somewhere on LinuxQuestions.org that Toshiba had designed the hardware to necessitate special drivers but then again I could be talking out my posterior.  I know that when I built these class of laptops at work with XP it required a driver from the Toshiba site.

I'm still scratching at it and if I find something I'll be sure to post it here.  ;-)

---

### Post by jbrnd on 2005-05-02
[QUOTE=DrMoxie]I remember reading somewhere on LinuxQuestions.org that Toshiba had designed the hardware to necessitate special drivers
[/QUOTE]

Based on some cursory googling, it seems like Toshibas use a Winbond chip. If they really do, then you're in luck as a linux driver for Winbond card readers was recently developed. See

[http://members.inode.at/g.schild/DIV/Winbond-howto.html](http://members.inode.at/g.schild/DIV/Winbond-howto.html)
[http://projects.drzeus.cx/wbsd/](http://projects.drzeus.cx/wbsd/)

If you're not comfortable with kernel patching, your best best is probably to wait for the driver to be included in an Ubuntu kernel.

---

### Post by Gandalf on 2005-05-02
i have the same problem!!! i have an HP pavilion dv1071ea, the card reader is a texas  instruments chip!!

---

### Post by pkoufalas on 2005-11-14
[QUOTE=jbrnd]Based on some cursory googling, it seems like Toshibas use a Winbond chip. If they really do, then you're in luck as a linux driver for Winbond card readers was recently developed. See

[http://members.inode.at/g.schild/DIV/Winbond-howto.html](http://members.inode.at/g.schild/DIV/Winbond-howto.html)
[http://projects.drzeus.cx/wbsd/](http://projects.drzeus.cx/wbsd/)

If you're not comfortable with kernel patching, your best best is probably to wait for the driver to be included in an Ubuntu kernel.[/QUOTE]

My 2.6.10-5-686-smp kernel package supplied the wbsd, mmc_core and mmc_block kernel modules. 

I did modprobe wbsd without issue, but still no success with reading an SD card.

I have a Toshiba Satellite P20 (P25) with an SD card reader as listed by the OP.

---

### Post by jcooper on 2007-05-01
(post revival)

Has anyone managed to get an M2 SD reader working? :(

---

### Post by scadieux on 2007-09-04
I have a Toshiba Satellite with a built-in SD card reader. I gets detected, the card mounts as /media/disk and I can browse through it with Nautilus, but as soon as I want to copy something, Ubuntu complains I should not remove the card unless I unmount first,  but the card is still in its slot, I didn't touch anything. Anyone had the same problem and managed to work around that?

---

### Post by hotweiss on 2007-09-22
Bump.

---

### Post by DonaldPK on 2007-11-09
I have a Toshiba 2430 with built in SD card reader. Finally got it working.

edit /etc/modprobe.d/options and add one line

options wbsd irq=11 nopnp=1

then 

sudo rmmod wbsd
sudo modprobe wbsd

now the device works and can be accessed as /dev/mmcblk0

now to get it automounted everytime i insert a card..

EDIT:

on rebooting, the card does automount.

---

### Post by manishsingh4u on 2007-11-26
Thanks. These steps work like charm :)

---

### Post by freak_lick on 2008-01-27
> **DonaldPK said:**
> I have a Toshiba 2430 with built in SD card reader. Finally got it working.

edit /etc/modprobe.d/options and add one line

options wbsd irq=11 nopnp=1

then 

sudo rmmod wbsd
sudo modprobe wbsd

now the device works and can be accessed as /dev/mmcblk0

now to get it automounted everytime i insert a card..

EDIT:

on rebooting, the card does automount.

I have Toshiba Tecra A8 and i add line to /etc/modprobe.d/options
and when i type sudo rmmod wbsd i get:
ERROR: Module wbsd does not exist in /proc/modules
i have opened file /proc/modules but it's empty and open always as read-only no matter if i open it with sudo...
What should i do to make my SD card reader work??

---

### Post by nunomp on 2008-06-30
I own an old Toshiba Satellite S2450-401 and the SD Card reader doesn't work neither... I tried the /etc/modprobe.d/options hack but nothing happens. dmesg shows nothing. Suggestions  :) ?

Actually, I never used this reader.. ever. Only now that I bought an Eee Pc I thought it could be useful, buy as far as I know it can be really broken. And now I don't have windows installed to check.

---

