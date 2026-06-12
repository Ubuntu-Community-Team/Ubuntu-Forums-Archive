---
title: "DMA-problems....box freezes"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by mart1 on 2005-10-11
Hello

I have the Ubuntu server version installed, Hoary 5.04.
Problem: Every once in a while my box freezes, and I have to push the reset-button to boot it. When I look at the log afterwords I see this message:

localhost kernel: hdf: dma_timer_expiry: dma status == 0x61
...then restart

I have no idea what this means, so I hope someone here can help. This is a Samsung 250GB btw. I have two of these in RAID.

If you need: 

sudo hdparm /dev/hdf

```
/dev/hdf:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 250059350016, start = 0
```

Thanks for any help!

---

### Post by alwbsok on 2005-10-11
Sorry, I know this is somewhat off topic but how om earth are you meant to post a new thread??????:mad:

---

### Post by Zelut on 2005-10-11
First Post: do you have dma turned on?  From what I hear its turned off by default but you can change that.  Instructions at [www.ubuntuguide.org](www.ubuntuguide.org)

Second Post: go to the appropriate forum & click 'new post' in the top left of the screen...

---

### Post by mart1 on 2005-10-12
OK, thanks.
But if you look at my first post and the print of hdparm, it sure looks like DMA is turned on:
               'using_dma    =  1 (on)'

...and Ubuntuguide.org's 'guide' on this is for speeding up CD/DVD-Rom. 
My hdparm.conf file doesn't even contain /dev/hdf...

I'm new to Linux, so still need a little help :)

---

### Post by mart1 on 2005-10-13
OK, nevermind this problem. I think it was because of my Promise raid controller, so I just disabled it.
But I still want the disks(2x 250GB IDE) in RAID. So now Im trying to set up software RAID 0, but Im missing a good guide for this. I manage to create the raid-array, and mount it, but when I reboot: gone! 
I see this message in the log

 'reiserfs_fill_super: can not find reiserfs on md0'

I have followed [this guide]("http://dcs.nac.uci.edu/~strombrg/Linux-software-RAID.html#striping") btw.

Thanks for any help!

---

