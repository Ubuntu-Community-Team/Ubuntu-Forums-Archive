---
title: "philips freevents x55 (twinhead h12y, etc)"
date: 2008-08-09
forum: Hardware
---

### Post by abyssdj on 2008-08-09
hi everyone,

i've not used any variant of linux for years, so i may as well be "new" to it as i can't remember ANYTHING.

anyway, i've decided to try ubuntu, of which the 32bit 8.04 live cd works fine on my desktop (using it now) but the 64bit version does not work on my laptop.

i think the bug is already well known, and it leaves the system completely frozen (ie. holding the power button for 4 seconds is the only way to fix it) when trying to load.

after a bit of messing around trying to get rid of the splash screen with the progress bar, it seems that the problem relates to sdhci:slot0, which after a search around is the built in card reader, i think?

has anyone come up with a fix, or at least a workaround for this? ideally, i'd like to try the live cd demo before installing fully on the laptop.

if there is any info that i can paste up that may help, tell me how to get it and i'll get it on here.

cheers

liam elliott

---

### Post by mikko.rantalainen on 2009-10-05
> **abyssdj said:**
> 
anyway, i've decided to try ubuntu, of which the 32bit 8.04 live cd works fine on my desktop (using it now) but the 64bit version does not work on my laptop. i think the bug is already well known, and it leaves the system completely frozen (ie. holding the power button for 4 seconds is the only way to fix it) when trying to load.


Philips Freevents and other Twinhead H12Y variants have a broken BIOS. See_ _[http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm) for details and workarounds. 32 bit live cd can be used with additonal kernel parameter (reserves the memory area not reserved by the bios when it should have been reserved):
reserve=0xFFB00000,0x100000

The 64 bit ubuntu kernel had a bug in the parsing of "reserve" parameter last time I checked and it cannot be used with this workaround. If this bug has been fixed, the 64 bit Ubuntu should work with the same workaround.

Hopefully the kernel can regognize this broken BIOS in the future and automatically apply the required "reserve"...

---

### Post by zanderred on 2010-03-07
Hi all freevents.

Fist you have to make the laptop boot-able for CD's. when booting press Delete (before the Philips screen), this will take you into the BIOS, make the CD the first boot-able device, save and quite.
(I'll take-it that you have an Ubuntu ISO 9.04 and upwards). When rebooting press Pause Break key next to the F12 key, this will halt the computer form booting, open CD drive put Ubuntu CD in and let the CD spin-up and then press Enter, the CD drive is slow at picking up. You should have booted the CD if not start again.
Once booted pick you language, F3 key map then F6 this will give you a list eg, acpi=off noapic etc press Esc, you will now  have a line of writing starting with Boot Options, the prompt is off to the right hand side, press the left arrow key will bring it back, scrawl left to the front of quite splash, it will look like this /initrd,gz |quiet splash --, you need to add the kernel parameter reserve=0xFFB00000,0x100000 and look like this /initrd,gz reserve=0xFFB00000,0x100000 quit splash, do not forget to space between 000 quite, after editing press Enter will boot Ubuntu.
If you install Ubuntu 9.04 you will have the same problem booting. You will need to edit grub Have a look at [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm) as above.
If you have installed Ubuntu 9.10 you need to edit grub 2, sudo gedit /etc/default/grub : change
GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="reserve=0xFFB00000,0x100000"
Save the file and run sudo update-grub
I hope this will help.

---

### Post by Eolith on 2011-01-07
Did this for my Philips freevents (don' know what type it is) and Ubuntu 10.10 - can confirm this all works just fine. Thanks.:D

---

### Post by nickrave on 2011-01-27
I've tried to install the 64bit, but it seems that the bug mentioned is still present in the kernel. It freezes at the entering username screen.

Have tried the 64bit Studio version, but can't install network manager, and other problems arise. 

I'd like to be able to run 64bit... in the mean time this 32bit works just great, thanks for the workaround, now I've got a really workable laptop, lovin Ubuntu you guys are genius.

---

### Post by Neophyt_e on 2011-01-27
I have Ubuntu 10.10 installed on a Philips X59 (h12y).

Installed, updated etc. Runs a treat, apart from one really niggling problem...

The battery indicator doesn't work correctly.

It constantly displays discharging, even tho it's on charge. It says there is only 14% battery life & I have to ignore the prompt to hibernate. The screensaver never kicks in because Ubuntu thinks the netbook is running on battery :confused: 

I've installed the acpi through apt-get & that dispalys the same info through a terminal window.

Running Windows Vista on the same machine & the battery indicator/charge/discharge work fine.

I installed the desktop, not netbook version of 10.10, would that be the problem?

Cheers

Neo

---

### Post by iz0nlee on 2011-11-26
I also have a freevents, the x56.  and am completely new to linux ubuntu.  I tried the above workaround with 2 different ubuntus, 11.10 first, this gave me a blank screen, just as it had before the modified code.
I then tried the 10.10 version, this has given me a screen with only the ubuntu logo and under it 5 dots which change alternately from red to white one by one. after a while even that stops and then there is no more action, no HD working, just the black screen with the ubuntu logo and 5 dots underneath
I did find another thread earlier that mentioned the card reader was a problem but I can't find it again.  I'll keep trying though and hopefully someone will provide an answer
 
best regards

---

