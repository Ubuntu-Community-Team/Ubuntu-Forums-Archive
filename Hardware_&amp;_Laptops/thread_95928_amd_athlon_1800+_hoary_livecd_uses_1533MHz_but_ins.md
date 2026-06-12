---
title: "amd athlon 1800+: hoary livecd uses 1533MHz but installed uses only 997Mhz"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by spite on 2005-11-27
Hi all. I've been using ubuntu since Warty, but I've never been a linux command-line/source-compiler user.

I have this Acer Aspire 1310, and it has had clean installations of warty, hoary and now breezy. My processor is an Athlon XP 1800+, this is part of proc/cpuinfo:

model name      : AMD Athlon(tm) XP 1800+
stepping        : 1
cpu MHz         : 663.745

I am running powernowd, and the top speed of the micro seems to be 997MHz, even though the real top is 1533Mhz. I thought it was something in the kernel, or something in the cpu scaling module, so I looked and looked in the forums and in the Internet. Some people are reporting the same problem, but I haven't found a solution which seems to work. Everybody seems to assume that is a powernowd problem, but lshw reports size and capacity of 1150MHz.

Okey, I could stop right now and assume that's the way my processor is. But the problem is that when I got my snail-mailed Breezy CDs, I first tried the Live CD, and when it started, the CPU was running with load over a glorious 1,4GHz. So I thought that I was saved with the new release. But I was not, since once it was installed in the laptop, it turned back again to the dull 663Mhz-997Mhz speed.

So - what can I do? Is there anybody who can help me, please?

---

### Post by spite on 2005-11-29
Bump/update: I've just read that there's a problem with many laptop BIOS managing PST tables. May be all those problems people are having all around about scaling are due to some cheesy BIOS. So: 

1. How to flash a BIOS using a linux _without_ using a win/dos boot disk?
2. If the BIOS update doesn't work, how can the PST tables be manually fixed?

And the funny thing about the LiveCD detecting everything with no trouble.

Thanks.

---

### Post by spite on 2005-11-29
I will reply myself, again. 

I've solved the problem by updating the BIOS. A quick guide for the perplexed on upgrading bios with non-linux tools. Download a "Non-Windows Based Image Files W/ImageApp" at [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) (WinMe is just fine). Unzip it and type "dd if=_the_name_of_the_image_file of=/dev/fd0" (or your media). You'd better do it as normal user, because you will probably need to delete some files in order to make some room. After that, just copy the rom file and the tool and reboot your computer. Check in the BIOS the boot order and flash it like there's no tomorrow. Once completed, you should be good to go with the latest revision of your BIOS. Check powernow freqs with "dmesg | grep powernow".

See you around!

---

