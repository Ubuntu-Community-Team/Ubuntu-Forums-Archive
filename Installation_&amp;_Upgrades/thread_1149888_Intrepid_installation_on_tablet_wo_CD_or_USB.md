---
title: "Intrepid installation on tablet w/o CD or USB"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Enter t'Ibex on 2009-05-05
I am trying to load Intrepid on a Fujitsu tablet.
The tablet will not boot from USB and has no bootable CD.

I have an adpater to plug the drive into my PC.  

Last night I loaded Intrepid on to the tablet HDD, but of course the driver set was so screwed that I could not make the tablet operational.

Could someone tell me a way where I could put the whole installation disk onto the HDD and do the live load on the tablet instead?

Cheers!

---

### Post by Enter t'Ibex on 2009-05-06
I tried creating and loading two partitions on the drive one with a copy of the live disk and one to boot from.

It seems to have problems booting from one and finding the other.

Is it possible to use this proc:

[http://www.syschat.com/install-windows-xp-without-floppy-cd-463.html](http://www.syschat.com/install-windows-xp-without-floppy-cd-463.html)

But instead of XP using the stuff from the ISO disk instead?

Thanks for any assistance you can provide!
Cheers

---

### Post by Favux on 2009-05-06
Hi Enter t'Ibex,

See if this thread has anything for you.  Start with post #8:  [http://ubuntuforums.org/showthread.php?t=1121058](http://ubuntuforums.org/showthread.php?t=1121058)

Good luck!

---

### Post by Mark Phelps on 2009-05-07
> **Enter t'Ibex said:**
> I am trying to load Intrepid on a Fujitsu tablet.
The tablet will not boot from USB and has no bootable CD.

I have an adpater to plug the drive into my PC.  

Last night I loaded Intrepid on to the tablet HDD, but of course the driver set was so screwed that I could not make the tablet operational.

Could someone tell me a way where I could put the whole installation disk onto the HDD and do the live load on the tablet instead?

Cheers!

Wish you luck with the Intrepid install on the Fujitsu tablet PC.  I have a Fujitsu T4020 tablet PC running great under Hardy.  I booted from first, the 8.10 LiveCD, and then from the 9.04 Live CD, and in both cases, no tablet functions worked.  I was able to hack around and get the stylus back working but was left with two problems that I was unable to resolve (despite lots of posting in this forum):
1) Bezel buttons do not work, in fact, NOTHING is able to detect them -- xev, acpi-support, dmesg -- nothing even sees them.
2) Xsetwacom no longer rotates the stylus, thus rendering, tablet PC orientation useless with the stylus.

So, I'm staying with Hardy -- which sees all the keys and handles rotation without any difficulty.

---

### Post by Enter t'Ibex on 2009-05-07
An update from last night.

1) With the Tablet drive on a desktop I loaded DOS7.1
2) I then added the USB driver for DOS. (At this point the tablet will boot dos71. and will recognize the USB stick)
3) I have ubuntu on a USB drive, but wait for it!!!!! 

I cannot install Ubuntu because it says that umenu.exe cannot be run under DOS.  DUH I guess I knew that was coming.

Can someone can direct me to instructions (again I have looked but not seemed to find!) on how to install ubuntu from DOS.  Then I will/should/could be able to load onto the pc.

I have not seen a linux loader from dos that will work with ubuntu.

If I get this to work, i will it all with links and instructions. It may prove to be useful for other older computers.

Thanks for whatever help you can provide
Cheers

---

### Post by Enter t'Ibex on 2009-05-08
Mark:
I wish I had read your entire email two days ago.
Im going to try hardy tonight and see what happens
Cheers and thanks
Logan

---

### Post by Enter t'Ibex on 2009-05-17
I just want to close this down in point form as to how I needed to do this, a bit rough as I was trying to remember all the things that "worked" over the last couple of weeks!  I'm only adding details for the parts where I couldn't find the info in forums, or documentation, or elsewhere on the net.

1. Get a desktop with Ubuntu (its what I had see c) below) with unetbootin and G-parted installed.
2. Get a 2.5" to 3.5" adapter
3. With the power off on all puters, remove the HDD from the laptop and connect it into the PC. Put the L-HDD as the primary and the D-HDD as a slave since you will not be able to select the 2.5" as a primary (no jumpers) and you will be able to select the 3.5" as a slave.
4. boot the desktop and go into the bios.  Make sure that both HDD's register and change your boot order to SLAVE HD first.
5. Make sure the desktop boots to the D-HDD and comes up in ubuntu.  At this point the L-HDD may or may not be mounted (in my case it was a brand new drive so it wasn't).
6. Go into G-parted and optionally start a new partition table to blow the whole L-HDD away for a clean start.   Create a 800 meg partition on the L-HDD. Restart. 
7. In terminal type gf-h and note the logical description for each drive.  I saw the D-HDD as sdb1 and the L-HDD as sda1.  Whatever you have write it down. Restart
8. The L-HDD should be mounted. Restart (and if things aren't looking right try restarting again)
9. Start unetbootin and put the distro of your choice on it (see unetbootin for details, its pretty straight forward). Make sure you pick the correct drive to install on, check it several times before you start the load!!!!! If you point to the D-HDD you will write over your current load = NOT COOL
10. If you need to make changes to the menu.lst file (like I did) do it now. in terminal CD /media/disk to change terminal to point to L-HDD then nano the menu.lst file and add your lines.
11. Shut everything down and then put the drives back the way they were. Don't forget to fix the desktop bios.
12. Boot the laptop and install from the menu. If things go well you should get your puter loaded.

Please note 
a) You should have a wired ethernet connection with a valid internet connection during installation (things just work out better if you have it when you end up trying to fix the install it will try to get update files automatically)
b) L-HDD = laptop hard-disk-drive D-HDD  = desktop hard-disk-drive
c) not saying you couldn't do this from windows, I just don't know how to...

---

