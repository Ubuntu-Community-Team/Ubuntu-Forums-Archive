---
title: "Did I ruin my Windows side?"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by johnphilipjohnson on 2009-02-17
I was messing around with the new Kubuntu last night, running it off a CD, and for speed I thought I'd put it on the hard drive.  I accepted the defaults, wasn't paying too much attention. 

I THOUGHT it said it would install Kubunu in available space. 

I ASSUMED it would run side by side, and when I rebooted I would have the choice to run Linux or Windows.

BUT NO WINDOWS OPTION!  Just boots Kubuntu.

75 gig, a lot of stuff not backed up...

Am I ruined with this?  I installed it off the "install" icon off the Kubuntu desk top.

I mean, even DOS 25 years ago would warn you before you formatted a drive!

Is there anything i can do to recover some of the data?  Is Windows actually gone?

Thank you thank you thank you thank you....

---

### Post by avtolle on 2009-02-17
While I don't use Kubuntu, I presume it, as well as does Ubuntu, warn you (but not with flashing lights, sounds, etc) that formatting the drive/partition will cause loss of the data on the drive/partition.

First, though, do this (and nothing else) from your Kubuntu install. From Konsole (as I recall) do```
fdisk -l
```and post the results.

---

### Post by johnphilipjohnson on 2009-02-17
thanks.  I'll try it when I get home.  I'm at work now.  Although I'm not exactly sure where I'd write that phrase, as the Kubuntu I'm using has a graphical interface (like evil tinker toys) instead of a command prompt.

Thanks!

---

### Post by avtolle on 2009-02-17
You need to do it from konsole; in Ubuntu, it is called Terminal, and gives you a command line. I think it (konsole) is found under menu>applications, but as I don't use Kubuntu, not sure and am going from memory of other posts. Good luck.

---

### Post by johnphilipjohnson on 2009-02-17
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9539    76621986   83  Linux
/dev/sda2            9540        9726     1502077+   5  Extended
/dev/sda5            9540        9726     1502046   82  Linux swap / Solaris

---

### Post by johnphilipjohnson on 2009-02-17
So, that looks kind of bad to me, is it?  

Do you think one of those hard data recovery companies could help?

---

### Post by Mark Phelps on 2009-02-17
Yep ... it looks like you completely overwrote your Windows installation with Ubuntu. And, while it DOES provide a warning, from the number of complaints here, it's obviously not strong enough to make it apparent that the entire Windows install will be destroyed.

And yep, you can spend a FORTUNE sending your hard drive to a disk recovery company ...

But before you do that, do you have a second machine you can hook the hard drive to?  If so, what OS is that machine running?  

There are cheaper recovery options that will work nearly as well that will recover removed files and deleted partitions.

I've even been told that Testdisk can completely restore your Windows partition(s), but I haven't used it myself.

---

### Post by avtolle on 2009-02-17
You have definitely overwritten your Windows installation; as to your query, don't know. Hopefully, someone with better knowledge than I can give you some guidance here.

---

### Post by cariboo on 2009-02-17
You could give [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") a try. You can install it from the repositories, but I would suggest going [here]("http://ubuntu-rescue-remix.org/") and downloading the Ubuntu-rescue-remix and using it. You will needed another hard drive to write the rescued data to.

Jim

---

### Post by Mark Phelps on 2009-02-18
Just so you know ... the more you use your current drive, especially to install ANYTHING, the less the chance you will be able to recover files, let alone the partition.

You will need to run the recovery on another machine, with the affected hard drive hooked up.  You will not be able to recover files to the same drive.

---

### Post by dstew on 2009-02-18
Testdisk is part of the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), I believe. You could boot this Live CD, and run testdisk from there.

---

### Post by johnphilipjohnson on 2009-02-18
Thank you all for your words.

We have a couple of other machines which run Windows XP.  We can clear off enough space on the drives, but I'm probably going to just buy a new drive for it, so it could be Linux if that would be better for recovering my other drive.

Should we try the Ubuntu-rescue-remix method first, before trying Testdisk? 

We're open to whatever we should do.

Thank you again for your help with this.  Much appreciated.

---

