---
title: "Partition HELL - Vista"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by copan on 2009-06-10
I've done my own little research, I know I'm not the first one to ask questions like these; but why is Vista such a b**** when it comes to partitioning?

I tried Paragon as suggested by members in this forum, to no avail.  Paragon did my job in "virtual" mode, then when asked to restart so it could have full access to my hard drive... well it just forgot about the task after reboot.

Lastly, Vista's own built-in partition tool seems to work the best except for it's major limitations.  The following screen shot will help you understand my situation better:

[http://i172.photobucket.com/albums/w10/wigginDaddy/screeny34.jpg](http://i172.photobucket.com/albums/w10/wigginDaddy/screeny34.jpg)

As you can see from the right-click menu, I cannot extend the Ubuntu partition, nor can I extend the Space partition - but when deleted they are both unallocated space that do not work together for some strange reason (mind you I know little about partitioning and hard drives).

Can anybody tell me how I can bring these two partitions (Space and Ubuntu) to become one and peaceful?  Together they would make 7GB+ which would be okay for my Ubuntu install.  I'd like to have 10GB but I also cannot shrink the Windows partition anymore than it has already.

I'd be willing to try a partition program on Ubuntu but I don't know much about the terminal - which is why I'm installing in the first place.  I love the feel of it but don't know how to use the terminal effectively.

Thanks all!

---

### Post by coffeecat on 2009-06-10
You can't combine 'Space' and 'Ubuntu' because they are not contiguous. Sorry. No partitioner whether in Windows or Linux will be able to do this for you.

Another (minor) point is that both partitions are formatted NTFS which is a Microsoft filesystem. Ubuntu can read and write NTFS OK, but will need a native Linux filesystem such as ext3. The installer will do this for you.

However, there is a way around this. You could use the 3.39GB 'Space' partition for your / (root) partition, and the 4.3GB partition for /home. It will be a bit limiting, but it will get you going, at least until you can afford a bigger drive. :wink: You'll need the 'manual' choice at the partitioning stage of the installer.

By the way, you don't need to use the terminal to do partitioning in Ubuntu. In the live CD, simply go to System > Applications > Partition Editor, and Voila! A partition editor that knocks spots off most of what the Windows world can offer.

**Edit:** Paragon?! Hmmph! Spit! I installed Paragon in Vista - and then uninstalled it. :wink:

---

### Post by orangepenguin97 on 2009-06-10
i would get freebsd and use their partitioner, make 150MB for freebsd and split the rest of your hd how you want it. Of course, this would mean reinstalling everything.:(

---

### Post by Person_1873 on 2009-06-10
i suggest booting into an ubuntu live CD and using GParted to shuffle your partitions around until you have your roomy 7GB of space sitting at the end of your drive, you will need to delete your "space" partition, move your "windows" partition towards the front of your drive as far as you can, then extend your "ubuntu" partition out to 7GB, GParted will also allow you to format your ubuntu partition to a linux FS such as reiserFS or ext2/3/4 etc. this entire process will take many hours so i suggest that you set it to happen overnight while you sleep

---

### Post by copan on 2009-06-10
Thanks, your advice was helpful.  I just installed Ubuntu on the same drive as Windows so that space wasn't an issue.  I'm glad I know where the partition editor is in Ubuntu now though.

---

### Post by coffeecat on 2009-06-10
> **copan said:**
> I'm glad I know where the partition editor is in Ubuntu now though.

It's on the live CD, but doesn't come as default with a hard-drive installation. But all you need do is install it from Synaptic. Look for the 'Gparted' package.

By the way, you could use Gparted to resize XP partitions, but don't use Gparted to resize a Vista C: partition. Vista doesn't like it; it doesn't like it at all. [This page]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/") is not really what you need at the moment, but it describes this Vista problem well enough.

> 
**Using Linux to Resize**
 You can also use the [gparted live cd]("http://gparted.sourceforge.net/livecd.php") to resize your partitions. The problem with this is that it will definitely cause your system to not boot anymore unless you follow some [very specific steps]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"), because Vista can't handle it.

---

### Post by Mark Phelps on 2009-06-10
As to your original "problem", you could not extend the Ubuntu partition simply because there was no adjacent available space.  That limitation is true regardless of the partitioner used.  Also, as already mentioned, you can only combine adjacent partitions.

If you want to be able to continue to use Vista, do NOT use the Ubuntu partitioner or a Gparted liveCD to shrink or move the Vista OS volume.  If you do that, you run the risk of corrupting the volume such that it will no longer boot.  If you have a Vista DVD (not an OEM recover CD), you will most likely be able to repair that damage by booting into it and choosing Startup Repair, and running it over and over -- until it finds no more problems to repair.  If you don't have  Vista DVD, the corrupted partition will remain permanently unbootable.

---

