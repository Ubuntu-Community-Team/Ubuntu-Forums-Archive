---
title: "Trouble installing Jaunty on a Dell Inspiron"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by deer dance on 2009-07-29
Hello, I own a Dell Inspiron 1521, with Windows Vista pre-installed on it.

What I would like to do is replace Vista with Ubuntu 9.04. So, I burned a disc with the 64-bit version on it, however, the laptop would recognize it.

So I burned a second disc with the 32-bit version on it. Still wouldn't recognize it. So, I sent away for a disc from Ubuntu, since it would recognize my disc of 8.10. Unfortunately, if had a small scratch at the installation couldn't complete.  So, I figured that the disc would work.

So, This morning my copy arrived, but once it loads, I get an error. I get to the screen where I have the option to use the Live CD, install Ubuntu, test the memory, etc. However, regardless of which option I choose, a command line interface comes up saying if failed to load several objects and then it gives the directory /lib/modules/some file

That file named with a series of numbers.

It then goes on to give me a terminal structure allowing me to enter various commands, nothing particularly useful though.

My laptop runs on an AMD 64 Athlon X2 1800MHz.

If anyone has a solution to this problem, it would be much appreciated.

---

### Post by deer dance on 2009-07-29
Does anyone have a solution?

I know I only posted this an hour ago, but it's getting buried by other topics.

---

### Post by confused57 on 2009-07-30
Did you burn the Jaunty iso at the lowest speed possible, less than 8x?

If you did, another possibility is that the optical drive is having problems reading the install cd.  If you have another computer you can use, you could try making a bootable live usb, which is an option on the Jaunty live cd.  If you don't have access to another pc, you could try Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

A live usb would be feasible, if your computer is able to boot first to a USB device.

There may be some boot options you could try adding to the kernel when you boot up the live cd.

---

### Post by deer dance on 2009-07-30
I've tried various CD's and DVD's many of them worked.  Including one from Nero, MS-Office and a movie.

I've tried manually burning an image onto a USB drive, that didn't work, so, I'll try the UNetBootin thing, then get back to you.

---

### Post by deer dance on 2009-07-30
And no.

That didn't work, after trying all of the different install modes, several times each.

However, I do believe that the problem lies in the BIOS.

Some component isn't recognized by the Linux kernel.

However, in my earlier perusing of the internet for a solution, I was given a link to this site, where someone announced that they managed to install Ubuntu on their Dell Inspiron 1521.  The exact same laptop I have, AMD and all.

So, I know that it's possible, so, I'll keep searching for a solution and report back if and when I find one.

EDIT:

It appears there are different ways to burn it onto the USB drive, I'll try those.

EDIT:
no.

---

### Post by confused57 on 2009-07-30
If you can install Ubuntu 8.10, you should be able to upgrade to Jaunty 9.04:
[https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

Have you tried running the Hardy 8.04.3 LTS, which is supported until April, 2011?

I don't know if you could install Ubuntu 9.04 from the alternate install disc and get a fully functioning system...alternate install instructions here:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Maybe something in this thread will help:
[http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

---

### Post by uncre8d1 on 2009-08-11
Very interested in this topic, as i am getting the same issue in trying to install 9.04 on a Dell inspiron (this one a 5000 currently running XP).
*except I don't seem to have a problem reading the discs*

---

