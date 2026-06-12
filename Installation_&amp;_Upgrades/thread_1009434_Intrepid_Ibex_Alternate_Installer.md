---
title: "Intrepid Ibex Alternate Installer"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by EdwardFisher on 2008-12-12
Hey Guys.
Small problem, just installing Ubuntu intrepid ibex on my machine. Raid setup works fine, but it prompted for another CD.
"Please insert disk labeled Ubuntu8.10 Intrepid Ibex Release i386 (20081028)"

I was under the impression that the alternate installer should do the whole lot, seeing as its the same size as the live CD but text based.

Is it prompting for the live CD? I did the standard disk integrity check on the CD when i started the install and it said it was fine. 

Just means now i need to piddle about downloading the live CD of intrepid too?

Advice.
Ed

---

### Post by Pumalite on 2008-12-12
Burn a new CD. Do md5sum on the iso, burn at 4x or less. Do not use CD-RW
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by EdwardFisher on 2008-12-12
Hey Guys. Yeah burned to CD fine, CD verified during install process, CD ISO image md5sum is fine, raid and initial setup is all fine, just happens to prompt for another CD? Ill try a general install tomorrow, along with a new download of the original iso image, reburn to CD and see if that does the trick. Its very much the same as when older software prompted for another floppy disk, 'please insert disk ... press continue to continue the installation'

Cheers
Ed

---

### Post by EdwardFisher on 2008-12-13
Ok so this is starting to get annoying. Ive got the live CD for Intrepid and all the check sums etc are fine. 

I use the alternate installer to set partitioning and RAID etc, it prompts for another CD but strangely the CD tray will not open, i tried everything to open it, I don't want to force it as its pretty tough.

Anyone else having a similar problem with alternate installer wanting another CD. I think I'll download a new version of the alternate CD and check it out too.

---

### Post by mcwest on 2008-12-15
I have actually the exact problem as you people.I have no raid but have just 2 disks installed on my machine.MBR is on the first one hard drive,where I try to install ubuntu on the second one.

This is very weird behaviour.I'm going to install it on the virtual machine and I'll inform you.I think it might be the problem only with installing ubuntu on some types of disk arrays.

[EDIT]

I tried to install it on the single connected hard drive but no result, the same problem occurs.

---

### Post by tw0g on 2009-01-09
Am seeing the same problem.  Trying to install using the alternate CD with a software RAID configuration.

Poking around a bit in /var/log/syslog, it seems like the last thing the installation process does before getting stuck in the media change prompt is:

[INDENT][FONT="Courier New"]The following NEW packages will be installed:
  mdadm[/FONT][/INDENT]

By the way, if you hit Alt-F2, you can get to a shell and eject the CD ala:

[FONT="Courier New"]# umount /dev/scd0
# eject /dev/scd0[/FONT]


*UPDATE*

There are several bugs in LaunchPad that seem to refer to this same problem.  See, for example, [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/289702](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/289702) ... but alas, no resolution as far as I can tell.

I tried inserting and mounting the live CD, but no success in dismissing the media change prompt.

I'm stuck :-(

---

### Post by EdwardFisher on 2009-01-12
Thanks for the update tw0g, looks like we need to get in touch with the developers of the alternate CD. I'm a total newbie so i have no idea how to do that. I seem to remember seeing somewhere that its a single guy that's working on getting Ubuntu to recognize Raid setups.

@Mods: It might be an idea to sticky this for anyone else that has Raid setup problems and also to promote resolutions.

Cheers.
Ed

---

### Post by Pumalite on 2009-01-12
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

