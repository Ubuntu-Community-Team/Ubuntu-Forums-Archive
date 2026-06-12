---
title: "When Installing &quot;-bash: /dev/null/: Permission Denied&quot;"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by Epidural on 2008-12-24
I've installed Ubuntu on this drive before. The reason I'm re-installing is because I switched boards (to an old-ish P4 Intel board with that oh so lovely rambus memory.)

I can't for the life of me figure out what the heck I'm supposed to do to get Ubuntu to install. I've removed all drives but the one I'm using for my OS's. I've completely wiped this drive of everything.

Earlier, I successfully installed Windows XP Pro with absolutely no problems on this same drive. I tried installing Ubuntu after this, and the problems started. It loads the loading screen for Ubuntu, meaning when I put in the CD it gives me my Install, Try without changes etc. options, and has the scrolling marquee bar or whatever after choosing install. It loads the bar, but when it would normally bring me to the partitioner/set-up menus, it brings me to a command promt, with  bunch of words that FLY BY before it. The last set of information it gives me is a lot of lines saying "-bash: /dev/null: Permission denied". I try using it as a live CD, same problem. I've tried with two seperate previously-working Ubuntu 8.10 Desktop disks. I checked both CDs for errors, and within about 3 seconds both discs "appear" to have 7 files corrupt. I can't see how this would be so, they both worked no more than 3 days ago. 

I do have a command prompt "ubuntu@ubuntu:~$" but I have no clue what to do from here.

Any help is greatly appreciated. I'll give any information I can if you need it (just ask of course.) 

Thanks in advance for your time.

---

### Post by hailukah on 2008-12-25
If they were made from the same iso then it may be bad.  Have you checked the md5sum of the iso?

---

### Post by Andy in Indy on 2009-01-04
I have a similar problem.  The CD worked fine as a trial, but the laptop powered down during installation around 98-99%.  Now I get the same thing as he does when I start the laptop (but it is booting from the hard drive, not the CD-ROM).

The suggestion was to check the iso file - how do I check the md5sum in windows?  I mean, where do I find what the check sum should be and where do I find a program for Windows XP to do this?

-Andy in Indy

---

### Post by Dman33 on 2009-02-28
I am having the exact same problem when trying to install onto a Dell Latitude L400.  The installer begins and then spits me out to to a bunch of the /dev/null: Permission Denied

I also have the following after the permission denied lines:
[  253.049483] aufs au_xino_do_write:242:apport[5897]: I/O Error, write failed (-20)
[  253.049673] aufs au_xino_write:242:apport[5897]: I/O Error, write failed (-5)
[  253.059064] aufs au_xino_do_write:242:apport[5897]: I/O Error, write failed (-20)
[  253.059152] aufs au_xino_write:242:apport[5897]: I/O Error, write failed (-5)

It is from a brand new cd burnt with iso downloaded just last week.
:confused:

---

### Post by saul11 on 2009-03-07
Same here, although using Wubi, posted my problem at [http://ubuntuforums.org/showthread.php?p=6842711#post6842711](http://ubuntuforums.org/showthread.php?p=6842711#post6842711)

---

### Post by Epidural on 2009-08-04
I'm sure this thread has been long forgotten about, but the way which it was fixed was by using a different disc drive as a master to boot from. For whatever reason, Ubuntu did not like my DVD-Reader as a master. Using a CDRW as Master instead, with DVD as slave worked. Nothing is wrong with the DVD drive, it just didn't seem to agree for some reason.

---

