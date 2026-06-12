---
title: "Dual-boot, lose DVD drive after installing edgy"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by ElginRoko on 2007-03-08
Howdy

I'll start by appologising to anyone who can be bothered to read this for it being rather long.  I wanted to be thorough see (I do work in a firmware test team after all).

I'm currently trying to set up my laptop (evesham branded Clevo M575U) to dual boot ubuntu as my general OS, with an extremely thinned out windows xp install for when I want to play Neverwinter Nights 2 again (and maybe to listen to some evil DRMed football commentry if i can't get it working under wine, but that's another issue).

The state I'm starting from is with my one 100Gb drive having a 50Gb partition on it (god I love being able to do a clean install yet keep your home directory).  The rest is unpartitioned, and will go as 2Gb for windows (any apps I install in win will end up in /winapps via the gift of a windows ext2 driver), a 1Gb swap (which will end up being 2Gb once I thin out windows enough that i can take a gig away from it), and the rest, about 40Gb, formatted ext3 and mounted as /.

The reason I'm starting over btw, is because of exactly the problem I'm describing, no DVD drive visible in either windows or linux.

So, I goes about setting up windows on a 2Gb partition, which installs as well as windows ever does, meaning i need to do half an hours updates once I've installed the drivers for my network card.  Still, everything that has a driver is working at this point, which includes my built-in sony DVD-Writer (it's actually removable so you can stick a hdd or second battery in its place, but I digress...)

So, next I set up ubuntu via the LiveCD.  Having booted from the LiveCD I can still get at my DVD drive, so I do the install, which works fine.

Now, irritatingly I completely failed to check the state of my DVD drive immediately after install, and went on to do a full update, reboot, then install the nvidia drivers from the respoitory mentioned in the wiki BerylOnEdgy page, oh, and beryl too.

It's after that when I realised my DVD drive wasn't showing up in edgy.  Selecting CD-ROM 1 in the file browser gives me the error "mount: Special device /dev/scd0 does not exist".  checking through /dev ive got sdaX (sata HDD) and sdbX (usb Hdd, i mounted sdb2 it to make sure, I figure sdb1 is that little bit of seemingly unpartitioned space the windows format tool seems to leave behind since mounting it requires I specify a partition type).  there's nothing in /dev matching hd* or cd*.  Sure enough, booting to windows reveals that my DVD drive has seemingly disapeared.

As I previously mentioned, I'd had the problem before I cleansed my system, and after reinstalling windows it was there and working, so it's not a hardware failure.  What's more, I'd have thought the only thing changing in relation to a windows boot would be the addition of a few unrecognised partitions to the hard drive, and the insertion of grub before the windows bootloader.

One more thing worthy of note, I looked round the forums and google and came up with something possibly rather revealing.  if i mobify /boot/grub/menu.lst and add the kernel option acpi=off (and yes, i now realise that I should do this by pressing e when grub starts), i can boot into linux and my DVD drive is there and waiting for me.  There are only two major reasons why this isn't a solution.  Firstly, this only gives me the DVD drive back in ubuntu, where I don't really need to use it that much, it's still missing in windows.  Secondly, acpi=off breaks eth0, it's detected but can't do DHCP or access anything on the network when I statically assign an ip.  I also tried the noapic kernel option, but this just causes ubuntu to hang on the loading splash screen just shy of half way.

My plan of attack for tonight when I get home is to try and get windows to replace the bootloader with its own again for reasons of curiosity, see if that brings my DVD drive back in windows.  I'll then start over again and see if the drive still works after a raw un-updated edgy install, then check again after an update, then again after installing the nvidia drivers, just to track down the exact point of failure.

But before I do anything like that, does anyone hae any suggestions of things to try.  I'll also take any dumps anyone thinks might be useful, lshw seems to be one mentioned quite frequently for example.

Cheers in advance, and sorry again for the rediculous length.
ElginRoko

---

### Post by ElginRoko on 2007-03-08
OK, i've been doing more nosying around and turfed up this:

[http://ubuntuforums.org/showthread.php?t=336293](http://ubuntuforums.org/showthread.php?t=336293)

which if you follow through the link gives the story of someone whose having the exact problem I'm having, on almost the exact same hardware (it's an M570U not an M575U), so I'm gonna try setting up lilo tonight and hope that works.

---

### Post by Denis_iii on 2008-04-13
I have same laptop as you with same problem.....after installing Ubuntu 7.10 off live CD I have no CD-rom in windows or in ubuntu.....it lists one in ubuntu but it doesnt mount disks but in windows my cdrom drive isnt even listed it just shows my daemon tools virtual drive........did you find a solution?


Also have you managed to get the nvidia restricted graphics driver to work? No matter which way I enable it my system restarts in low-graphics mode at 800x600 on plug and play monitor and if I try to change to monitor that support 1920x1200 it asks for drivers ..... tried using envy for this but cant install as asking for ubuntu cd which I cant use cause awesome linux cant even manage detect a simple cd drive

---

### Post by thure on 2008-04-29
The problem is stil present **in Ubuntu 8.04**

After having installed Ubuntu from CD, the CD drive is missing in both Windows XP and Ubuntu.

If you boot up on the live CD ("Try Ubuntu without install"), the CD drive is detected fine!

Is it Grub or what is the problem?

---

