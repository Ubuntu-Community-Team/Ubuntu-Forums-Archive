---
title: "what version shold i chose for my eee 901?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by mirana on 2009-09-06
hello all!
so i have an eee pc 901 and i think i want to install ubuntu on it.
now i thought i would ask you which disrto is best suited for this, eeebuntu, ubuntu eee, ubuntu eee gold, ubuntu netbook remix etc.
maybe some advantages and disadvantages?

(also, it would be a plus, and i would like to know if it would be possible to, play warcraft 3 under wine on it, though it's not really a necessity.)

---

### Post by Herman on 2009-09-06
I like the standard desktop Ubuntu in my Eeepc.

About the main thing to know is when a window is too big to fit in the screen and especially if there are buttons that need to be clicked on at the bottom of the window, we can press the tab key while dragging with the mouse to lift the bottom of the window into view. I think that's something that has been fixed in the special eeepc versions. It's a minor thing that would annoy some people after a while but which I'm prepared to tolerate in order to have my standard Ubuntu. I like 

I have a list of tweaks and settings that I think improve things in various ways, like making the partition begin on an erase block boundary, ext4 file system, noop io scheduler, noatime, setting swappiness to 10 and using a swap file instead of a swap area. I guess that about covers all the main ones. I can go into details if you're interested.

Regards, Herman :D

---

### Post by mirana on 2009-09-06
details sound great :D

---

### Post by Rhubarb on 2009-09-06
> **mirana said:**
> ...(also, it would be a plus, and i would like to know if it would be possible to, play warcraft 3 under wine on it, though it's not really a necessity.)

I wouldn't think the integrated intel video graphics would be quick enough to be able to run Warcraft 3 on your little eeepc 901.

Personally I'm running the stock Ubuntu 9.04 / 9.10 alpha 5 on two eee pcs here, they both run well.
- I have customised them to be using ext4, no swap partition or swap file.

---

### Post by mirana on 2009-09-06
> **Rhubarb said:**
> I wouldn't think the integrated intel video graphics would be quick enough to be able to run Warcraft 3 on your little eeepc 901.

Well, the graphical requirements for warcraft 3 are "8MB 3D video card (TNT, i810, Voodoo 3, Rage 128 equivalent or better) with DirectX 8.1 support", which in theory the 901's intel GMA 950 should be able to handle (224 MB, 400 MHz and directX 9 support...)
[ [http://www.youtube.com/watch?v=__kfP3koyeE](http://www.youtube.com/watch?v=__kfP3koyeE) ]

Question is, does it run under wine? :-|

good to know that it'll run the 9.10 alpha too...

---

### Post by foobic on 2009-09-06
I tried eeebuntu first, but decided that the only thing I really wanted from it was the eeepc-tray and its acpi utilities. So I went back to the standard desktop (on ext2, no swap) and just added those.

But the graphics performance is poor with intel graphics on the stock kernel (well known issue, apparently) so I loaded the 2.6.30 kernel in "Optimal" configuration as described in [this thread]("http://ubuntuforums.org/showthread.php?t=1130582"). I managed to crash X several times along the way but worth it for smooth OpenGL 3D (and the ability to run compiz effects).

In the end, with the help of eeepc-tray, everything just works - full power saving controls, all the special buttons and function keys, wireless, bluetooth, usb mobile broadband and DVB-T... Great little machine!

Haven't loaded wine yet (not sure I'll bother, since I have XP in a VirtualBox) and I'm not into gaming so can't help you there.

---

### Post by Herman on 2009-09-06
> details sound great :D:D Okay.
These ideas are only useful if your eeepc has an SSD drive instead of a hard disk drive.
I'm not sure what your 901 has, but the 701's I use have SSD drives.

1. making the partition begin on an erase block boundary,
SSD drives are made of flash memory MLCs and a flash memory controller. The controller makes the disk appear to the operating system and it's user as if it's a hard disk, with tracks, cylinders and sectors. Really the flash memory is divided into erase blocks, commonly 1 MiB each in size. 
[Aligning filesystems to an SSD&#8217;s erase block size]("http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/")  - Theodore Tso

2. ext4 file system,
Supports ATA trim command, but that's probably not able to be used yet unless the eeepc has an SSD drive with a very up to date controller, which it might have. (Some of my info sources are a few months old already - a long time in terms of computer technology).
[TRIM (SSD Command)]("http://en.wikipedia.org/wiki/TRIM_%28SSD_command%29") - Wikipedia
[Linux ATA Trim Support]("https://lists.ubuntu.com/archives/kernel-team/2009-May/005776.html") - [https://lists.ubuntu.com/archives/kernel-team/2009-May/005776.html](https://lists.ubuntu.com/archives/kernel-team/2009-May/005776.html)
[New vs Used SSD Performance]("http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=13") - Anandtech
The ext4 file system holds back writes to disc and stores them in memory longer, so every small change doesn't get written immediately to disc.
I used to prefer reiserfs for flash memory and I noticed it seemed much faster than ext3 in some flash memory sticks I have, but now that I've tried ext4, it seems as fast as reiserfs or maybe faster. I have tried used benchmarking software for testing. That gives numbers which make me feels as if I'm being objective and impartial but in reality I think just trying out the file system with a running operating system gives a better feel for which file systems work best. When I hoover my mouse over the 'Applications', 'Places' and 'System' menus in Ubuntu I like to see the icons appearing right away, not several seconds later.

3. noop io scheduler, 
Because we're not using a spinning hard disk with read/write heads on an arm controlled by a voice coil actuator, (see '[head actuator]("http://www.storagereview.com/guide/actActuator.html")' -StorageReview.com), there's no need to queue up disk reads and writes waiting for the read-write heads to be passing through the right neighborhood on the hard disk. We can send the information or read it electronically right away. [Noop scheduler]("http://en.wikipedia.org/wiki/Noop_scheduler") - Wikipedia, the free encyclopedia.
To do that I add elevator=noop as a kernel option in my /boot/grub/menu.lst and run update-grub.```
# defoptions=elevator=noop quiet splash
```4. noatime, 
Linux file systems record the last time the file was modified and the last access time. Skipping updating the access time can save some work for the disk and speed things up a little bit. 
I edit my /etc/fstab with noatime as a mount option for the file system.

5. setting swappiness to 10,
So the system will prefer to use the RAM most of the time, which is faster.
See: [Performance tuning with 'swappiness']("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") - Ubuntu Community Docs.
```
gksudo gedit /etc/sysctl.conf
```Add this line at the bottom of the file,
```
vm.swappiness=10
```6. using a swap file instead of a swap area,
  [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") - by iva2k.

:D I'm out of time right now, I'll come back and edit this post later on ... bye for now

---

### Post by Hobgoblin on 2009-09-06
I use the the standard 9.04 Ubuntu desktop edition on my 900A with the alternative graphics driver.

---

### Post by mirana on 2009-09-08
wow, mate. you make me feel spoiled, it's like you're writing a guide just fo me; you should definately make this into a HOWTO ^^
i can't wait for this weekend, when i'll have the time to try this out :D
(nad yes, the 901 has two ssd's, one small and fast, one slightly larger for storage)
 
I don't know how i can thank you; you are what makes the ubuntu comunity so formidable.

---

