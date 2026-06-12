---
title: "Bootmgr is missing??"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Arkitekt on 2009-10-31
I have run into this manager before when dealing with hard drives.. but never with USB keys.

I downloaded UNetBootin and created a bootable USB key with it for 9.10 64bit. It downloaded the distro, copied the files over, and then installed the bootloader. However, when I try to boot to it I get the 'Bootmgr is missing' message. 

The machine I am trying to install this on has 2 drives, the Slave is a media drive, the master hdd has 3 paritions on it (1 for windows 7, one that I want to install ubuntu on, and then a media partition to share between the two operating systems).

I installed Windows 7 64 bit earlier today and now want to install ubuntu into a dual boot environment. I am doing ubuntu second so that GRUB does not get over written.

I have tried to load it up through windows but it just gives me the option to reboot (which it doesn't seem to do), to install it along side windows as a executable program (don't want to do this), or to install a cd boot helper (tried this, failed while extracting. "an error occurred: could not retrieve required installation files" )

I should also add that I have already tried to add bootmgr to the usb key via bootsect.exe on the windows 7 dvd. I ran bootsect.exe /nt60 and it said it was successful, however upon rebooting I received the same message as before.

my usb key is formatted as NTFS, would this cause a problem? does it need to bet FAT32?


Any help would be greatly appreciated.

---

### Post by Arkitekt on 2009-10-31
.

---

### Post by Arkitekt on 2009-10-31
just wanted to update.

I re-formated the usb stick as FAT32 and re-did Unetbootin on the stick for 9.10 64bit. 

This time I got into the Unetbootin bootloader and selected default.

This is what I got

```

Loading /ubnkern...............................................
Loading /ubninit...............................................
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


```

This is on my HP dv9231ca Intel Centrino Core 2 Duo T5600 1.8Ghz

---

### Post by Arkitekt on 2009-10-31
So I decided to try using the 32 bit 9.10 instead to see if I got any further.

This time I get a little bit further, it loads up ubnkern and ubninit, says ready, goes to a screen with a white ubuntu logo, screen then goes back, then it turns into a flashing pinkish purpleish screen  with some random blocks of other colors. Keeps doing this until I restart.

Never had this much trouble trying to install a distro.. what exactly is going on here?

perhaps it is UNetbootin? I am running it under Windows 7 (in Vista SP2 Compatibility mode and running as administrator). I will try in Jaunty with usb-creator.

---

### Post by Arkitekt on 2009-10-31
re-did the usb stick under jaunty with usb-creator. successfully made a 9.10 32bit usb key, this time I was able to select language when I booted up, and then had the options to run with change to my system or install. I first chose Install and once again got a screen with a bunch of flashing colors which then switched to a flashing pink/purple screen again. 

Rebooted, decided to see if I could just get into a live version of karmic and this time I got this:

```

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-commands

(initramfs) mount: mounting aufs on /root failed: Invalid argument
aufs mount failed 

```

Is anyone else having this much trouble installing Karmic?

---

