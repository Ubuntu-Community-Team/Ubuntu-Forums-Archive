---
title: "Install Bamboo Fun Pen and Touch"
date: 2010-12-09
forum: Hardware
---

### Post by mdouble on 2010-12-09
Problem: the tablet is not working under Ubuntu

I'm looking for help installing and configuring my Bamboo Fun Pen and Touch / Model CTH661.  My Distro is Ubuntu 10.04, which is installed on a dual boot system with Windows XP Pro. 10.04 was originally installed using the Windows Wubi installer, so is not on a fully separated partition or drive.    

Before offering any help, please be aware that I have already read a huge number of threads in the forum and tried many of the solutions offered to others. I have also read through and tried the solutions offered on the Linux Wacom sites, also without success.

The problem for me is simply that I am not familiar enough with Linux or use of the terminal to properly understand or execute the routines.  I can follow the directions, however I often hit a snag in the routine which leads me to a dead end.  In other words, it is my own lack of experience and understanding that is likely at fault.

I need a simple, step by step routine and some hand holding from someone with experience and the ability to explain what I'm doing and why. 

Footnote:  I attempted to upgrade to Ubuntu 10.10 following the typical upgrade routine for 10.04.  Unfortunately this resulted in the loss of GRUB, which I could not recover.  Eventually I reinstalled 10.04 from the Windows Wubi installer.  

I also have a live CD for 10.10 but have been fearful of using it to install.  I have recently read that, to install 10.10 one should have a fully separate partition.  Some of these routines advise that for a proper dual boot set up Windows should be entirely removed then reinstalled on it's own partition.  Then Ubuntu.  For me, this is not a viable option at this time.  

My preference is to install the tablet using my existing 10.04 / Windows XP dual boot setup.

Any help offered to resolve this issue will be gratefully accepted.

---

### Post by lukeiamyourfather on 2010-12-09
Try running this in a terminal.

```
sudo apt-get install xserver-xorg-input-wacom
```

That's the Wacom tablet driver in the Ubuntu repositories. You might have to restart before it works.

---

### Post by Favux on 2010-12-09
Hi mdouble,

The problem is your tablet is not in the default wacom.ko (the usb kernel driver) that comes with Lucid.  You need to compile a newer wacom.ko and copy it into place.  See I. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

I used WUBI a little bit at first.  Don't remember much about it.

What you want to do is to tell Windows to shrink itself.  First you do a disk check and defrag.  Once it's shrunk itself to the size you request you'll have an empty partition.  When you use the Ubuntu live CD it will install itself into the empty partition.  There is no need to remove Windows.  You do want a backup before doing this of course.

---

### Post by mdouble on 2010-12-10
Thanks for your reply I will try the command suggested and see what happens.

---

### Post by mdouble on 2010-12-10
Thanks very much for your reply, I appreciate your suggestion.  I was confused by the fact that, according to my understanding, when installing using Wubi, Lucid is actually created as a kind of virtual partition on the actual Windows partition.  Is this understanding correct?

---

### Post by Favux on 2010-12-10
> when installing using Wubi, Lucid is actually created as a kind of virtual partition on the actual Windows partition. Is this understanding correct? 
Sure.  If you look around you'll see the Ubuntu WUBI partition is actually a file in the Windows filesystem.  So you could shrink Windows while keeping WUBI.  And install a "real" instance of Ubuntu on the empty part of the hard disk.

Probably not a good idea though in practice because you don't want to limit yourself too much on how much it will shrink.  That's why you want to error check and defrag first.  There's some arcana if it balks at giving you more than a little partition.  I think that's due to the recovery points and you may need to turn that off if you don't get as much space as you want.  There's Windows HOW TO's on shrinking that will explain it.  Ubuntu is happy with 10 to 25 Gigabytes, depending on how much stuff you want to install.

---

### Post by mdouble on 2010-12-10
> **Favux said:**
> Hi mdouble,

The problem is your tablet is not in the default wacom.ko (the usb kernel driver) that comes with Lucid.  You need to compile a newer wacom.ko and copy it into place.  See I. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

I used WUBI a little bit at first.  Don't remember much about it.

What you want to do is to tell Windows to shrink itself.  First you do a disk check and defrag.  Once it's shrunk itself to the size you request you'll have an empty partition.  When you use the Ubuntu live CD it will install itself into the empty partition.  There is no need to remove Windows.  You do want a backup before doing this of course.
Hi Favux and thanks very much for your help.  I stumbled through the instructions on Bamboo P&T HOW TO.  I am pleased to report that the tablet is now working.  Here's another novice question.  After the install I now have several new files on my desktop. All of these are related to the process of installing the software.  Can I now remove these files from the desktop or are they required?

Thanks again

---

### Post by Favux on 2010-12-10
Hi mdouble,

Great!  Nice job.  :)

Well you haven't told me what they are.

Are they linuxwacom-0.8.8-10.tar.bz2 and linuxwacom-0.8.8-10?  The tar file is the compressed version of linuxwacom-0.8.8-10 that you downloaded with the wget command.  You uncompressed it into linuxwacom-0.8.8-10 with the tar xjvf command.  You can do the same thing to the tar by right clicking on it and choosing extract here.

If you get offered and accept a kernel update you'll need linuxwacom-0.8.8-10 because you will have to recompile the wacom.ko.  The tablet will seem to break after the kernel is updated.  That's because the new kernel will have the old default non-working wacom.ko and you'll have to replace it again.  So unless there is a new linuxwacom version by then keeping it saves you from re-downloading it.

---

