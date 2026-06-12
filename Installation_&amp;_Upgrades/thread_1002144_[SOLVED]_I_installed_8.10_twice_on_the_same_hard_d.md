---
title: "[SOLVED] I installed 8.10 twice on the same hard drive"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by gdeer81 on 2008-12-04
I loved it so much I put it on twice.

It all started when I had problems partitioning the drive in the setup.  I kept getting an error saying it couldn't resize it. Basically it sent me to the next step where it showed the file system. When I tried to manually make some space and create the partitions it gave me the error again.

After playing with the manual resizer and then hitting the back button to the resizer guide I got it to work but I think I just hosed it.  When I select windows as my OS I get a white cursor that blinks at me until I hit ctrl+alt+del to reboot.  

After completing the install I couldn't see anything when I logged in to ubuntu.  This happened when I used wubi ubuntu on my other PC(which was fixed by uninstalling and using wubi xubuntu; should've taken that as a hint it wasn't the install).  I had a feeling it might just be something with ubuntu but I couldn't figure out what so I went through the whole process again from the CD.  This time I figured since my HD was messed up I might as well put the slider to 100% ubuntu.

After a few more hours on the forums I finally find the compiz bug.  After logging in to failsafe terminal and running the sudo commands to disable it I could log in and see everything instead of a plain brown background and my pointer.  Yay, I had ubuntu working but now I have two of them.

So now when I boot up I have 3 options: ubuntu,  windows (that doesn't work), and ubuntu.

Should I try to recover windows or is that just a lost cause now?  Not that I need it because I could make a copy of windows from my other computer(which would make me a criminal *yikes*) but I'm more concerned about the files that may be lost.  I backed them up on a CD that I didn't label and haven't seen in a couple weeks.

And more importantly how do I clean up my hard drive to have only one copy of 8.10?  

Thanks for any assistance and sorry for the mega-post.

Cheers

---

### Post by jerrykenny on 2008-12-04
wow . . . .gosh . . . 

OK i wonder how many OS's you really have on that Hard drive . . . 

Open a terminal, type in 

sudo fdisk -l

and let us see what results you get from that?

---

### Post by gdeer81 on 2008-12-04
[HTML]Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4fa9eb4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         724     5473408+   b  W95 FAT32
/dev/sda2   *         733         745       98280   82  Linux swap / Solaris
/dev/sda3             746       10337    72515520    5  Extended
/dev/sda5            7404       10209    21213328+  83  Linux
/dev/sda6           10210       10337      967648+  82  Linux swap / Solaris
/dev/sda7             746        7207    48852657   83  Linux
/dev/sda8            7208        7403     1481728+  82  Linux swap / Solaris

Partition table entries are not in disk order[/HTML]

---

### Post by Happypants on 2008-12-04
Ok... you actually have 3 OSs on your comp, but you're trying to boot using Linux swap space, that explains why windows won't work.  

If you want to attempt to get what's on your Windows partition back then you can try a program called Parted Magic.  [http://partedmagic.com/](http://partedmagic.com/)  I used it to get back some of a lost partition and had a bit of success.  

After that I'd use the GParted tools that come with the program and get rid of all those partitions (right now your have 7 on your drive).  Just delete them and start over at this point.  After you do that your comp should boot up and say something to the effect "No operating system found".  Install Ubuntu like you did before but let it do the partitioning the first time and let it use the whole disk right off the bat (if you want, otherwise you could mess with the partitions yourself). 

Good luck to ya and remember to back up your data next time.

---

### Post by jerrykenny on 2008-12-05
Your windows installation looks to be intact, so theres prob no harm in keeping it there . . . . (its the first partition on the list) it may come in handy if you intend to use canon printers, say, or certain usb wireless devices.

Might i suggest a partition table for future use ?

   Device Boot      Size           System
/dev/sda1             55Gb         Windows
/dev/sda2   *         100mb         ext2     /boot
/dev/sda3              1Gb          swap      swap
/dev/sda5              10 Gb         ext3      /   (this is the root file system)
/dev/sda6           rest of disk     ext3      /home

---

