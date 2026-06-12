---
title: "Installing 8.10 in VirtualBox"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Volt9000 on 2009-03-10
Hello again everyone... been a long time. :)

I'm trying to install Ubuntu 8.10 Interpid Ibex in VirtualBox (host OS is Windows XP.)
I've tried several times but keep running into the same problem: during the installation while the installer is copying files, it would give me "[Errno 5] Input/output error" and a file, which seems to change every single time I try the installation.

I've searched for this problem, even read the whole thread [here]("http://ubuntuforums.org/showthread.php?t=600126") but it seems like this is mostly related to badly burned  CDs/DVDs. Since I'm using VirtualBox I'm just mounting the ISO directly with the program, so that's not an issue.

I've verified the MD5 sum of the ISO image. I ran the diagnostic check of the image from the main installer menu. I've tried different options in VirtualBox in the hopes that one of them would change something but they didn't.

I have 512MB of RAM allocated for the VM, and the virtual hard drive is 15GB.

My system specs:
Intel Core 2 Duo E6750
2GB of RAM
Windows XP SP3
Host running off 320GB SATA drive, 200+ GB free
Guest installed to secondary 160GB IDE hard drive, 140+ GB free

I had this working once before a while ago, I believe with Dapper Drake.

Does anyone have idea suggestions, short of burning to CD? Alas I only have DVDs on hand at the moment.

---

### Post by Volt9000 on 2009-03-10
Ok, small update:
I tried installing onto a virtual hard drive which is on the same drive as my host C: and I made some progress. But now the installation hangs at 82% "Configuring APT".

So now this makes me wonder if my second drive is no good. :(

But that aside, what can I do about the new problem?

---

### Post by Neo_The_User on 2009-03-10
Try doing the install again with no internet connection. Check the iso as well. The CD iso and the downloaded one. Make sure they match up. Be sure to compare the md5 hashes to the one Ubuntu provides you (most likely on the http directory or ftp directory server that you downloaded it from)

---

### Post by Volt9000 on 2009-03-10
Hi Neo,

Thanks for the info about disabling the Internet connection, I was JUST trying that as you posted, and it worked! :D

As for the image, I've already checked the MD5 checksum and it's ok. Can't burn since I don't have any CDs, only DVDs, and my DVD burning software won't let me burn a CD-sized image to a DVD (go figure.)

But anyways I got it installed... I suspect my secondary drive may be corrupt/damaged after all. :(

---

### Post by Neo_The_User on 2009-03-10
eh you can fix that corrupted hard drive. Check my thread out:

[http://ubuntuforums.org/showthread.php?t=1090641](http://ubuntuforums.org/showthread.php?t=1090641)

That should solve that. Glad the install worked.

---

### Post by Volt9000 on 2009-03-10
That threads seems to be for creating a Linux partition. This is not what I want to do-- I want to format the drive as NTFS and just plunk the virtual hard drive in there, so my guest is running off a different physical drive than my host, to improve performance.

---

### Post by Neo_The_User on 2009-03-10
Actually that thread has a command in there that replaces every block of data on the hard drive back to a 0 therefor wiping everything out.

---

### Post by Volt9000 on 2009-03-10
Ah yes you're right... guess I really should read the thread. :oops:

Well I think my suspicions are confirmed when I tried manually moving the virtual hard drive image to my secondary drive, and Ubuntu wouldn't even boot (GRUB threw Error 25 at me.)

[Edit]
Wait a second I just thought of something-- no way for me to access that drive inside of Ubuntu, since Ubuntu itself is just running inside a virtual machine, so its Universe, as far as it's concerned, is a 15GB virtual hard drive I've created for it.

I'll try using Western Digital's utilities to reformat, hopefully THAT will do the trick.

---

### Post by Neo_The_User on 2009-03-10
yes or the sudo dd blah blah from the livecd

---

### Post by Volt9000 on 2009-03-11
Ok well I tried reformatting with Western Digital's utilities, no dice.
Tried reformatting with Windows, no dice.
In both instances the hard drive is formatted but it still has problems. I know because when I run a chkdsk, it always gets stuck at the last stage (verifying security descriptors complete.)

Booted the Live image and ran that dd command, and I get:

> 
ubuntu@ubuntu:/dev$ sudo dd if=/dev/zero of=/dev/sdb bs=512
dd: writing `/dev/sdb': Input/output error
90481+0 records in
90480+0 records out
46325760 bytes (46 MB) copied, 32.0482 s, 1.4 MB/s


Does this mean the hard drive is completely fried? :(

---

