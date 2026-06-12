---
title: "Installation disc problems... this is my last attempt"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by bradsthompson on 2009-08-03
I will admit, that this is the first that I have ever ventured into the world of linux... so far, it is proving to be a big headache.

I downloaded the Ubuntu 9.04 (x86) ISO and burned it using ImgBurn.  I ran the verification and everything was fine.  I booted from the disc and chose to install.  It ran through a few splash screens and then came to a wonderful black screen with lots of random white lines on the bottom and red lines at the top.  There was green also.  It sat like this for a good 10 mins and I decided this was a problem.  I restarted the computer and booted from the CD again and this time I chose to check the disc for errors.  It came back with 5 errors.  I ditch this disc.

Next, I burn another CD using the Windows burning software that comes with Windows 7.  It runs a verification and everything is fine.  I boot the computer from this disc and choose to install.  It says it can't read the boot CD and that I need to reboot.

I burn yet another CD running the burner at 8x and run a test first.  The test is fine.  I burn it with verification.  Verification is fine.  I boot the computer and choose to install.  I come to the same black screen as before (imagine that) with all the different colored lines.

I do some googling and searching in the forums and try winMD5Sum.  The hashes match.  I do some more searching and do not find a definitive solution.  I download another file from another server.  I achieve the same results as before.  I download and burn from another server.  Same results.

Now, I download a previous version from yet a different server and I actually make it a bit further in the download screens before I see this:
[b]
/etc/init.d/rc: 317: /etc/rc2.d/s99acpi-support: Input/output error
* Running local boot scripts (/etc/rc.local)
...done.[/b]
_

I have no idea what this is.  Can someone please help me before I completely abandon Ubuntu altogether?..

EDIT: Consolidating the thread...

System Specs:

MSI K8TNeo-FSR/FISR
Abit Siluro Ti4200 GPU Card in AGP slot
AMD Athlon64 3000
1 GB Crucial Ram
80 GB HDD
Running Windows XP Professional Performance Edition (bare bones) as primary OS - would like to replace with Ubuntu

Picture of screen:

[IMG]http://img34.imageshack.us/img34/8574/img00051t.jpg[/IMG]

---

### Post by Sef on 2009-08-03
1) What are your system specs?

2) Did you burn at 4x or slower?

---

### Post by running_rabbit07 on 2009-08-03
Is it possible there is a problem with the CD burner?

---

### Post by bradsthompson on 2009-08-03
> **Sef said:**
> 1) What are your system specs?

2) Did you burn at 4x or slower?


1.  MSI K8TNeo-FSR/FISR
    AMD Athlon64 3000
    1 GB Crucial Ram
    80 GB HDD
    Running Windows XP Professional Performance Edition (bare bones) as primary OS - would like to replace with Ubuntu

2.  My drive said it could burn at 10x minimum.. besides, the CD seems to work on my laptop.

> **running_rabbit07 said:**
> Is it possible there is a problem with the CD burner?

Again, the CD seems to work on my laptop.  Besides, I've burned several different Windows 7 discs recently and they all work.  The computer I'm burning on is less than a year old.

---

### Post by running_rabbit07 on 2009-08-03
I think you are using the wrong ISO for your system. In the original post you say you are burning the x86 and in your response to Sef, you said you have the AMD64 processor. I hate to ask this of you but are you willing to download and try the AMD64 version offered on the Ubuntu page?

 I hope this works for you. Though I am new to Linux myself I am learning a lot and Ubuntu is the third Distro I have tried and is by far the best.

---

### Post by bradsthompson on 2009-08-03
> **running_rabbit07 said:**
> I think you are using the wrong ISO for your system. In the original post you say you are burning the x86 and in your response to Sef, you said you have the AMD64 processor. I hate to ask this of you but are you willing to download and try the AMD64 version offered on the Ubuntu page?

 I hope this works for you. Though I am new to Linux myself I am learning a lot and Ubuntu is the third Distro I have tried and is by far the best.

I was going to try this as well but I don't believe that I need to download the 64 bit version to make it work.  It should boot fine with the 32 bit version even if I have 64 bit processor.  I am leaning towards it being a problem with my graphics card but I have no idea why or how to fix it.

---

### Post by NESClUS on 2009-08-03
> **bradsthompson said:**
> ... Now, I download a previous version from yet a different server and I actually make it a bit further in the download screens before I see this:

/etc/init.d/rc: 317: /etc/rc2.d/s99acpi-support: Input/output error
* Running local boot scripts (/etc/rc.local)
...done.
_


I have no idea what this is.  Can someone please help me before I completely abandon Ubuntu altogether?..

The media or architecture are not the problem.

 I would say that the problem would be with the chipset, I haven't found if GPU is a part of the chipset- can you find out what GPU you have? 

Please try to describe the problem more details, specially the part about the booting screens - can you switch to TTYs during booting? you'll do that by hitting ctrl+alt+f1/f7 while f1 are boot logs and f7 is the graphical interface.

the message about acpi is just reminding why a chipset from VIA is not good thing for your or anyone elses computer.

---

### Post by bradsthompson on 2009-08-03
> **NESClUS said:**
> The media or architecture are not the problem.

 I would say that the problem would be with the chipset, I haven't found if GPU is a part of the chipset- can you find out what GPU you have? 

Please try to describe the problem more details, specially the part about the booting screens - can you switch to TTYs during booting? you'll do that by hitting ctrl+alt+f1/f7 while f1 are boot logs and f7 is the graphical interface.

the message about acpi is just reminding why a chipset from VIA is not good thing for your or anyone elses computer.

Oops!

I meant to include that in the post earlier.

I have a Ti4200 GPU.  I could not do anything when the screens locked up.  On one screen, I could move the mouse - the cursor was a black and blue X - but clicking around did nothing.  I could not get any keyboard commands to respond... not that I know any for linux.

---

### Post by Hobgoblin on 2009-08-04
When you boot from the Ubuntu disk and select the option to try Ubuntu what happens?

---

### Post by bradsthompson on 2009-08-04
> **Hobgoblin said:**
> When you boot from the Ubuntu disk and select the option to try Ubuntu what happens?

/etc/init.d/rc: 317: /etc/rc2.d/s99acpi-support: Input/output error
* Running local boot scripts (/etc/rc.local)
...done.
_

---

### Post by bradsthompson on 2009-08-04
> **NESClUS said:**
> The media or architecture are not the problem.


Please try to describe the problem more details, specially the part about the booting screens - can you switch to TTYs during booting? you'll do that by hitting ctrl+alt+f1/f7 while f1 are boot logs and f7 is the graphical interface.
.


again, ctrl+alt+f1/f7 didn't do anything on that screen.  Also, the splash screens have tiny lines in them when they are actually working.  This is why I think it is an issue with the graphics card.


BTW, I REALLY appreciate the help.  Hopefully, this will work.

---

### Post by bradsthompson on 2009-08-04
bump

---

### Post by bradsthompson on 2009-08-04
For the hell of it, I downloaded, burned and booted the AMD64 version of Jaunty with the EXACT same results.

I've done some searching for K8T Neo; K8T800; and Ti4200.  No one is having the same symptoms that I am.

My first inclination is that my GPU is just simply old and non functional but my stripped down version of Windows is able to do it with no additional drivers so why can't the most advanced version of Ubuntu do it?  I ran memory tests too and they came back fine.  I'm really just at a loss.  With all the other problems I see people having with Ubuntu installations and upgrades I'm wondering if this is such a good move for me...

Bump for the updated thread...

---

### Post by running_rabbit07 on 2009-08-04
> **bradsthompson said:**
> For the hell of it, I downloaded, burned and booted the AMD64 version of Jaunty with the EXACT same results.

I've done some searching for K8T Neo; K8T800; and Ti4200.  No one is having the same symptoms that I am.

My first inclination is that my GPU is just simply old and non functional but my stripped down version of Windows is able to do it with no additional drivers so why can't the most advanced version of Ubuntu do it?  I ran memory tests too and they came back fine.  I'm really just at a loss.  With all the other problems I see people having with Ubuntu installations and upgrades I'm wondering if this is such a good move for me...

Bump for the updated thread...

It is saddening to hear Ubuntu isn't working for you. One system you could try is Debian. I will be quick to say that while it is one of the most powerful and versatile operating systems, it also takes a lot more studying and learning to be able to make it run right. 

There is also Mint, Arch and Fedora that I hear people saying work good for them, but I haven't tried those yet.

Out of  all OSes including XP and 2000 pro, Ubuntu has been the the best to me. I only have 3 problems with Windows, having to pay for good anti-virus software and the amount of time it takes to boot and the fact that mostly every update seems to require a reboot.

Edit: It also sounds like a new graphics card would be a good investment.

---

### Post by oldfred on 2009-08-04
I also had problems burning some CD's but it was the CD. Cheap music CD's do not work for data reliably.
Here is an old 2006 solution.
[http://ubuntuforums.org/showthread.php?p=1320697#post1320697](http://ubuntuforums.org/showthread.php?p=1320697#post1320697)
You will have to update with the current old version of the nvidia drivers as the current new version is for 7000 series or newer (I think).

---

### Post by ugm6hr on 2009-08-04
Just to summarise:
Working 32-bit 9.04 CD (confirmed md5sum and verified CD, works on another computer)
Boots to initial LiveCD menu
Fails to boot to desktop

I would suggest you try changing some of the "advanced settings" - I can't even remember what they all do, but often turning off acpi support will allow the LiveCD to boot OK.  It is something like F4 or F6 at the boot menu.

---

### Post by presence1960 on 2009-08-04
+1 ugm6hr!

look here for [boot options]("https://help.ubuntu.com/community/BootOptions")

---

### Post by ptn107 on 2009-08-04
Why don't you just use the alternate install disk for 9.04[1]?  It uses a text based installer (which may circumvent your video problem) but installs the same stuff as the regular desktop cd.

[1]_[http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso]("http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso")_

MD5SUM here: _[http://releases.ubuntu.com/jaunty/MD5SUMS]("http://releases.ubuntu.com/jaunty/MD5SUMS")_

---

### Post by ugm6hr on 2009-08-05
> **presence1960 said:**
> look here for [boot options]("https://help.ubuntu.com/community/BootOptions")

This is rather more helpful than my rambling description....

I suggest: F6 & turn off acpi support; if that still doesn't work, try some of the other options too; F4 and using Safe Graphics mode might also be sensible.

---

### Post by bradsthompson on 2009-08-05
> **ugm6hr said:**
> This is rather more helpful than my rambling description....
 
I suggest: F6 & turn off acpi support; if that still doesn't work, try some of the other options too; F4 and using Safe Graphics mode might also be sensible.
 
OK.  I have now succesfully installed Ubuntu!
 
I stumbled on it on my own by pressing F4 and doing the safe graphics mode I think.
 
I tried this on the x86 version and nothing happened... the x64 version worked fine.
 
Another strange quirk is that after I installed Ubuntu and booted it for the first time it searched for driver updates and found one for my video card.  I installed it, rebooted, got a completely black screen.  I let it sit for about 20 minutes, gave up, and did a complete reinstall of Ubuntu.  I think there is definitely something wrong with current drivers available and my GPU.  I'm leaning towards my GPU just being a piece of crap.
 
Either way, I am now running Ubuntu (without an updated driver) just fine and will move on to migrating my media files and hard drives to this computer as a media server.
 
Thanks for all the help!!

---

### Post by ugm6hr on 2009-08-05
> **bradsthompson said:**
> Either way, I am now running Ubuntu (without an updated driver) just fine and will move on to migrating my media files and hard drives to this computer as a media server.

After all that, I have one piece of further advice...

If you just want a media server, I would have suggested abandoning Ubuntu in favour of FreeNAS.

It has many benefits: no need for a GUI (hence no GPU issues); preconfigured for that purpose; managed from a networked computer via web browser; can be installed on a 128MB USB flash drive (or internal HD); built-in SMB, NFS and uPNP for file sharing; built-in backup options.

If you are interested, have a look at the FreeNAS link below.

---

### Post by bradsthompson on 2009-08-05
> **ugm6hr said:**
> After all that, I have one piece of further advice...

If you just want a media server, I would have suggested abandoning Ubuntu in favour of FreeNAS.

It has many benefits: no need for a GUI (hence no GPU issues); preconfigured for that purpose; managed from a networked computer via web browser; can be installed on a 128MB USB flash drive (or internal HD); built-in SMB, NFS and uPNP for file sharing; built-in backup options.

If you are interested, have a look at the FreeNAS link below.

Thanks for the suggestion!  I may transition to that later.  The other two (minor) purposes for choosing Ubuntu was because I want to learn more about linux personally and my wife will use the computer every great now and then for basic word processing and to surf the web.  We won't be running anything too intensive on this machine so it can certainly serve all three purposes.  Thanks again!

---

### Post by Sid 6.7 on 2009-08-05
I've skimmed through the replies & didn't see anything about the Windows installer Wubi.  I'm new to Linux also & found this to be the easiest way to install Ubuntu if you got the disk space & you just want to mess with it.  Here's the link to the windows installer:
 
[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)
 
Scroll down & you'll see it the DL link.  It automaticaly partitions your drive, finds the necessary Jaunty flavor, & adds it as a secondary partion.  PLUS it starts to DL the torrent for the .iso.
 
Look at the name of the iso, cancel the set up, & go to this page for a direct link for a faster iso download:
 
[http://www.ihackintosh.com/2009/04/download-ubuntu-904-final-version-codename-jaunty-jackalope/](http://www.ihackintosh.com/2009/04/download-ubuntu-904-final-version-codename-jaunty-jackalope/)
 
add the iso to your desktop with Wubi also on the desktop & restart the setup.  There is NO BURNING REQUIRED!  Plus if you mess up Ubunutu beyond repair save Wubi & the iso.  Wubi has the option to uninstall & reistall a FRESH OS (I've done this once, lol).
 
Like I said this is the simplest, fastest way to get a dualboot with Ubuntu.  Good luck :D

---

### Post by ugm6hr on 2009-08-05
> **Sid 6.7 said:**
> Like I said this is the simplest, fastest way to get a dualboot with Ubuntu.  Good luck :D

The intention was to replace MS with Ubuntu, not dual-boot.  A goal that (apparently) has been achieved now.

---

### Post by presence1960 on 2009-08-05
> **Sid 6.7 said:**
> I've skimmed through the replies & didn't see anything about the Windows installer Wubi.  I'm new to Linux also & found this to be the easiest way to install Ubuntu if you got the disk space & you just want to mess with it.  Here's the link to the windows installer:
 
[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)
 
Scroll down & you'll see it the DL link.  It automaticaly partitions your drive, finds the necessary Jaunty flavor, & adds it as a secondary partion.  PLUS it starts to DL the torrent for the .iso.
 
Look at the name of the iso, cancel the set up, & go to this page for a direct link for a faster iso download:
 
[http://www.ihackintosh.com/2009/04/download-ubuntu-904-final-version-codename-jaunty-jackalope/](http://www.ihackintosh.com/2009/04/download-ubuntu-904-final-version-codename-jaunty-jackalope/)
 
add the iso to your desktop with Wubi also on the desktop & restart the setup.  There is NO BURNING REQUIRED!  Plus if you mess up Ubunutu beyond repair save Wubi & the iso.  Wubi has the option to uninstall & reistall a FRESH OS (I've done this once, lol).
 
Like I said this is the simplest, fastest way to get a dualboot with Ubuntu.  Good luck :D

Wubi is not meant to be a permanent solution. it is also subject to performance degradation due to fragmentation as it is installed inside the windows file system. The OP was looking to replace windows, not install inside of it.

[see here]("https://help.ubuntu.com/community/Wubi")

I would only recommend wubi in a case where someone isn't sure if they really want to use Ubuntu, that way they don't repartition their hard disk(s). This obviously is not the case in this thread.

---

