---
title: "Moving Ubuntu installation to another HDD"
date: 2008-07-16
forum: General Help
---

### Post by Metallinut on 2008-07-16
I'm wondering if there's anyone out there who can give me some tips/pointers for what I want to do here...  First some background.

I currently have a Hardy server with 3 HDDs in it:  
[LIST=1]
[*]SATA (/dev/sda) - / /home & swap partition
[*]IDE (/dev/sdb) - data storage
[*]IDE (/dev/sdc) - data storage
[/LIST]

I just got a [_[COLOR="Blue"]Drobo[/COLOR]_]("http://www.drobo.com"), in which I'll be putting 2 500 GB drives.  The Drobo takes SATA I or SATA II drives, but not IDE.  

I plan on moving the data from the 2 IDE drives onto the Drobo. 

Once that's done, I figure I could move my / /home and swap partitions onto one of the now empty IDE drives, and then I could add the 140GB SATA drive to the Drobo, giving me a bit more disk space.

So how would one accomplish this?  Is it even possible?  I figure I should be able to do partition /dev/sdb to mimic /dev/sda, and then do a straight up copy:

/dev/sda1 -> /dev/sdb1
/dev/sda2 -> /dev/sdb2
and just make /dev/sdb3 a swap partition...

But what will I need to do to accomplish this?  Boot records...the device names may change once drives are uninstalled from the chassis, etc.

Thanks!

---

### Post by bodhi.zazen on 2008-07-16
You do not need to move swap, just make a new one.

To move home : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

To move / (root partition) use a live CD and you can use gparted to copy and paste a partition.

Now with all that moving you will need to update fstab and grub.

These links should help :

[How to run bleeding edge - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316237") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Metallinut on 2008-07-16
I'll need to update the MBR on the replacement drive too, right?  So that the BIOS will view the new drive as bootable?  I think I can use fdisk for that...

---

### Post by bodhi.zazen on 2008-07-16
Yes, install grub to the MBR and mark at least one partition as boot.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

fdisk will do just fine :)

---

