---
title: "Extreamly long boot"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by 123456789123456789123456 on 2009-04-22
I have just installed Ubuntu 8.10 on a dell Dimension 2400 desktop computer, with 40gb hard disk, and currently 512mb ram.

I attempted boot from the live cd into live desktop, it seemed to freeze after the identification sound.  I restarted, and ran the install ubuntu, second option under the live cd menu.  It installed fine, but the system seems to lock up, I get the circle icon for the mouse after it gives the startup sound, but it does not move, the hard drive light continues to blink, but nothing is happening on the screen, screen is also black no color to it.  I restarted computer manually, went to recovery mode, second option under grub, only one kernal was listed.  after running file system check, I tried starting normally, I get no sound at startup, but the screen is a blank light orange backdrop.  no circle icon for the mouse, just the mouse pointer.

does anyone have any ideas?

---

### Post by whiteman on 2009-04-22
I had similar problesm. I had  an external harddrive. It was causing me to see pages of text, error messages, then finally it would start. Unplug anything in your usbs for now. Just a thought. I also tried once to install a windows emulator, quemm or somesuch thing. It played hell. Dual boots are no good for me too. Had to just go 100% Linux-Ubuntu. Kicked windows to the curb. (My other computer is an Apple) Failing that, make you a disk of the new iinstallation and start over.

---

### Post by wpshooter on 2009-04-22
Did you check the intregrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you try installing using the safe graphics mode parameter ?

If neither of the above helps, then downloading and try the installation from the ALTERNATE (text based) CD version of Ubuntu.

---

### Post by 123456789123456789123456 on 2009-04-22
I did not try testing the integrity of the disk, the cd drive that is on the machine is acting funny sometimes, may be unbalenced.  What i can try is some point later on, make another cd, and use the new dvd drive to boot from, see if that fixes the problems.  the only usb device plugged in is a usb keyboard.
the live cd detected it fine, as it allowed me to use it to go through the boot menu's.
I will check back again later, and deffinatly report on progress.

thanks for the help.

---

### Post by Mark Phelps on 2009-04-22
One thing you can do to see what's happening is go into your menu.lst file, and for the kernel stanza you're booting, remove "quiet" from the kernel options line.  That will result in a screen of scrolling text -- which will show you how far it's getting and maybe some error messages as well.

---

### Post by 123456789123456789123456 on 2009-04-22
I will try anything at the moment, I have gotten through with a build, and I am tired, I may get to the other machine later on tonight, I don't know for sure.

---

### Post by 123456789123456789123456 on 2009-04-22
> **wpshooter said:**
> Did you check the intregrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you try installing using the safe graphics mode parameter ?

If neither of the above helps, then downloading and try the installation from the ALTERNATE (text based) CD version of Ubuntu.

I checked the integrity of the disk, said it was fine, I am attempting safe graphics to see if it loads up, still has not loaded up.  reports no problems, the hard drive, and the cd drive is blinking the lights.

The thing I find strange is that even though, it did not start up the live desktop, when I went to install, it loaded the installer screen, along with the desktop pattern, everything fine.  It takes a while to load up the boot menu itself.  longer than it seems it should.  I have a slax disk, it loaded it up, started the live desktop, and runs perfectly.

I have one question, from this information, could there be some sort of error problem with 8.10, and the dimension 2400 desktops, or the cd be damaged in some areas but not all, enough to effect operation, but not be detected in the integrity scan?

---

### Post by 123456789123456789123456 on 2009-04-22
ok guys, I think I figured out the problem.  I also have an xubuntu cd, I managed to load it up, and boot into live desktop, under normal modes, after it loaded up it ran fast as to be expected under 512mb ram, seeing that this booted fine, I would assume that the problem is with the ubuntu cd, it has troubles of some sort and that was somehow transfered to the install on the hard disk.  Does this agree with anyone.  If I have to I will simply install xubuntu on the machine instead.  I understand that the new version 9.04 is released tomorrow.  I may just download it, and try that cd, instead of trying another copy of 8.10.  I also have a copy of 8.04 ubuntu, I can try to boot with it also.

---

### Post by 123456789123456789123456 on 2009-04-22
I seem to have confirmed my belief, I had a copy of ubuntu 8.04, it booted into live cd desktop fine, with no problems, the disk also read fairly fast.  so conclusion I have come up with is as follows, either the iso I downloaded was damaged in some way, causing installed systems, and live desktop load problems, the cd I burned it to got damaged some way corrupting one or more files, but did not read as a integrity problem.  The other possibility of an error existing in 8.10 seems to be elimitated since 8.10 xubuntu booted up in live cd desktop.
Instead of downloading a copy of 8.10 again, I will wait and download 9.04 when it comes out.

---

### Post by 123456789123456789123456 on 2009-04-22
I don't want to seem overly confident, and I am not entirely sure it is not a problem with some distributions of 8.10.  I don't have another copy of 8.10 ubuntu, I tested xubuntu and it worked perfectly, 8.04 ubuntu worked perfectly, I had a version of kubuntu8.10, it looked like it would work.  It loaded up, to the loading screen, got all the way to the picture of the desktop icon, and froze.  I am not sure, it could have been a problem with the cd.  At this point in time, I am waiting for the 9.04 to come out, download it and test the live cd boot.  It if boots to live cd desktop fine, and I am able to do an install.  The install should also boot fine.  If it does, and if no one comes forward with an explanation of why the copy of 8.10 was not working.  I will resolve this, and call it solved.

Again, thanks for all the posts, it really helps me out a lot.  the only thing I have run into one time before was that 7.10 did not boot in any ubuntu, or xubuntu on some machines, due to an error within the os, it did not like the cpu of certian computers, this was resolved, and fixed in 8.04.  I don't think something simular is happening here, because 8.10 of xubuntu started fine.

---

### Post by 123456789123456789123456 on 2009-04-24
problem solved

---

