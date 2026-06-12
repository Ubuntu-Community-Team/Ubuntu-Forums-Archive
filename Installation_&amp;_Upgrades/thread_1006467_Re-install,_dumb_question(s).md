---
title: "Re-install, dumb question(s)"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by revjim on 2008-12-09
Hi people,

I have been happily dual-booting XP and ubuntu for some time.
Then I got a bit carried away with following scripts/how-to's that I didn't fully understand. The result is a broken install, it will boot but a lot of stuff no longer works. I have backed up my data and want to do a clean re-install.

If I delete the existing linux partitions using something like partitionmagic under XP, can I then install ubuntu from the CD and it will re-write grub and include the XP installation?

I looked at installing 'over the top' of the existing ubuntu install, but it got confusing at the disk partition section, because ubuntu was already using the 'spare' disk space.

The thing I'n worried about is if I delete the linux partitions, will grub still function and allow me to boot XP? or is there a problem where it fails to boot at all?

Thanks,
RevJim

---

### Post by oldos2er on 2008-12-09
Grub relies on the file /boot/grub/menu.lst to tell it which partitions are bootable, so if you delete your Ubuntu partition, you delete this file and grub will no longer function.

 Can you please post output of the command "sudo fdisk -l"?

---

### Post by Kevbert on 2008-12-09
Easiest way would be to delete the existing linux partition as part of a manual install and then create a new one using the empty space. Format ext3 and mount point /  You can leave the swap partition untouched.

---

### Post by revjim on 2008-12-09
Thanks for the prompt replies!

I figured deleting the partitions would remove the grub boot file.

And I will re-look at the manual install, however iirc it offered only the options to completely remove all partitions or shrink the existing ext3 partition and install another instance of ubuntu.

I may have to remove grub from the mbr, if I can find my XP cd.

RevJim

---

### Post by revjim on 2008-12-10
Well, today I looked again at the partition thing during install, and found it recognised the exisiting partitions. Cool!
So I tried an install, manual partition scheme, formatted the existing partitions and it set to installing, returned a few minutes later with an error, tried again and same error. Looks like the CD is scratched or damaged. Tried to reboot from the hard drive and I get grub error 15... which is something to do with missing grub file on a partition that was formatted.

So now I have an unbootable system and a damaged CD.
I do however have blank CD's but if I try to open the CD burning software from the live CD (yes it boots from the 'damaged' CD fine) it won't let me due to the CD being in use I suppose.

HELP!!

Rev

---

### Post by logos34 on 2008-12-10
> **revjim said:**
> So now I have an unbootable system and a damaged CD.
I do however have blank CD's but if I try to open the CD burning software from the live CD (yes it boots from the 'damaged' CD fine) it won't let me due to the CD being in use I suppose.

Did you check the md5sum and do an integrity check?

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Assuming that's the problem, the easiest solution would be to find some other machine on which to burn a new cd.  Otherwise you could download [Unetbootin]("http://unetbootin.sourceforge.net/") installer to your windows partition and try reinstalling that way. (you'll have to use the xp cd to restore the windows bootloader)

good luck

---

### Post by louieb on 2008-12-10
> **revjim said:**
> ...tried an install, manual partition scheme, formatted the existing partitions and it set to installing, returned a few minutes later with an error, tried again and same error. Looks like the CD is scratched or damaged. Tried to reboot from the hard drive and I get grub error 15... Rev

When I have to,  thats the way I usually reinstall. Hope you have a 2nd computer you can make a good install disk.  Or if you have a  [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") handy you could get to boot XP so you could burn a new install disk using XP.

---

### Post by revjim on 2008-12-10
will try re-downloading latest live cd and burn it on the flakey spare pc...


/me crosses fingers

---

### Post by revjim on 2008-12-10
downloaded a fresh iso, then had to download xpburner and swap out a dvd player for a cd writer, and finally burned a good copy of live CD.

Finally installed and all works fine :)

oh apart from the OS forgets its network settings each reboot... google-fu is on the case

Rev

PS how do i edit the thread title to [SOLVED] ?

---

### Post by logos34 on 2008-12-10
> **revjim said:**
> 
PS how do i edit the thread title to [SOLVED] ?

>Thread tools>mark as solved

glad you got it sorted.  enjoy

---

