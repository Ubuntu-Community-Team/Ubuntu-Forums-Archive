---
title: "[SOLVED] macbook boot has 20 sec. blank screen (ubuntu is the only system)"
date: 2008-06-11
forum: Hardware
---

### Post by flavio newbie on 2008-06-11
as anticipated my problem is that hoary, my only os on macbook, takes a long time to boot, because of a blank-screen that holds right at the beginning

on an old post with no solution they said that the guid was looking for the mbr, thats why its long

thanks in advance

---

### Post by flavio newbie on 2008-06-12
please..

---

### Post by stchman on 2008-06-12
> **flavio newbie said:**
> as anticipated my problem is that hoary, my only os on macbook, takes a long time to boot, because of a blank-screen that holds right at the beginning

on an old post with no solution they said that the guid was looking for the mbr, thats why its long

thanks in advance

Hoary????!!!!!

Time for an upgrade.  Do a clean install of Hardy 8.04.

---

### Post by flavio newbie on 2008-06-12
oops i meant hardy, they are both with h

---

### Post by flavio newbie on 2008-06-12
WARNING IMPORTANT UPDATE

as expected from a newbie i forgot something important:

sync the mbr via refit, see the step right after the installation of ubuntu


- Machine: Macbook 2.16 ghz core2duo black

- Os: H.H. ubuntu (read his highness) as unique operating system

- Symptoms: on boot the blank screen at the beginning hangs for 30 sec. before grub stage 1.5 starts the countdown before loading

- Problem: GUID and MBR are not syncronized and before grub is found it takes ages

- Solution:

1- insert the installation disk of Mac OS X and boot it. You need to press c as the screen lights up which will trigger the boot from cd.

- Once you are on the live cd desktop open utilities and launch disk utility. 

- Here make a partition (click on the disk icon and then the button that says partition, it will open your task window) with these characteristics:

Name: pointless
Format: I used mac os journaled and did the job
Size: entire disk
Properties: use guid, not Master Boot Record. You find it in the properties of the partition.

- Close the live CD and reboot

- On boot press the mouse button to trigger cd ejection

- Reboot with the Ubuntu cd inside

- let it start the live cd (sometimes the keyboard doesn't wake up)

- Once in Ubuntu -> System -> Administration -> Partition Editor and check that you have one partition of 200 mb dedicated to efi and the rest is free for you.

- Resize the big one to two: 2 gb for the swap and and the rest for ubuntu in ext 3 format

- Launch the installer of Ubuntu

- choose to manually manage the hard disk partitions and use sda2 which should be your large partition following the 200 mb for efi partition. Mount point is:   /
Format ext 3 primary partition

- then dedicate the other 2 gb to the swap.

- on step 7 you will be inquired to verify the settings and given the option to manage advanced settings, so go ahead and open the advanced settings and install the boot loader on /dev/sda2 which is not the default

- Now you have a working Ubuntu with my problem, the 30 seconds boot delay

- Check that Ubuntu works properly and reboot, just keep the power button warm

- Create a cd with the refit cd image [http://refit.sourceforge.net/doc/c1s5_burning.html](http://refit.sourceforge.net/doc/c1s5_burning.html) and boot it

- Syncronize the mbr using the partition tools (small icon under tux) use arrows

- reboot

- Put in Mac OS X disc 1, boot the live cd (press c) and open again disk utilities. Check the name of your two partitions and write down the one of your linux (it has a large size) should be disk0s2, and I don't see why it shouldn't

- close Disk Utility and open up a terminal

- type:

bless --device /dev/disk0s1 --setBoot --legacy --verbose

- Hope that everything works and press enter

- Close the live cd, reboot, eject the cd by holding the mouse button at the blank screen

- Reboot for one last time, and have your orgasm

if you dont like the sound at the beginning then do a clean install of mac OS X, turn down the volume and follow my how to from scratch

This information is gathered from sources I lost, as i was reading how to's and erasing operating systems, but haring is caring right?

let me know if it works for you guys too

to speed up the ubuntu boot there was also a nice guide, i'll update when i find it.


Update:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) tells you how to speed up even more
-

---

### Post by flavio newbie on 2008-06-12
now how do i flag it solved?

---

