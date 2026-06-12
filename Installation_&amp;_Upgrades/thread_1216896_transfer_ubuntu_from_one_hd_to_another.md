---
title: "transfer ubuntu from one hd to another"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by allenbina on 2009-07-18
I was playing around with partitions and to be safe i cloned my drive beforehand.  Somewhere in the new partitioning, I messed up but only after getting exactly what I wanted.  The only thing missing is that ubuntu isnt reading from grub.  Is there a way to reinstall ubuntu in the partition I want it to be in the new drive and transfer all of my data from the old partition to the new one?

Is there some sort of settings transfer wizard or time machine thing I can do to transfer all of my old data to my new drive?

---

### Post by jerrrys on 2009-07-19
you have to make sure that whatever backup software your using will copy MBR. thats one reason i use Clonezilla...

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Wickd on 2009-07-19
I will agree with Jerrys here.

Download the Live CD iso, write to disc, boot from disc and off ya go.

You can also dd (disk dump) to do this for you. Used this tutorial to do this a while back

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

Cheers :)

---

### Post by allenbina on 2009-07-20
brilliant! thats what I used to back up my whole drive in the first place.  obviously I'll need to change grub to reflect the new position of the partitions, but should I have a problem just moving the partition over and correcting that?

---

### Post by allenbina on 2009-07-21
I'm still having the same problem.  When I tried to move the partition from the clonezilla live cd, it didn't read the disk properly.  I booted from the live ubuntu cd and gparted says the entire disk is "unallocated" (see [http://ubuntuforums.org/showthread.php?t=1216430](http://ubuntuforums.org/showthread.php?t=1216430)).  Do I just start from scratch?  I can't even count the number of small edits and such that I had to use to make it work right.  Is there any sort of file and settings transfer app that I can use?

thanks for the halp!

---

