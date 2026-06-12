---
title: "Winbook TW700"
date: 2014-12-31
forum: Hardware
---

### Post by kellyvotrenom on 2014-12-31
I just purchased a Winbook TW700 for dirt cheap.  I plan to use it as is for now but...

What is the possibility of installing Linux on it, either now or in the future??

Here's some specs


[LIST]
[*] HD IPS LCD 7" 1280x800 Display 
[*] Intel BayTrail-T Z3735G 1.33GHz Quad-Core CPU 
[*] 1GB RAM & 16 Flash Storage 
[*] Windows 8.1 OS 
[*] Expandable up to 64GB via microSD Card 
[/LIST]
 The WinBook 7" TW700 Tablet has 16GB of integrated storage, which can  be expanded via microSD Card. Includes 1 year subscription for Office  365 Personal.

Thanks

Mark Springer
industrial arts

---

### Post by ianlantzy on 2015-01-13
I also purchased one of these last Saturday. It's an incredible little tablet for the $60 I spent on it. My understanding is, however, that it uses 32-bit UEFI with no legacy BIOS support. That makes using Ubuntu (or really anything other than Windows), a bit of a pain.

---

### Post by mtndrgon on 2015-01-14
I got ubuntu to install .. but in no way stable and no wireless anything. (on the 8 and 10 inchers anyway). Needed the keyboard so mainly messed with the 10, tw100. 
Issues: no touch, no wifi, no bt, no battery or power management. 
alternatively tried the fedlet custom from the dell venue forums.
Issues: no wifi, no bt, partial power management (almost cooked the processor) and single point touch only with both x and y inverted.

both installs failed to initialize the HCI bus which the sdio inputs are related to.. kernel panic on attempts to suspend or blank screen/ screen saver

---

### Post by ianlantzy on 2015-01-28
So it sounds like there are a bunch of drivers missing, which isn't surprising being as these are essentially generic tablets. It's just a shame because I feel like if they could properly run Ubuntu (or anything other than Windows), they would be pretty powerful little tablets with a decent amount of space. I managed to play One Way Heroics and Beat Hazard on the thing and they actually ran pretty smooth, only real drawback was the memory usage.

---

### Post by mtndrgon on 2015-02-10
I swapped over to fedlet on my install and really only lack bluetooth and rotation at this point. There are source files for the wifi, axis sensors and the intel package is available. Need to make/compile/install manually.. but I am 2 weeks stable on my TW100. Stableish anyway.

---

### Post by ianlantzy on 2015-03-24
I got Arch to boot on my TW700 from USB. Had to manually boot grub.efi file from an EFI shell. Got stuck there before installing due to my USB hub being unrecognized. I would bet an Ubuntu installer with a 32 bit efi file would work great but I have no idea where to acquire one, or if one could built using something like the boot cd/dvd customizer.

---

### Post by masnatacion on 2015-05-28
[COLOR=#666666][FONT=Helvetica Neue]Hi[/FONT][/COLOR]
[COLOR=#666666][FONT=Helvetica Neue]I got it this error during install:[/FONT][/COLOR]
[COLOR=#666666][FONT=Helvetica Neue]Executing grub-install /dev/mmcblk0 failed

ubuntu 15.04
disable secure boot

[/FONT][/COLOR]
[COLOR=#666666][FONT=Helvetica Neue]can u help me?[/FONT][/COLOR]
[COLOR=#666666][FONT=Helvetica Neue]greetings[/FONT][/COLOR]

---

### Post by ianlantzy on 2015-07-23
To anyone who visits this thread looking to install Ubuntu on the TW700 I found a working walkthrough here:

**Part 1**
[URL="http://infosoda.com/ubuntu-tw700-1/"]http://infosoda.com/ubuntu-tw700-1/
[/URL]
**Part 2**
[URL="http://infosoda.com/ubuntu-tw700-2/"]http://infosoda.com/ubuntu-tw700-2/
[/URL]
There are some bugs on mine I'm trying to work out.

---

