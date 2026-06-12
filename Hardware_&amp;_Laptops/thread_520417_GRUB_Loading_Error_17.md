---
title: "GRUB Loading Error 17"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by eager2know on 2007-08-08
Hello. I REALLY NEED HELP GUYS...

After one month of perfect operation, my new and shiny Western Digital HDD with 320 GB capcity seems to have stopped working. 

Last night I installed amule and while configuring its options system froze. Totally. Long story short, when I turned the pc off and rebooted I was unable to boot into linux with GRUB loading Error 17. I surfed thru forums and grub pages for half the night and below is a my no-can-do list based on what I tried:

[LIST]
[*]Can't go into grub menu. 
[*]Can't boot with Grub Super Disk. Tried many ways. Won't work.
[*]Can't even boot from Live CD because it starts printing "ata error smth..." messages and simply won't go through with booting. 
[/LIST]

Also tried the following last night: unplugged hdd and booted from Live CD - no problem. Connected HDD back in - errors on screen. SGD grub shell geometry showed only a single partition on the disk, even though a day before there were two. Disk is only 25% full about 80 gigs so it's nowhere near limit.

!!! SOS!!! PLEASE HELP...  I want my data back...
I count on your support...

Thanks.

---

### Post by Circuit99 on 2007-08-08
Hi,

I had a similar problem, I think it was error 17. I couldn't extract any data of system.
The fault occurred due to faulty keyboard on a multi-booting system.

Use this link to explain grub errors

[http://orgs.man.ac.uk/documentation/grub/grub_14.html#SEC106](http://orgs.man.ac.uk/documentation/grub/grub_14.html#SEC106)

You'll find something like this.

Grub Error !7 -
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the file system type cannot be recognized by GRUB.

I didn't find away to extract data from hard drives or repair file system so making the hard drive mountable.

One way is possible forensic tools to extract data something like 

The Sleuth Kit and Autopsy Browser (ext3 support) OR Helix

[http://www.sleuthkit.org/](http://www.sleuthkit.org/)

This link is an article on restore compromised systems

[http://www-128.ibm.com/developerworks/linux/library/l-livecddiag/](http://www-128.ibm.com/developerworks/linux/library/l-livecddiag/)


This link below on types of rescue disk

[http://plug.twuug.org/articles/rescuedisk.html](http://plug.twuug.org/articles/rescuedisk.html)

Also you can find recovery live CD at Distrowatch like systen rescue disk @

[http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

Note there is a good article on Parted Magic - here

[http://distrowatch.com/weekly.php?issue=20070806#feature](http://distrowatch.com/weekly.php?issue=20070806#feature)


Helix is found here

[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)


The problem is what to do, I didn't find a solution. Most recovery software work on mountable hard drives. The current situation is your hard drive is not mountable.

If it was I would use Knoppix Live CD and extract the data.

One way data is to pay a company to recover the data for you. At the end of the day, has the file system become corrupt or is your hard drive faulty. If corrupted hard drive due to a system surge then in theory date could be extracted.

Hard drive manufactures provide software to test hard drive integrity, but I don't know if it will damage existing data on system.
There is software called Testdisk but I don't think it is suitable to repair the hard drive, because I tired it and it didn't work. Maybe someone knows more.


I hope this helps 

Good  Luck

:popcorn:

---

### Post by Circuit99 on 2007-08-09
Have a look here this is a possible solution


[http://ubuntuforums.org/showthread.php?t=478084&highlight=grub](http://ubuntuforums.org/showthread.php?t=478084&highlight=grub)


:popcorn:

---

### Post by eager2know on 2007-08-10
Thanks for the links. But I haven't been able to get into text mode or even boot. I took the drive out of the computer and gave for diagnostics. They said the drive had bad blocks on it and was virtually unuseable. They will try and restore the data on it and then I will need to replace the drive.

That's the story. :(

---

### Post by afzalnaj on 2007-08-12
today i resized an ntfs partition to make a 1gb fat32 partition thru paragon partition manager...did ok...showed in windows...when windows said 'please restart to finish hardware installation; i rebooted and there it was error 17....

i tried to do stufff.i'm a complete newbie...after 3 hours i reinstalled ubuntu and every thing came back...

altho i think just reinstalling the grub package from synaptic wud ve done...can any1 confirm this for future reference?

---

