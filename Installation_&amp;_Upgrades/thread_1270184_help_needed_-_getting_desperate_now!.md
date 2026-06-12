---
title: "help needed - getting desperate now!"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by manc-munsters on 2009-09-19
hi all
I had ubuntu 9.04 installed on my acer laptop. no duel boot, no windows, just ubuntu. after many months of struggling to get my wireless router, printer and external hard drive to work, I have finally given up.
I now want to put windows vista back on the laptop, and ubuntu as a duel boot option.
 
Now the problems.
windows disks do not boot. xp, win89 and vista all tried and all failed.
I read that ubuntu must be taken off first, so booted from a 9.04 disk and formatted my hard drive.
now no disks will boot. xp, win98, vista, ununtu 9.04 and ubuntu 8.10 all tried and failed.
all I get is the GRUB error 17 message.
 
Can anyone tell me how to get the laptop to boot from my vista disk so I can install it from disk? I am OK from then on as the ubuntu 9.04 disk will give me the option of installing into a partition and sorting a duel boot out.
 
replies in "idiot language" please as I am useless with computers ;-)
 
again, I am getting a GRUB error 17message at boot up and need to install vista
 
hope someone can help me finally get the machine running!

---

### Post by Bartender on 2009-09-19
First off -

Don't Panic

Calm down.  It sure looks to me like your PC is not set to look at the optical drive first.  Restart it and go into BIOS.  Look for Boot Priority or Boot Devices.  If you've never been into BIOS before it will seem awkward.  I still get bamboozled with one of mine til I remember it's weird combination of keystrokes.  Using some combination of your up/down arrow keys, enter key, and a couple of others, move the optical drive to the #1 slot in the boot priority list.  Then save the changes as you get out of BIOS.  It's easy to get out of BIOS and fail to save the changes!

With the first vista recovery disc in the optical drive tray, restart the PC.

---

### Post by manc-munsters on 2009-09-19
cheers bartender (and boy do I need a drink!)
 
bios is set to boot from cd drive 1st, then hdd
 
the vista is on a cd, not a recovery disk. does that help?

---

### Post by dandnsmith on 2009-09-19
With that set of circumstances, I'd now be suspecting the optical drive was dying, and is now, effectively, not working.

Have you the resources to try an external HDD/Optical drive/USB stick?

Additionally, it might be possible to restore some functionality by using a head cleaner - but it might be a little tricky without a working OS.

---

### Post by J1m on 2009-09-19
Despite the boot order in the BIOS - some laptops require you to press ESC or F12 or some other key to access the BOOT MENU.  Otherwise they will boot from the first hard disk anyway.

If I were you - i'd boot and repeatedly press ESC and F12 to see what happens!

---

### Post by AmerNewbieInDE on 2009-09-19
hmm, actually, a vista disk not booting maybe because it is a upgrade disk and not install disk... there is a big price difference. problem with upgrader disk is you must have a windows installation on the hd, and start the iinstall from within windows...

---

### Post by manc-munsters on 2009-09-19
bios is set as 1st boot cdrom, 2nd hdd, 3rd usb. 
 
the cd drive was running oem and copied disks (photos etc) without problems before I formatted the hard drive
 
I can easily change it to boot with usb before hdd and I have access to a 2gb usb memory stick if that is of any use?
 
hope this clarifies the situation a little

---

