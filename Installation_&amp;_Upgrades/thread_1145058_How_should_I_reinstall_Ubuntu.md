---
title: "How should I reinstall Ubuntu?"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by EvanKroske on 2009-05-01
Situation summary:
Tried to upgrade to Jaunty.
[Could no longer boot up any linux kernels]("http://ubuntuforums.org/showthread.php?t=1143806")
Decided to reinstall Linux by overwriting partition (whole drive) with Live CD installer
Lost grub; couldn't even boot windows from first drive
[Regained grub; can now load windows]("http://ubuntuforums.org/showthread.php?t=1144338")

Now, when I try to load linux through grub manually, it hangs at "Starting up..." permanently. My installation was probably crippled by one of the glitches I encountered from trying to overwrite a linux partition wrong. When I start the Live CD Ubuntu installer and reach the partition step, it only shows one drive; the one with windows on it. 

I have three questions: Why can't the partitioner see my second drive anymore?; Does that matter, or should I reinstall Intrepid Ibex a different way?; and What should I do now?! It seems to me that the solution will be to destroy the partition containing just Ubuntu (not grub), reinstall Ubuntu in the blank space, and point grub to its new boot files, but I'm obviously not very confident in my plan or my installation skills. Thanks for reading.

---

### Post by zigga15 on 2009-05-01
Gotta install windows first, set up some "Unpartioned space" from the windows partitioner, then you have to install linux after that. Windows doesn't like to go onto a drive after linux, but linux can do it easily :P

Not sure why this happened to you, sounds weird.

good luck, hope this helps.

~ Dan

---

### Post by zigga15 on 2009-05-01
sorry for another post. But did u get the official cd - otherwise you may have a corrupt image - try checking the md-5 checksum:

[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_094.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_094.html)

---

### Post by EvanKroske on 2009-05-01
Windows is installed and working and grub is installed and working; I just don't have linux. I don't want to destroy my grub partition again (unless I must), because then I won't be able to boot anything.

Edit: Yes, I burnt the CD myself, checked its md5 sum, and verified its integrity: the CD is rock solid.

---

### Post by zigga15 on 2009-05-01
If you have windows installed and you have either "RAW" unpartitioned space or another drive with space on it you should be able to install it fine.

Just to a custom partition and pick where you want it to go. This should be fine on your grub. It worked great for me. As long as windows was the first thing you installed.

Installing windows after linux on the same disk, can kill grubs, kill swap space, and god knows what else :P - damn communi$t micro$oft

---

### Post by codeseer on 2009-05-01
If GParted can't see the drive, you may have some problems. Have you tried disconnecting the Windows drive and seeing if it can then see the Ubuntu drive?

---

### Post by EvanKroske on 2009-05-01
No, I don't like to open up my hardware unless I have to. I sorta followed zigga's advice, booting up windows and repartitioning the linux drive. However, when I reinstalled linux in the blank space, I got the same problem I got last time: an error saying "The window server has crashed about six times in ninety seconds." I tried to look up the error, but all the instances I could find were people who had messed up their xorg.conf files. The error appears after a screen that looks like a hardware check ending with this line:
```

Checking battery state              [Ok]

```
After seeing that, the screen flashes black several times, then the error comes up. I hit enter to get rid of the error and I see the same screen for the two minutes the window server waits until it tries again. Is there a way I can boot the system without the window server to see if I can fix the problem that way?

---

### Post by zigga15 on 2009-05-01
Try leaving about 500MB to a GIG of raw space between the partitions

i.e make a third partition that is tiny.

Its a long shot but it might work. This whole thing is very wierd but I would put it down to a windows problem. It doesn't play well with other operating systems. 

If they are on different drives you "shouldn't" have a problem. However it might be a "Master-Slave" problem. I.e if windows is on a secondary slave drive then it might have a complain. Might have to mess around with your bios if that is the case.

Try googling the windows error message on micro$oft sites.

---

### Post by EvanKroske on 2009-05-02
Problem solved. After a hard day of researching grub and linux loading, I realized that I had been doing it wrong. I had been trying to load linux like I load windows:
```

root (hd1,0)
chainloader +1
boot

```
That code would simply load grub again. After that, I tried loading the second partition on the linux drive:
```

root (hd1,1)
chainloader +1
boot

```
As any linux user knows, linux creates two partitions upon installation: the file system and a swap file. That code above attempted to boot the swap file; that's why it would hang on "Starting Up...". 

Finally, I looked it up and found that I need to load linux a completely different way, with these commands:
```

root (hd1,0)
kernel /vmlinuz root=/dev/sdb1
boot

```
Those commands sent me into a kernel panic every single time, because I was missing another critical yet poorly documented grub command: **initrd**. I finally got it to load properly with this series of commands:
```

root (hd1,0)
kernel /vmlinuz root=/dev/sdb1
initrd /initrd.img
boot

```
Success! Apparently, my new linux installation was fine all along; my grub ignorance was the source of my woe. Although, I never did see that "The display server has been shut down 6 times in 90 seconds" error again... Thanks for all the help; maybe this thread will help someone else overcome their grub incompetence.

---

