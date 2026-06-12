---
title: "Unetbootin can't find my harddrive.... :o("
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Chris-Chicken on 2009-02-02
Hello peeps,

I've been given an old Toshiba Satellite 1410 laptop, which has only 256Mb of ram, a 20Gb hd, and a dead CD drive. I want to put Xubuntu on there for a friend. Even with the latest bios, it doesn't boot from USB.

So, I'm trying to use unetbootin....which seems to work fine, until the fourth part of the install, when the program starts a partitioner. There are no drives in the window, and all the buttons are greyed out. If I try to continue, an error message appears, saying that there is no location for the root directory selected, and instructing me to use the partitioner to do so..... which I can't.

I've tried setting up a separate logical partition (fat32) which both Windows and Linux can see, but to no avail. If I attempt the install with a USB drive connected, the software detects that, and offers me a "guided partition" option.... which isn't much use.

So - could it be the hard disk?

Does anyone have any ideas on how else I can install?

Thanks for anything!

---

### Post by boof1988 on 2009-02-02
I had a similar problem maybe.

Are you trying to install from an "install" partition you created on the HDD using Unetbotin?  Are you trying to install Ubuntu 8.10?  When you get to the partitioning step (in the Ubuntu Installer), the HDD on which the "install" partition is located will not show up?

It may not be very eloquent... But my solution was to use the ubuntu-8.04.(1,2)-desktop iso.  Not sure exactly why, but it (for my systems) seems to work just fine when installing Ubuntu/Xubuntu 8.04.

---

### Post by Chris-Chicken on 2009-02-02
I'm trying to install using Unetbootin, through the existing installation of XP.

First installed Unetbootin on the single drive (it wasn't partitioned, as it's only 20Gb) that didn't work, so I  partitioned it. On both occasions, the partition section of the installer doesn't display anything at all, no drives showed up. When I tried with a USB stick connected, that did show.... but I don't want to install there...

The iso was originally on the USB stick, but all the files would have been copied to the HDD...right?

Interestingly, the logical partition I made isn't detected by the software unless I check the "show all drives" box.

I am trying Xubuntu 8.10. I can try 8.04... but surely...this is a unetbootin issue?

---

### Post by maybeway36 on 2009-02-02
I suppose you could try the Ubuntu netboot installer instead of the graphical one. I think UNetbootin has a way to use this installer (it's only 9MB and downloads everytihng fron the Internet).

---

### Post by boof1988 on 2009-02-02
> **Chris-Chicken said:**
> I'm trying to install using Unetbootin, through the existing installation of XP.

My understanding of what Unetbooting does is that it copies the the contents of the iso file (with appropriate changes) to a partition and then makes it bootable.  I'm not trying to correct you.  I'm hoping someone else can chime-in and clarify this detail.

> **Chris-Chicken said:**
> First installed Unetbootin on the single drive (it wasn't partitioned, as it's only 20Gb) that didn't work, so I  partitioned it. On both occasions, the partition section of the installer doesn't display anything at all, no drives showed up. When I tried with a USB stick connected, that did show.... but I don't want to install there...

Yes... I think there is some bug (or something) that prevents the installer from using any of the partitions of the drive which includes the installer partitiom.

> **Chris-Chicken said:**
> The iso was originally on the USB stick, but all the files would have been copied to the HDD...right?

I believe this is what happens.

> **Chris-Chicken said:**
> Interestingly, the logical partition I made isn't detected by the software unless I check the "show all drives" box.

Yes... I think Unetbootin uses this method so that it's a little more difficult to mess up the internal drive.  If the wrong partition is selected, really bad things can happen (I have messed up in this way).

> **Chris-Chicken said:**
> I am trying Xubuntu 8.10. I can try 8.04... but surely...this is a unetbootin issue?

I agree that there is an issue.  I'm just not sure who can fix it.  Also be aware (in the times I have used Unetbootin to make a HDD installer partition) that some of the menu options may not work.  The "Try without installing", "Install" and "check integrity" options are the only ones that have worked for me.

---

### Post by boof1988 on 2009-02-02
> **maybeway36 said:**
> I suppose you could try the Ubuntu netboot installer instead of the graphical one. I think UNetbootin has a way to use this installer (it's only 9MB and downloads everytihng fron the Internet).

Thanks for mentioning this... Will check it out.

---

### Post by Chris-Chicken on 2009-02-02
Yep, I tried pointing Unetbootin at the net based installer (Xubuntu 8.04) and it went off without a hitch....

Perhaps the graphical installer and Toshiba have an issue? 

I don't know, but I'm very impressed with the net based installer. Making toast is more difficult.

Thanks for the help :o)

---

### Post by boof1988 on 2009-02-02
> **Chris-Chicken said:**
> Yep, I tried pointing Unetbootin at the net based installer (Xubuntu 8.04) and it went off without a hitch....

Will have to check this out and try it.  I'm glad maybeway36 mentioned it.

> **Chris-Chicken said:**
> Perhaps the graphical installer and Toshiba have an issue?

I've had the problem on other hardware.  So it may just be some software issue.  I'm not too good at reporting bugs (can't remember and pass on the important details) or I'd pass the info on.

> **Chris-Chicken said:**
> I don't know, but I'm very impressed with the net based installer. Making toast is more difficult.

Glad it worked well/easy for you... That's why I'll have to try it out.

---

### Post by Rofko on 2009-03-09
Ha. My problem is identical, except that I also can't use the network install! I have tried so many hacks in the past two days... I have just come across the reply about trying 8.04... i'll try it now and post the results...

---

