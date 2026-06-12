---
title: "Is there a solution to the suspen/hybernate problem?"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by p10 on 2008-01-27
I am running ubuntu 7.10 on a AOpen 1556 laptop with lots of "Intel Inside".  I have tried to make my laptop hybernate or suspend to ram, to make my batteries last longer. But when I want to resume after suspend/hybernate I just get a black screen... 

Sometimes I get a coursor that I can move around, other times the coursor is frozen. My only option is to turn the PC of using the powerbotton.

I have read many topics on this problem, but I have not found a solution yet. It seems to me that suspend/hybernate is like playing the lottery; If you are lucky it works on your computer, and if you can't get it to work there's little you can do about it...?

I get the impression that this is a big problem with ubuntu 7.10, but not so on earlier releases... Could my solution be to install 7.04, 6.10 or 6.06 while waiting for 8.04??

---

### Post by steveneddy on 2008-01-27
I have 64 bit Gutsy (7.10)

My issue with suspend was fixed when I installed the 32 bit hwclock in the package util-linux.

There are small fixes that can make this easier.

From[ this thread]("http://ubuntuforums.org/showthread.php?t=676422&highlight=gutsy+suspend"):

> 
Try changing some of the options available on /etc/default/acpi-support

On my laptop, changing the
SAVE_VBE_STATE=true

and

POST_VIDEO=true

to false did the trick.


Also - in my file

```
/boot/grub/menu.lst
```

I added this line to the **kernel** line:

acpi_sleep=s3_mode

So that it looks like this - 

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro quiet splash[/COLOR] **acpi_sleep=s3_mode**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

The kernel line just wraps around in this post, but just add this to the end of the line after "splash" and re-boot and see if it works.

These are the three things I had to do to get suspend to work on my machine.

You may not have to install the 32 bit version of hwclock. This was an alternate issue that effected the suspend feature on my laptop.

The second two suggestions are the most popular.

---

### Post by p10 on 2008-01-27
Thank you for the tip! Tried it, but it didn't do it for me. 
Could it be som kind of problem with my videocard?

**Edit:** After turning off my desktop effects and rebooting, my PC now wakes up from suspend!
But when it does so, my wireless doesn't work! At least it feels like I'm getting somewhere!

I'll report back after working on the wireless-problem!

---

### Post by nowhere@cox.net on 2008-01-27
Thanks for the summary steveneddy! I did options 2 and 3 on your list and suspend works perfectly now for me.Did 5 cycles to test it out since I had read that others found it very intermittant. 

For the record I have a Lenovo T61 with the nvidia quadro 140 discrete card, Intel 7500 core 2 cpu and 4GB kingston value ram. 

Next is to get hibernate working although I almost never use hibernate.

Thanks again!
Eric

---

### Post by p10 on 2008-01-27
I have tried to restart the network using this command:

```
sudo /etc/init.d/networking restart
```

But it doesn't do the trick!

Have also tried adding

```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="[COLOR="Red"]networking[/COLOR]"
```

But it did not help...

---

