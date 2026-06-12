---
title: "Install on formatted/unformatted drive fails"
date: 2005-11-05
forum: General Help
---

### Post by sappman2 on 2005-11-05
Pent III 850 MHZ PC. Removed Windows ME.
Install disk fails to even start the install program. While "setting up the file system", it either hangs up repeating "Segmentation Fault" or "Kernel Panic, attemtpting to kill-something". I've tried deleting all partitions, I've made sure my Bios operating system and file system is set to "Other", I've tried partitioning again then formatting the hard drive with a DOS format tool, then re-deleting the partition, re-installing partition, etc. 

I did get it to install almost-successfully once, but I didn't have sufficient privileges to edit ANYTHING, apparently because the network connection was disconected at the time of installation. So, I attempted to correct this in Rescue mode, no effect. I couldn't edit the Host file or network settings. So, I tried to run an install with the network connected, and now I'm back to the original problem of the install CD not loading. I suspect it has something to do with the hard-disk format, but I'm at a loss as to what to do. I REALLY want to convert to Linux, but at this point I'm very frustrated. Somebody please be kind enough to help.  Thanks!

---

### Post by mustang on 2005-11-05
Ok so if I'm not mistaken, you're back at square one right? You got your ubuntu install cd and an empty hard drive and you want to install it but it somehow fails?

When you initially boot from the install cd and get to that first screen, I believe there's an option somewhere to check the integrity of the disc from possible CRC errors when you originally downloaded the iso file. Try running that and see if it fails or not. If it does, you know it's the cd's problem. 

I can't exactly explain how it managed to work out once for you. Is the cd stratched or something?

---

### Post by sappman2 on 2005-11-07
Yep... I can't figure that out, either. I've tried new downloads & new CD burns (On CD-R's, not CD-RW's) I've tried KUBUNTU (In case it might somehow have been GNOME? causing problems). I've tried both CD drives on this PC. This HD is completely empty, so there shouldn't be any problemd. I keep coming back to it being a format issue, with UBUNTU installer not liking the format of the HD somehow. (even though there are no partitions present, not even a primary DOS partition.)

Thanks for replying... it's a big forum out here.
-Chris

---

### Post by gt24 on 2005-11-07
There are a few options depending on how long you want to wait and what your specific problem is.

First off, you can scan your CDs for corruption.  I don't know of a specific utility that does this (I use Nero's scanning disk utility), but you can try out the one below...
[http://www.elpros.si/CDCheck/news.php](http://www.elpros.si/CDCheck/news.php)

Next, you can try a network install.  This is of course best if your computer has a detectable network card.  This method isn't exactly official yet, but it might just work for you.
[http://www.ubuntuforums.org/showthread.php?t=75372](http://www.ubuntuforums.org/showthread.php?t=75372)

You can also order CDs to be shipped to you free of charge, although this could take a while.  The official wait time is 4-6 weeks, although it could come sooner than that.  The first link is an FAQ that you can read while the next link is where you order the CDs.
[http://www.ubuntulinux.org/support/documentation/faq/shipit/](http://www.ubuntulinux.org/support/documentation/faq/shipit/)
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

You can ask a friend, one of whom has a flawless CD burner or alike, to burn a CD for you.  Sometimes, computers act pretty darn flakey for no apparent reason at all and by having your disk burned by somebody else you can begin to eliminate CD burning issues as one of the problems.

Finally, choosing a distro that is right for you...  It was mentioned somewhere on these forums that one key in choosing a distro that is right for you is to measure the amount of hassle that the distro causes you.  For instance, if the distro fails to detect 2 or more pieces of your hardware, it might be time to look elsewhere.  For instance, a lot of people running other distros say that they don't run Ubuntu because they could never get it to install.  One popular distro review doesn't list Ubuntu because they could never get it to install.  So, if you are in the same boat and can never get Ubuntu to install, this could be something to look into.

Random question to anybody in the forum...  Let's say that another Linux boot disk was used and was used to format the hard drive as needed (like with a Knoppix CD or alike).  Is there a way that the person could wget a gzipped version of a minimal Ubuntu network install and plop that in?  They would probibally have to set up Grub, but this method might work too.... hmmm...

---

### Post by sappman2 on 2005-11-08
I found the likely problem on my causing install to fail. I talked to one of my work-mates, who is far more computer-savvy than I. He suggested that I could be having a problem with my RAM. I insisted that the box ran fine on Windows, to which he replied that Windows, which "leaks" memory anyway, has  built-in redundancies that cover over RAM problems. Linux, however, does not.

BINGO! I ran "MEMTEST" from the install CD and only about 12% (Average) of my "brand-new" 512Mb RAM passed, even though my BIOS boot RAM test passed it w/no problems. I sincerely appreciate the UBUNTU community for their attempts at helping. I hope that, as I grow in knowledge, I'll be able to give back and help others and promote the benefits of Linux and Ubuntu. Now... Any ideas on a place to find decent, cheap RAM for a 6 year old Pentium III?      Thanks............... -Chris

---

