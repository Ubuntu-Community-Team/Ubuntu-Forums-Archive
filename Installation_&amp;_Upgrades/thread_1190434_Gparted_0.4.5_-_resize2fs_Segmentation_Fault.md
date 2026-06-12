---
title: "Gparted 0.4.5 - resize2fs Segmentation Fault"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by terazen on 2009-06-17
Hi,
I have been trying to use gparted live cd to resize my ubuntu partition to make room for another OS to test around with.  When I got my pc parts from newegg in the mail I put everything together in a hurry to play some video games and forgot to leave a spare partition for other things...

Anyhow, When I try resizing it using the graphical program on the livecd all I get is "nothing to do" when it gets to the shrink stage.  So I researched and found a suggestion to try `resize2fs -f /dev/sda1`.  I booted back to the livecd and tried it from the terminal and now I get "Segmentation Fault".

Does anyone have an idea how I can get this working?  The live cd is 0.4.5-2 which is supposed to work with ext4 since 0.4.2.

Any ideas would be appreciated.

Thanks!

---

### Post by tommcd on 2009-06-18
Try Parted Magic. There was a new version of Parted Magic that was just released yesterday:
[http://partedmagic.com/](http://partedmagic.com/)
Also, the Ubuntu live CD should be able to shrink your Windows partition to make room for Ubuntu to install. 
I assume you are currently using Windows since you said you built the PC to play games.

Also, what motherboard is in your computer?

---

### Post by terazen on 2009-06-18
Actually I have ubuntu jaunty right now.  I was really wanting to see what nexuiz and a few other games would look like with my new graphics card.;)

Thanks for the suggestion.  I'll check it out tonight when I get home.

---

### Post by terazen on 2009-06-21
PartedMagic 4.2 worked like a charm.  I guess it has a a few more up to date packages at the moment.  The whole thing only took about 4 minutes including the reboots. :o

Thanks!

---

### Post by tommcd on 2009-06-22
> **terazen said:**
> PartedMagic 4.2 worked like a charm. 

Parted Magic uses the same GParted and Parted programs that the GParted live CD has. For some reason though, I have found that Parted Magic seems to work better that GParted live CD. Parted Magic is also updated more frequently than the GParted live CD. And the newest version of Parted Magic includes the Clonezilla disk cloning tool as well.

GParted is still very good though.
Glad Parted Magic worked for you!

---

