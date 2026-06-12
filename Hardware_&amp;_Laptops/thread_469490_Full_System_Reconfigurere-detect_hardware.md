---
title: "Full System Reconfigure/re-detect hardware"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by mrant on 2007-06-09
I have a somewhat complicated problem and I'm not sure how to apporach it. I had Ubuntu 7.04 up and running fine on an old laptop (PIII 500MHz 128MB RAM...) and recently swapped the hard drive with another old laptop. The laptop that inherited the drive with Ubuntu on it has no floppy drive, no ethernet port, no cd rom drive, can't boot from USB. So there is essentially no way I can reinstall Ubuntu. I managed to get the system to boot and got X working ok, but there are still some issues with other hardware. What I would like to do is reconfigure the system, similar to when the Ubuntu installer initally sets up your hardware. The problem is the lack of the ability to simply reinstall. Is there any way I can force the system to reconfigure all the hardware? I am currently trying "sudo dpkg-reconfigure -a" in the hopes that that will work, but I'm not very confident. If anyone has another idea as to how to reinstall based on the available methods of input that would work as well.

Thank you,
--MrAnt--

---

### Post by DagMan on 2007-06-10
Don't know if this works and you'd need to be comfortable with grub stuff.
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

If that works, or you find another solution, can you post it please.  I'm curious about it.

---

### Post by neptho on 2007-06-10
You may wish to start by editing /etc/modules to not reference hardware which this machine does not have; edit/remove the ethernet interfaces in /etc/network/interfaces (leave 'lo', you always need that), and then look in /etc/modprobe.d/ for loaded and blacklisted modules, but a 'stock' kernel, by design is set to work with most equipment.

Good luck!

---

### Post by mrant on 2007-06-10
Thanks for the suggestions. After running dpkg-reconfigure -a for, literally, all day, it failed to have the desired effect. I think the best to way to get what I'm looking for is to simply reinstall. I'm going to try what is explained in the post DagMan linked. Before I start editing my menu.lst though I'm going to need learn a lot more about grub. I don't want to be stuck with the system unable to boot anything. That link has got a lot of useful information, thanks a lot. I'll post again after I give it a shot and let you know how it goes.

--MrAnt--

---

### Post by mrant on 2007-06-10
Ok, I got the alternate install iso and the hd-media boot files, but I've run into a snag. I need to resize the root partition to make room for a dedicated partition to hold the install data (iso + hd-media files), but from what I can tell, it's not possible to resize an active partition. Due to the lack of external boot options (limited to just HDD) how can I resize this thing? I considered reclaiming the swap partition since I'm going to be blowing away the currently installed system anyway, but its not big enough, only 353MB. Anyone got any ideas?

--MrAnt--

---

### Post by mrant on 2007-06-16
After extensive research I have concluded that there is no way to resize an active partition, so the only way I can resize the partition to make room for the hd-media partition to stick the iso onto is by putting the hard drive into another laptop which supports pxe-booting and resizing the partition from the ubuntu netboot environment. I am currently in the process of doing this, and so far so good. I'll post the results just in case anyone is still following the progress.

--MrAnt--

---

