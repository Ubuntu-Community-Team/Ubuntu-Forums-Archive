---
title: "lost partition"
date: 2010-02-05
forum: Hardware
---

### Post by Mr_Wonderful on 2010-02-05
Hello everybody,

I removed Ubuntu a few months ago and reinstalled it on my laptop (due to some issues with my ATI graphics card) I'm looking to do the same again (due to network issues with 9.10).  However the last time I did this I simple deleted the partition of my hard drive containing Ubuntu (using PMagic) and run the installation again.  This worked fine ALTHOUGH I have lost the 20 gig or so which was the original Ubuntu partition; it is kind of just dead space on my hard drive now.

my question is, how do I free that space back up to us it for either a new Ubuntu installation or more hard drive space for XP and how do I avoid making the same mistake again ?

cheers in advance

Nick

---

### Post by brett- on 2010-02-05
Manipulating partitions is tricky.  Ubuntu will not allow manipulating an active partition.  You could boot with a live CD and use gparted to format the dead space and combine it with the Ubuntu partition.  Be sure that both are either ext4 or ext3.

That said, and your frequent reinstalls for whatever reason, I would advise using two partitions for Ubuntu; one for root, swap and boot and the other for home.  If Ubuntu has to be reinstalled then home is not affected.

If you run gparted, include a screen shot of of the partitions.

---

### Post by lidex on 2010-02-05
I would download and burn a copy of the Gparted LiveCD. You can boot into that and accomplish your task in a safe manner:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

