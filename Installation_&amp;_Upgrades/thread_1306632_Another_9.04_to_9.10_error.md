---
title: "Another 9.04 to 9.10 error"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Denton Larson on 2009-10-30
Hi everyone

I have a problem, I had 9.04 and it worked fine, and figured I could load 9.10 and go on, big mistake.:(

It took forever to download 9.10, the next morning it was ready to restart, then I got some flashing and SLOOW to type in my username and password.

I managed to get in a root prompt and this is what I have
Mount of Filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try
Give root password for maintenance
(or type Control-D to continue):

I entered the password after alot of guessing, and got this
root@dlarson-desktop:~#

I did a ls and got
Desktop

I am copying this to my laptop I have.
HELP PLEASE! I am new to Ubuntu I have only had it going for about a year.

Denton Larson
WB0ZUR

---

### Post by XDevHald on 2009-10-30
From the looks of it the install did not complete and could be because of downloading failure for certain packages. I would recommend re-installing Ubuntu as the Mount drive is not recognized or found at all.

Sorry to see you're going through this as it doesn't happen often.

---

### Post by schroedl on 2009-10-30
I went through this exact same problem and are stuck with it.  I was able to log in, but it didn't do anything.  Now my filesystem won't mount.  What happened was my computer froze somewhere last night during the upgrade while I was sleeping.  I think it froze while the computer was removing some packages.  I'm worried about loosing the files.  Is there a way to access the files now?  I got the maintenance shell as well with the control-d thing, but it was after that when my filesystems stopped mounting all together.

---

### Post by Chow7 on 2009-10-30
This is exactly what happens to me when I try to upgrade to 9.10.  I installed a fresh copy of 9.04 and upgraded to the 9.10 RC and same result as the upgrade to the final version of 9.10.  after it reboots I just get a login screen and the screen is flashing.  I too am a noob to linux.

---

### Post by XDevHald on 2009-10-30
> **schroedl said:**
> I went through this exact same problem and are stuck with it.  I was able to log in, but it didn't do anything.  Now my filesystem won't mount.  What happened was my computer froze somewhere last night during the upgrade while I was sleeping.  I think it froze while the computer was removing some packages.  I'm worried about loosing the files.  Is there a way to access the files now?  I got the maintenance shell as well with the control-d thing, but it was after that when my filesystems stopped mounting all together.

Do the following.

When you're at the login screen choose your session as **Xterm** which has no GUI display and will pop up a terminal. Execute the command: **sudo apt-get update** then follow the prompts as it SHOULD give you the packages that were not installed.

Keep us posted.

---

### Post by wyliecoyoteuk on 2009-10-30
If you are worried about your files, booting from a LiveCD may make it possible to recover them.
Not always a good idea to upgrade on the release date, for various reasons, but I admire your enthusiasm.

---

### Post by Chow7 on 2009-10-31
Apt-get update did not fix the problem for me.

---

### Post by verton on 2009-11-03
I upgraded from Jaunty 9.04 to Karmic 9.10.
When I turn on the computer and came to the Unbuntu logo;
it started filesystem checks and ended at 40%.
then:
Mount of filesystem failed.62d477-bc93-4754-9441-2097889ce21f
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@..............:~#
My question is what is the command?

---

### Post by Denton Larson on 2009-11-09
Hi everyone

I got the new 9.10 to run, I had to do a re-format of the drive :(
But 9.10 was WAY slow. So I re-formated again and loaded 9.04 and it is happy. Now I need to put in all of the add-in's :)

Denton Larson
WB0ZUR

---

### Post by manilaph on 2009-11-09
same exact problem:

usplash: setting mode 1152x864 failed
usplash: using mode 1024x768
Mount of filesystem failed
A maintenance shell will now be started
CONTROL-D will terminate this & retry
root@sgo-desktop:

but this is not from an upgrade. this was from a fresh install and it was working for a couple of days without problems.

is there a fix?

---

