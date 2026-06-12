---
title: "Grub Installation Fail"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by treezrppl2 on 2009-05-03
Hey everybody.
I _HAD_ a working, and functional (for the most part) Ubuntu running off of my 1.5TB sata hdd. i came across screen shots & vid caps of Kubuntu and was completely seduced, so i quickly DL'd the install CD, and started the installation for Kubuntu (i know. n00b mistake :'[ ). the point being, as many other people have experienced it failed at 94% with "Grub installation fail. this is a fatal error". attempt number 2 returned the same result.
i've now in the past two days attempted the reinstall about 12x. i've attempted to do manual partitions, use the entire disk, put grub in MBR, put grub in "/". no success. i'm now running off the LiveCD.

how can i get my computer back? is there a way to clear grub from the MBR? is there a way to completely reformat the entire drive (including MBR)? did i somehow break my HDD??? what happened?

(ps. if you need more specs, i'd be happy to post some, i just don't know the commands to do so. i'm a recent [attempted] convert from MS)

---

### Post by caljohnsmith on 2009-05-03
So when you say you specified to have Grub installed to "/", did you do that by clicking the "advanced" button in the final stage of installation, and there specifying the root Kubuntu partition (like /dev/sda1 for example)? Also, which file system are you using for the Kubuntu partition, like ext3, ext4, etc? And lastly, please post the output of:
```
sudo fdisk -lu
```

John

---

### Post by treezrppl2 on 2009-05-04
huh...
i have no explanation for this, but the last attempt at install i made (just to get into the LiveCD) managed to work out just fine... ubuntu installed (i went back to trying to just get Ubuntu up, and then i'll install KDE through here) and inexplicably everything went flawlessly...

thanks for your help anyway :D

---

### Post by NlCK on 2009-05-04
Try making a CDROM of Super Grub Disc. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) Click download CDROM on the right hand side.

It should boot from that CD and try to repair your GRUB so you can access your Operating Systems again. It's pretty self explanatory so you shouldn't have too much trouble with it.

---

