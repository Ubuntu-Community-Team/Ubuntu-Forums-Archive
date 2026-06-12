---
title: "[SOLVED] Triple Boot Windows/Linux/Linux...can it be done?"
date: 2008-07-12
forum: General Help
---

### Post by solwic on 2008-07-12
Here's my setup:

1.  20GB partition with Windows XP Home
2.  54GB partition with Ubuntu /
3.  3GB partition for swap.

What I want to do is split the 54GB partition into 30GB for Ubuntu and 24GB for openSUSE.  This leads to a couple questions:

1.  I can split the partition that way, right?
2.  I can use the same swap partition for Ubuntu and openSuse, right?
3.  How will this affect my bootloader?  I use GRUB to boot both Ubuntu and Windows.
4.  I have a 160GB USB HDD, and my BIOS will boot from a USB device.  Would it be better to install openSUSE to that drive?
5.  If I did install openSUSE to that drive, how would I configure GRUB to load all three OSes?  
6.  Would using a USB HDD slow down the openSUSE installation/operation at all?  (I'm assuming it would, but thought I should ask anyway).

A lot of questions, I know, but I really would like to have openSUSE and Ubuntu both, and I'm still not quite sure about getting rid of Windows.

So can I have my cake and eat it, too?  Thanks in advance for the help!

---

### Post by SkonesMickLoud on 2008-07-12
> **jrock612 said:**
> Here's my setup:

1.  20GB partition with Windows XP Home
2.  54GB partition with Ubuntu /
3.  3GB partition for swap.

What I want to do is split the 54GB partition into 30GB for Ubuntu and 24GB for openSUSE.  This leads to a couple questions:

1.  I can split the partition that way, right?
2.  I can use the same swap partition for Ubuntu and openSuse, right?
3.  How will this affect my bootloader?  I use GRUB to boot both Ubuntu and Windows.
4.  I have a 160GB USB HDD, and my BIOS will boot from a USB device.  Would it be better to install openSUSE to that drive?
5.  If I did install openSUSE to that drive, how would I configure GRUB to load all three OSes?
6.  Would using a USB HDD slow down the openSUSE installation/operation at all?  (I'm assuming it would, but thought I should ask anyway).

A lot of questions, I know, but I really would like to have openSUSE and Ubuntu both, and I'm still not quite sure about getting rid of Windows.

1. Yes.
2. Yes.
3. You can keep GRUB, or you can let openSUSE install it's own, which is a prettier version.
4. Installing/booting to USB will cause it to be slower.  How much?  I don't know.
5. GRUB should find, and automatically create entries for you.
6. IIRC installing openSUSE 10.3G took about an hour on my relatively well spec'd notebook.  I don't know if oS 11 fixed the install time, but it does take a while.  Again, I don't know how much slower it will be.

> **jrock612 said:**
> So can I have my cake and eat it, too?

Pretty much!

---

### Post by solwic on 2008-07-12
> **SkonesMickLoud said:**
> 1. Yes.
2. Yes.
3. You can keep GRUB, or you can let openSUSE install it's own, which is a prettier version.
4. Installing/booting to USB will cause it to be slower.  How much?  I don't know.
5. GRUB should find, and automatically create entries for you.
6. IIRC installing openSUSE 10.3G took about an hour on my relatively well spec'd notebook.  I don't know if oS 11 fixed the install time, but it does take a while.  Again, I don't know how much slower it will be.


Well you can't much more straight-forward than that!  Thank you for answering every question I had.  I kind of guessed that GRUB would do the dirty work automatically, since it did with Windows, but it never hurts to be sure.  

Thanks again for the help.  If I could thank you more than once for this post, I would.  This community needs more people like you in it, sir.  :)

---

### Post by SkonesMickLoud on 2008-07-12
> **jrock612 said:**
> Well you can't much more straight-forward than that!  Thank you for answering every question I had.  I kind of guessed that GRUB would do the dirty work automatically, since it did with Windows, but it never hurts to be sure.  

Thanks again for the help.  If I could thank you more than once for this post, I would.  This community needs more people like you in it, sir.  :)

No problem!  Should GRUB fail to do it's thing automatically, it's a very simple fix.  Just bump this thread if it doesn't work.

---

### Post by boblemur on 2008-07-12
for my few cents worth, you should prob boot into Ubuntu live and change the partitions from their.. especially if you are experimenting with a new os, you dont wana be hesitant and unsure of what you are doing... if you do the partitioning ( the scary dangerous stuff) in the Ubuntu environment ( that ur prob more usto) may save you from accidentally destroying something... 

and then when u go to install the new os you already have ur new partitions ready and u dont need to format anything... just point it to the space it can use

---

### Post by solwic on 2008-07-12
> **boblemur said:**
> for my few cents worth, you should prob boot into Ubuntu live and change the partitions from their.. especially if you are experimenting with a new os, you dont wana be hesitant and unsure of what you are doing... if you do the partitioning ( the scary dangerous stuff) in the Ubuntu environment ( that ur prob more usto) may save you from accidentally destroying something... 

and then when u go to install the new os you already have ur new partitions ready and u dont need to format anything... just point it to the space it can use

I took a look at the partitions using the SUSE installer...and yeah, I much prefer the Ubuntu way.  

I thought, though, that using the LiveCD had issues when partitioning?  Something about the LiveCD trying to mount the partitions it was modifying or something?  I've tried the gparted livecd, but it doesn't like my ATI video card.  

Since I'm somewhat of a partition noob, I wonder if I could wipe the HDD completely, install SUSE on the whole drive, then install Ubuntu and use its partition manager to resize, splitting the HDD half for SUSE, half for Ubuntu.  

Anybody see anything wrong with that idea?  I just want to make sure I know exactly what I'm doing before I start destroying partitions.  

(As a side note, I know I wanted to keep the Windows partition earlier...but to hell with it.  I don't play video games, and I can emulate Windows XP with Virtual Box, can't I?)

Thanks!

---

### Post by SkonesMickLoud on 2008-07-12
> **jrock612 said:**
> Since I'm somewhat of a partition noob, I wonder if I could wipe the HDD completely, install SUSE on the whole drive, then install Ubuntu and use its partition manager to resize, splitting the HDD half for SUSE, half for Ubuntu.  

Anybody see anything wrong with that idea?  I just want to make sure I know exactly what I'm doing before I start destroying partitions. 

You COULD do that, but why?

If you're thinking of wiping the disk anyway, why not learn partitioning by doing it?  You'll find that it seems daunting at first, but it's really quite simple.  You just have to pay attention.  Especially if you're not too worried about losing any data.  Make sure you back up what you want to keep though.  Once data is formatted over, it's very difficult to get back.

The GParted that comes on the Ubuntu LiveCD shouldn't mount any partition on it's own.  However, if it does, it's simply a matter of right-clicking on the partition and clicking "unmount".

In the end though, you should do what you're comfortable with.  Keep those questions coming if you have them.  No such thing as a stupid question.

> **jrock612 said:**
> (As a side note, I know I wanted to keep the Windows partition earlier...but to hell with it.  I don't play video games, and I can emulate Windows XP with Virtual Box, can't I?)

As long as your system can handle it, you shouldn't have too many problems with doing that.

---

### Post by solwic on 2008-07-12
> **SkonesMickLoud said:**
> You COULD do that, but why?

If you're thinking of wiping the disk anyway, why not learn partitioning by doing it?  You'll find that it seems daunting at first, but it's really quite simple.  You just have to pay attention.  Especially if you're not too worried about losing any data.  Make sure you back up what you want to keep though.  Once data is formatted over, it's very difficult to get back.

The GParted that comes on the Ubuntu LiveCD shouldn't mount any partition on it's own.  However, if it does, it's simply a matter of right-clicking on the partition and clicking "unmount".

In the end though, you should do what you're comfortable with.  Keep those questions coming if you have them.  No such thing as a stupid question.



As long as your system can handle it, you shouldn't have too many problems with doing that.

I never thought of using the opportunity to learn partitioning.  That's actually a very good idea.  :)

I've already got all the stuff backed up, so I think I'll fire up the Ubuntu LiveCD and see what I can figure out.  Worst case scenario is a screw up the partitions and have to start over from scratch, right?  

No possibility of physically damaging the drive by partitioning, is there?  

Thanks for all the help!  :)

---

### Post by SkonesMickLoud on 2008-07-12
> **jrock612 said:**
> I never thought of using the opportunity to learn partitioning.  That's actually a very good idea.  :)

Best way to learn.

> **jrock612 said:**
> Worst case scenario is a screw up the partitions and have to start over from scratch, right?

Yep.

> **jrock612 said:**
> No possibility of physically damaging the drive by partitioning, is there?

Nope.

---

### Post by solwic on 2008-07-12
Well I just used the Ubuntu LiveCD to split my Ubuntu partition in half, with no problems at all.  Just booted into Ubuntu to make sure it still loaded OK...now I'm off to install SUSE on the new partition. 

Thanks again for all the help, and I'll post back and let ya know how it turned out.  :))

---

### Post by absolutezero1287 on 2008-07-12
Dude, chill. A triple boot is simple. Make space for the next OS. Install OS. Update the menu.lst file and that's it.

Try booting 100 OSs!
[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

---

### Post by solwic on 2008-07-12
Well other than a confusing partition menu in openSUSE, things went perfectly.  All OSes were picked up by GRUB, and all boot up just fine.  The only thing different is when I select Ubuntu or WindowsXP from GRUB, I get a few seconds of black screen where my monitor puts up a little box that says "Input Not Supported".  No more than 5 seconds, and then the screen kicks on and all is well.  

Nothing to complain about though, because the HDD is still working when this happens, so it's not slowing down my boot any.

Thanks again, especially to SkonesMickLoud for answering all my noob questions.  :)

Cheers!

---

