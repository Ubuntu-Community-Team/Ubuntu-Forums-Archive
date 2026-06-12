---
title: "Can't install a bootloader no matter how hard I try"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by katanacb on 2006-02-03
Hello there, 

I've been trying now for 2 days (!!) to get Ubuntu installed on my home machine, and no matter what I do, how much I try, or how many fingers I cross for good luck, I can't get Ubuntu to install a bootloader on my machine.  I've been a Linux user for a long long time now, and this is the first time that I've ever had such a problem.

System:
AMD Athlon64 3200
2GB RAM
80GB as hda, HPT RAID controller as sda1 and sda2 (but have to install modules for that after everything's up and running)
nvidia FX5200
DVD ROM and DVD burner
MSI Motherboard

I've setup all my filesystems with XFS, / and /boot are on separate partitions.  

Interestingly enough, on other distros I have to boot with things like "ide=reverse, hde=noprobe hdf=noprobe, hdg=noprobe, hdh=noprobe" to get Linux to not core dump or hang on installing the hpt366 module, but Ubuntu seems to ignore or not honor this sequence.  I figured out a way around this finally, so it might be partially related to the problem I'm having now, I dunno.

Some things I've noticed:

I get a warning about GRUB not being safe to install on XFS (funny, first time I've ever heard that one), so I tried to install Lilo.  Fails at 50%, or returns error 1.  Then I got the option to install GRUB.  Yup that fails too, at 50% or I think gives error 32.  Dropping to a shell, here are some of the errors that I am seeing on the screen:

"Errors were encountered while processing:  lilo
E: Sub-process /usr/bin/dpkg returned an error code (1)"

If I chroot into the "new" environment, and run lilo -v, I get:

Fatal: open /vmlinuz:  No such file or directory

Well, I thought I'd get around all this and try to install the boot loader to a floppy, but no matter what device I choose (/dev/fd0. /dev/floppy/0, etc) at the lilo screen, it always fails saying that what I specified is not a valid block device ... which is strange because I can do something like "mount /dev/floppy/0  /target/media/floppy" and it works just fine.  Do I need to be in expert mode for this to work?

This is so frustrating because I setup my laptop EXACTLY the same way, with XFS, and the install went just fine. (and Ubuntu works like a champ, which is why I wanted to setup my home machine(s) with it as well).   The only difference here is the hardware, the layout and partitions are identical.

I've read through several threads here and it looks like lots of people have this problem, but the suggestions that I've tried based on other's problems haven't panned out.  

Anyone have any ideas?  I'm pretty much at a loss ... :(

---

### Post by katanacb on 2006-02-04
well, I've gotten a little further.

I stumbled across a thread in the forums that suggested that I don't use XFS, but use ext3 instead as there is some issue with Debian's installer and XFS.  So I did that, and the grub bootloader installed with no problem.

Now, having said that, I think it should be easier to install a bootloader to a floppy disk than what I ran into.  Maybe I was just specifying the floppy device wrong, I don't know, but it was basically impossible to get lilo or grub on a floppy using the installer.



Now, I've run into a multitude of other problems, which I'm trying to sort out.  I must admit, this is my second machine to install Ubuntu on... the first was a snap and went flawlessly (this was a Dell laptop), and it has to be the best distribution I've ever used on a laptop before.  I really want to get it up and running on my other machines here at home. but my main home machine, however, has been a  total and complete nightmare to install Ubuntu on.   I've never had so much trouble installing Linux on a box in the 8 or 9 years I've been using it.  I'll keep plugging away at it, I'm not ready to give up yet, but the neighbors can probably hear my frustration with things :)

As an aside, what's the best way to request upgrades and changes to future releases?  There are some things I've noticed so far that are a bit strange with Ubuntu (I come from other distributions, and KDE) and thought I might suggest some changes for future releases.

---

### Post by katanacb on 2006-02-05
well after several days of plugging away at this, I've got things up and going now.  I'm posting what I did in case anyone else runs into similar problems with the installation that I did.

The main issues that I ran into were: (1) the hpt366 module caused a kernel oops when the installer would try to detect hardware (modprobe -v ide_generic would fail)  and (2) once I figured a temporary workaround for (1), I couldn't install a bootloader.

Solving (2) turned out to be fairly easy -- I just changed the filesystem types that I was using from XFS to ext3 and grub installed just fine.  Someone on the forum boards said this is an issue with the Debian installers or something, hopefully they'll get that straightened out soon.

The problem with (1) was a little more difficult.  For those of you that have a HighPoint RocketRaid card (mine is a 133) that uses their hpt37x2 module, you'll probably run into a similar problem as me ... here's what I did to solve it.

1).  Pop your case and remove the card before trying the install.  (trust me, this is the easiest thing to do, rather than messing aroun with boot options, or modprobing things later).  Don't worry, any RAID arrays that you've defined should still be OK when you plug the card back in later (they were for me).

2).  Boot and go through the install ...  (don't forget about using the right filesysems!)

3).  Once you get up and going, and apply all the latest patches, you'll need to rebuild your kernel.  There's a pretty good how-to on doing this on this site somewhere, just search for it and follow the instructions.  When you do the rebuild, go into "device drivers -->  ATA/IDE and un-check the hpt 34x and 366 modules.  Don't build them as modules, just un-select them all together. They are what's causing the kernel panic.

4).  Save your config and build the kernel,  then install it per the howto.

5).  If you are using GRUB, go into your 'menu.lst' file (/boot/grub) and append "ide=reverse hde=noprobe hdf=noprobe hdg=noprobe hdh=noprobe" after the words 'silent splash' in your new kernel stanza line.

6).  Shutdown your system.

7).  Re-install the HighPoint card and reboot your system.  You should come up a-OK.

8)  Download the hpt37x2 driver from HighPoint technologies.  Un-tar it,  build it, install it and you should be good to go.


I really like Ubuntu (I come from KDE running under about every distro out there, but as over the years I've run SuSE, Gentoo, RedHat, and Mandrake / Mandriva), and I must say GOOD JOB to the developers ... despite the installation troubles on this machine.  I'm posting my issues and solution(s)  so that maybe they will help someone else out there....

---

