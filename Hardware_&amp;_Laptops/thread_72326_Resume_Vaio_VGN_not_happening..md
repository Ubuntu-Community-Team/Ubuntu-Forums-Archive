---
title: "Resume Vaio VGN not happening."
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by pnunn on 2005-10-05
Hi folks,

really need some help here because this is driving me nuts...

Ubuntu (Kbuntu in my case) is working fantastically on this notebook **except for** hibernation and the sound server.

Now.. I've searched for both on here and else where and can't seem to get any luck..

I have the machine going into hidernation OK.. but when it wakes up I just get little green squares on the screen and that's it.. have to go to terminal 1 and login as root and shut down each time.. (going back to 7 doesn't work).

The setup...

Grub command line...

title           Ubuntu, kernel 2.6.10-5-686 
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro acpi_sleep=s3_bios 
resume=/dev/hda5 vga=0x318 splash
initrd          /boot/initrd.img-2.6.10-5-686
savedefault
boot

/etc/default/acpi-support

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
#ACPI_SLEEP_MODE=mem
ACPI_SLEEP_MODE=standby

# Add modules to this list to have them removed before suspend and reloaded
# on resume. It should look something like MODULES="e1000 ipw2100"
MODULES="ipw2200"

Any clues?  Should I upgrade to Breezy? If so, how?

Thanks guys... Ohh.. btw.. the sound server has stopped for some reason (no idea why) and it won't start again.

Thanks.

Peter.

---

### Post by diomedes on 2006-01-13
Hi pnunn,  I have had luck using [855resolution](http://perso.wanadoo.fr/apoirier/) to re-init the display after a hibernate... 

855resolution 52 1280 768 > /dev/null
855resolution 43 1280 768 > /dev/null

---

