---
title: "installation  keeps looping-also destroys ports on computers"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by rolypolycat on 2009-01-18
Hello!

My reasonably savvy computer friend (with hardware, anyway), took apart my old, nonworking computer, and put the extra hard drive he found in it, one I'd completely forgotten was even in it, into a new tower with what I believe was an Ameritrend? bios on the motherboard. It had originally had Win XP on it, but there was nothing there now. When I attempted to install xubuntu, it would start with the screen asking what I wished to install, run some info on the screen so fast I couldn't see it, go blank, then- start all over again with the install screen. I tried a command line install; this time, it got to initrd, then restarted. When I ran yet another Ubuntu disk from Linux Format magazine, it started up with the usual screen asking what sort of install I wanted, then restarted again and again. 
I had another 160 gig drive with a working linux install on it. I know the hardware would have been different, since it was taken from the trashed computer. This time, it kept giving me a GRUB menu. I'd make a choice, it would start to boot- then back to the grub menu again.
Here's where it gets even more peculiar. When Rich, my computer buddy, took the tower and drive home, and plugged the 80 gig drive into 2 of his machines, it screwed them up. It wiped out the ports, is what he said. These were Windows xp machines. He also discovered it trashed ports on the motherboard on the tower he gave me. Rich said it was a "chimera" that is, it merged code from win xp and linux, and screwed things up. He also said when he tracked down the virus code, it was barely 100kb long, but was designed to ruin the ports. 
I take what he says here with a bit of confusion, because he's not that familiar with linux.
All the same, I know the disks I used to install linux were perfectly good, because they're the ones I've used time and again to install ubuntu on my previous 2 machines. There were no error messages when the install ran, or at least, none that could be seen. It just kept on looping. And Rich says the serial ports, and some others , are trashed.
So, anyone have any idea what sort of virus, malware, or just plain screwed-up mess is on this machine? And how to repair the missing ports? I've been using linux for the past 5 years, and I've never seen anything like this.
Thanks in advance for any info on this!

---

### Post by pytheas22 on 2009-01-18
With due respect to your friend, I think it's highly unlikely (to say the least) that some kind of Linux-Windows hybrid virus caused physical damage to his hardware.  It's possible that there was some virus that messed up Windows on his machine, but I would suspect that it's only a software problem, and that if he did a fresh install of Windows, things would work.  Either that, or the ports were destroyed by something else and he doesn't realize it yet (could just be hardware failure due to use if it's an old machine).

As for your issues installing Xubuntu, have you tried using the [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")?  It might work better, especially if your computer has less than 256 megabytes of memory.

---

### Post by rolypolycat on 2009-01-19
As to installation, I tried a command line install, too, with the alternate cd; it only got as far as loading the initrd file, then started all over again. Whatever the problem was, it didn't let me install xubuntu-gutsy, hardy, or intrepid; it wouldn't install regular ubuntu, both hardy and intrepid, and it wouldn't even install mandriva or simplymepis, which I tried as a last resort. I don't know about windows; I don't have any install disks for win xp around any more-lost them somewhere along the way when I started using linux.

---

### Post by pytheas22 on 2009-01-19
hmmm, it sounds like your computer doesn't agree with Linux for some reason.  The only other thing I can think of is to find an installation CD for Windows, install Windows, then install Ubuntu using [wubi]("http://wubi-installer.org/").

You could also try a really minimalist distribution like [DSL]("http://damnsmalllinux.org/download.html"); if your machine has very little memory (how much do you have, and what kind of processor is it), this might be the only thing that would work.

Final thought: you could also put the hard drive in a different computer, install Linux to it there, then put it back.  This might work, although you would probably need to do some tweaking after putting the drive back into the original computer.

---

### Post by dabl on 2009-01-19
If you are mixing IDE and SATA drives on the same motherboard, that will sometimes keep the *buntu installer from allowing grub to go on the SATA drive.  You can disconnect the IDE drive, and get it to go to a SATA drive, assuming you aren't trying to install Linux on the IDE drive at the same time.

---

### Post by RJARRRPCGP on 2009-01-19
Is it rebooting, when in the middle of setting up stuff like Windows does with unstable hardware?

Your may have bad caps on your motherboard or PSU:

[http://badcaps.net](http://badcaps.net)

---

### Post by rolypolycat on 2009-01-24
Hello!

I fnally got linux on my 160 gig drive, but I had to do a fresh install. I guess it didn't like having a install already there. Thnak goodness for dvd backups; I didn't lose too much data. Ubuntu wouldn't go, but simplymepis6 did.

---

