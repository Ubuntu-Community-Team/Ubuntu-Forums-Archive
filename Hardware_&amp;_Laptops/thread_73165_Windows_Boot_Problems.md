---
title: "Windows Boot Problems"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by Cad-Monkey on 2005-10-08
Hey all,

I have been experimenting a little bit, and it has gotten me into trouble. I am hoping someone on here will be able to help me fix this.

Last night I tried to install Gentoo Linux. After all, a week ago, I had to reformat my hard drive again (it is a new computer, and the university hard drive image has been very uncooperative for me, so I have had chances to try Ubuntu, Red Hat, and this time -without much luck- Gentoo.) Anyhow, I ran fdisk, and tried to make an extended partition with a swap and a root partition in it for Gentoo. When I wrote the changes, I got this error :

     The Partition table has been altered!


     Calling ioctl() to re-read partition table.

     WARNING: Re-reading the partition table failed with error 22: invalid argument.
     The kernel still uses the old table.
     The new table will be used at the next reboot.
     Syncing disks.

So I rebooted, thinking that that would prepare my hard drive to write on the new partitions. Well, surely enough, the hard drive simply wouldn't boot anymore. No Windows. Just a blinking underscore. Windows died.

Here is the good news. I installed trusty old Ubuntu Hoary, and was able to get the hard drive to grub. From there, I was able to rescue files from my windows partition and move them to my mac. YAY! I haven't lost any of my work!

But, Windows will not grub. It shows up in Grub, but if you try to load it from grub, it shows you this text : 

      root (hd0,0)
      Filesystem type unknown, partition type 0x7 
      savedefault 
      makeactive
      chainloader +1

Screwy, huh?

Does anyone know what is going on here? Can anyone tell me how to get Windows to load properly again? I should mention that this computer is a month old IBM Thinkpad T43p. It would be a nice machine, if I could keep it running properly in windows for more than 2 weeks...

I will be your best friend forever if you can tell me how to get this computer to boot from windows again. 

-------------Cad-Monkey

---

