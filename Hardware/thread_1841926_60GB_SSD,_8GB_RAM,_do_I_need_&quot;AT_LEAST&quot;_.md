---
title: "60GB SSD, 8GB RAM, do I need &quot;AT LEAST&quot; 8GB Swap??"
date: 2011-09-10
forum: Hardware
---

### Post by ProNux on 2011-09-10
I have a notebook with 8GB RAM & 120GB SSD.  Do I need an equal 8GB of Swap partition?  I can't afford to allocate 16GB of SSD space.

This notebook will be dual-booting with Windows.  I plan 70GB for Windows (1 partition only including data), and the remaining for Ubuntu including swap, but I'm not sure how much I will use for swap.

I read in the documentation that SSDs still need swap.

Any suggestions?

Edit:  The SSD is 120GB (not 60GB) as stated on the subject.  Already corrected.

---

### Post by haqking on 2011-09-10
> **ProNux said:**
> I have a notebook with 8GB RAM & 120GB SSD.  Do I need an equal 8GB of Swap partition?  I can't afford to allocate 16GB of SSD space.

This notebook will be dual-booting with Windows.  I plan 70GB for Windows (1 partition only including data), and the remaining for Ubuntu including swap, but I'm not sure how much I will use for swap.

I read in the documentation that SSDs still need swap.

Any suggestions?


The legacy idea of double the size is kind of redundant these days.

The same size + 1 if you will suspend to ram.

You can get away with less, depends on the resource intensity of your apps.  Such as multimedia and image manipulation etc.

I would say 2 or 4gb should be fine unless of course you use large apps or suspend to ram is an issue

---

### Post by oldfred on 2011-09-10
With an SSD there is no reason to suspend, you should be able to boot so quick it does not matter.  You hopefully will never use the swap as it is slow, but having some is recommended. The real memory intensive applications are video editing or if you are a user that loads everything and keeps it running. But with 8GB you will have trouble loading enough programs and data in most cases to fill memory.

Linux automatically uses RAM as a cache if not otherwise used to speed up things. So memory may lool full but it is not.

Another alternative is a swap file.
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")
I prefer sleep and shutdown to hibernate.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

---

### Post by ProNux on 2011-09-10
(My bad, the SSD is 120GB, not 60GB as stated on my original post)

Definitely I won't be running video editing and those memory hungry applications. I think swap file (not partition) is a better way. Thanks for clearing things up.

But I think I should read more info.  Like somewhere I read that Ubuntu 10.04 does not "yet" support TRIM, but how about 11.04?  And also about using swap will reduce SSD's life span?

---

### Post by walt.smith1960 on 2011-09-10
I've installed Linux a number of times and create a swap file if I feel like it;). This is on a 4GB. RAM machine and I've never run into a "not enough memory" situation. Like Old Fred says, create a swap file if you feel it's necessary.  AFAIK the only time a swap partition is **required** is if you want to hibernate/suspend to disk.  Linux needs a separate partition to write the RAM contents to.  Even with a convention hard drive, Ubuntu boots fast enough that I don't see a need to suspend to disk.  I use suspend to RAM and have not had a problem with it or I power down if I'm not going to use the machine for a day or more.  Others may have different requirements.

---

### Post by ProNux on 2011-09-10
Thanks, I think in my case, swap file is more appropriate and as far as I know, a swap file size can be changed anytime (correct me if I'm wrong).

---

### Post by oldfred on 2011-09-10
Some more info.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Arch site says 
> **Warning: **It is critically important that users switch  the controller driving the SSD to AHCI mode (not IDE mode) to ensure  that the kernel is able to use the TRIM command.
**Warning: **Users need to be certain that kernel version  2.6.33 or above is being used AND that their SSD supports TRIM before  attempting to mount a partition with the discard flag. Data loss can  occur otherwise!

---

