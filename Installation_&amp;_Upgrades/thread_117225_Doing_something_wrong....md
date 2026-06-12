---
title: "Doing something wrong..."
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by MrRabbitC on 2006-01-14
When partitioning hda and hdb; I can't seem to get ubuntu to see hdb as a usable drive.

What do I need to do? The drive is turned on in the BIOS and Ubuntu will load on either drive, but not see the other. So I am obviously doing something incorrectly when partitioning.

Can anyone help?

---

### Post by aysiu on 2006-01-14
So you have two Ubuntu's one on hda and one on hdb, and you can boot into both, but you want to be able to browse hdb while in hda and vice versa? Is that the situation?

---

### Post by MrRabbitC on 2006-01-14
Is it possible to install Ubuntu on hda and use hdb as extra file space? That is what I would like to do. I have a 20 GB HD for hda and a 120 GB HD for hdb.
Or should I just remove the 20 GB and go with the 120 GB only?

---

### Post by aysiu on 2006-01-14
[QUOTE=MrRabbitC]Is it possible to install Ubuntu on hda and use hdb as extra file space? That is what I would like to do. I have a 20 GB HD for hda and a 120 GB HD for hdb.
Or should I just remove the 20 GB and go with the 120 GB only?[/QUOTE] Yes, it's possible and advisable. 

During the installation process, select "Manually Edit Partition Table."

Then select /dev/hda1 to be reformatted as Ext3 and mounted at **/**

Select /dev/hdb1 to be reformatted as Ext3 and mounted at **/home**

You may want to create a small swap partition as well; though, I don't know whether that would be best on /dev/hda1 or /dev/hdb1

---

### Post by MrRabbitC on 2006-01-14
Don't know if this is even possible.
Right now this is what I see:


IDE1 master (hda) - 20.0 GB WDC WD-200AB-00CDB0
              pri/log 20.0 GB         FREE SPACE
IDE1 slave (hdb)   - 122.9 GB Maxtor 6L120P0
              pri/log 122.9 GB        FREE SPACE

What would be the most efficient way to partition these drives?

---

### Post by MrRabbitC on 2006-01-14
Sorry, posted a couple of seconds after you there.

So now it looks like this:

IDE1 master (hda) - 20.0 GB WDC WD-200AB-00CDB0
/ 20.0 GB 
IDE1 slave (hdb) - 122.9 GB Maxtor 6L120P0
/home 121.9 GB 
/swap 1.0 GB

We'll see how it goes! 
Thanks for the help aysiu. Much appreciated.

---

### Post by MrRabbitC on 2006-01-14
Nope. It didn't like that.

---

### Post by aysiu on 2006-01-14
[QUOTE=MrRabbitC]Nope. It didn't like that.[/QUOTE] Can you be more specific? What did you do? At what part did it fail? Was there an error message? What was it?

---

### Post by MrRabbitC on 2006-01-14
It said there was no swap space available and that it is recommended that some swap space be allocated. So I assume hda needs some swap space too? When I say 'it' I mean when the partition manager started writing the partitions.

I'm now partitioning like this:

IDE1 master (hda)
    #1 primary 19.0 GB  ext3   /
    #2 primary  1.0 GB  ext3   /swap
IDE1 slave (hdb)
    #1 primary 120.9 GB ext3  /home
    #2 primary    2.0 GB ext3  /swap

What do you think?
I may be totally hosed here.... but I'm learning.

---

### Post by aysiu on 2006-01-14
Yes, you do have to create some swap space. I don't think you need it on both hard drives, but I don't know which one it's most appropriate to have swap on... or if it matters at all.

How much RAM do you have? Swap is usually supposed to be about twice the RAM size but no bigger than 1 GB.

The Ubuntu installer has a part where you can resize partitions and create new partitions, but it may not seem the most intuitive to you if you're just beginning. You press Enter on **size** and then enter a new partition size. To see what this looks like, scroll a little above the middle of [this page](http://users.bigpond.net.au/hermanzone/p3.htm). The example resizes an NTFS partition, but the same principle applies to Ext3.

I would recommend either [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) to create the swap partition or using QTParted on Knoppix.

Both involving downloading another ISO and burning it, but it's worth having a live CD around for recovery and other tools.

---

### Post by MrRabbitC on 2006-01-14
Awesome, 
I'll give it a try and let you know how it goes.
Thanks again for the help. You rock.

---

### Post by Ptero-4 on 2006-01-14
AFAIK. The swap should go on the first drive and /home alone on the second.

---

### Post by MrRabbitC on 2006-01-14
Yeah, The partition manager flagged the two /swap partitions as bad.
Although, when I try creating just one partition /swap on the hda, it tells me there is no partition and asks if it should continue.
This time I just said yes. So we'll see what that yeilds on install.

---

### Post by MrRabbitC on 2006-01-14
C'mon... Isn't this fun?

You're witnessing the slow death of windows in action here....

---

### Post by MrRabbitC on 2006-01-14
Well that seemed to have worked. I can see both drives now which sparks another question....

Can I use the free space on hda (19 GB) for data since it is allocated to / without totally screwing up the OS? Do I need to partition out the free space to something else?

---

### Post by aysiu on 2006-01-14
[QUOTE=MrRabbitC]
Can I use the free space on hda (19 GB) for data since it is allocated to / without totally screwing up the OS? Do I need to partition out the free space to something else?[/QUOTE] I don't know what you're asking. You have a second hard drive with 120 GB...? 

Ubuntu and all its programs probably take up at the very most 6 GB (and that's if you install *a lot* of programs), so if you wanted to resize that partition and make another one for another operating system, you could. Keep in mind that if you install Windows, it'll overwrite Ubuntu's Grub boot menu on the Master Boot Record (MBR).

Did you just want more space for data...?

---

