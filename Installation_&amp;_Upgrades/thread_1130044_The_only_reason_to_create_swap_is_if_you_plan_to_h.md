---
title: "The only reason to create swap is if you plan to hibernate???"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by kallenes on 2009-04-19
I've been reading throughout forums "*The only reason to create swap is if you plan to hibernate*"  

**Is this true? -> only for hibernation?**

On install I did not create a swap because of reading similar to the above. I don't use hiberation.
But, my eeePC901 with 2GB RAM is a bit slow at times, when memory is been used. **Would a swap help better it's performance?**

I have added uxa to video settings to resolve my scroll lag. But, i still have scroll lag and some general lag.

I've seen the 901 perform with windows XP. My ubuntu eee is slower. Shouldn't it be the other way around? :o

Any suggestions?

---

### Post by Elegia on 2009-04-19
I think normally swap space is used when you run out of RAM. The swap space is then used as an extension to the RAM, but because it works with the harddisk, it's much slower. 

So if the software you run uses more than the 2GB of RAM you have, it might help having a swap partition. 

As for hibernation, I'm not sure if it actually stores the system state on the swap or not. It makes sense though.

---

### Post by kallenes on 2009-04-19
I realize that it's been used as RAM, as it is in windows.

But, I'm certainly not using over 2GB of RAM running ubuntu eee 8.10, with one or two small apps running.

Why the lag? 

PS: I've even tweaked video controller option - uxa

---

### Post by oldos2er on 2009-04-19
> **kallenes said:**
> I've been reading throughout forums "*The only reason to create swap is if you plan to hibernate*"  

**Is this true? -> only for hibernation?**
  

 No, that's not true. It might be if amended to say "The only reason to create a swap partition the same size as installed RAM is if you plan to hibernate."

 I would imagine the slowness you're experiencing is because of hard disk I/O, not RAM.

---

### Post by Herman on 2009-04-19
I agree with oldos2er.
I prefer to think of the swap as a 'slow lane' for the memory, where slower moving items can be shunted out of the way, leaving the faster RAM free for the 'fast lane' items to whiz along briskly and freely.

I have an Asus EeePC 4G here with Ubuntu Intrepid Ibex in it and it's as quick as a flash! 
It has no separate swap area, but instead I have a swap file. I made that according to the following excellent how-to,  [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") - by iva2k.
I don't believe having a swap file or a swap area will reduce the life of the flash memory to the degree where it would be uneconomical.  
I set the swappiness to 10 though, to make the operating system prefer to use the RAM more and the swap file less for better performance. See: [Performance tuning with 'swappiness']("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") - Ubuntu Community Docs.
I'm using the vmlinuz-2.6.27-8-eeepc kernel.
My EeePC still uses the standard 512 MB PC2-3200 SODIMM memory module it came with from the store. I'm considering a memory upgrade. I haven't decided yet, it's working fine the way it is.

I'm using the Reiser File System because it's supposed to be 10 to 15 times faster for small writes to disc. It doesn't look much faster in benchmarking tests, but in real life I've noticed it makes a very great and real difference. ReiserFS is way faster in flash memory or an SSD, at least in the ones I've tried. Results can vary between brands and models of flash.
I have the with the 'nolog' option set in /etc/fstab to turn off file system journalling, again for performance not because I'm scared of wearing out the flash. I'm not sure if that makes much difference in speed though. 

I haven't tried the ext4 file system in an SSD drive yet, but it's supposed to have a lot of improvements over ext3, and I'm hoping it'll give ReiserFS some competition there.

---

### Post by kallenes on 2009-04-20
Thx for detailed replies .. much appreciated guys.

I can't see how the SSD's I/O could be the cause .. i have seen the eeePC901 with windows XP run very quickly. 

I'm using easy peasy 2.6.27-8-eeepc kernel.

You see, I'm new to linux. 
So before installing easy peasy i read in the forums how to partition and install, keeping in mind the SSD longevity situation.(I hope you're right Herman, not a nice thing about SSD's)

so, this is what i did.

/      SSD0 4GB ext2
/usr   SSD1 16GB ext3
/tmp   SSD1 16GB ext3
/home  SDHC 8GB CLASS6
no swap

Could my partition structure be the prob? Is it the correct method for a linux install?

I really don't want a swap part/file, I've got 2GB of RAM ... and it's a NetBook .. i use it for my internet stuff ... not like i'm running any large apps. 

But, i do have lag, and some scroll lag - especially in firefox.

---

### Post by Herman on 2009-04-21
Have you tried timing how long it takes your PC to boot up?
Also, how long does it take to open a spreadsheet the first time and how long does it take to open a spreadsheet again after your first one is closed?
Also, do the icons on your 'Applications', Places and 'System' menus appear instantly? Or do they take a long time to appear when you mouse over each sub menu?
What about the second time you try mousing over all your menus? Still slow?

I'm timing my boot-ups from the GRUB prompt, (when I hit 'Enter'), all the way through the login until I have a usable desktop and the network icon appears, (the network is up and running).
I'm timing opening a spreadsheet by selecting Open Office.org spreadsheet from the menu first and starting the stopwatch from when I click on the item in the menu and timing until the blank spreadsheet is open and ready to use.
Then I close it and open another blank spreadsheet and time it again.

Boot-up is taking about 1 min 35 secs
Spreadsheet first time about 9 or 10 seconds
Spreadsheet second time about 4.5 seconds
There is no lag before the icons appear when I mouse over the menus. Only the first time after boot-up it's possible to see that it takes an eye-blink, but after that it's instant, as if they were already there.

Remember, Windows uses a 'Page File', which is like a 'Swap file', so if you think Windows doesn't wear out your flash because it has no swap area, you are mistaken and it's not fair to compare the speed of Ubuntu without any swap area to Windows when it has a page file.

Another difference between Open Source software and proprietary is that Open Source software is polite and it doesn't jump into your RAM at startup like proprietary programs do. That's important in a PC with modest RAM, Open Source software leaves the RAM ready for whatever programs you decide to load. That's why Open Office programs take longer the first time than Windows Spreadsheet, but the second time they're quicker. 
In Windows you have to forcefully delete items from the startup menu or something like that when you want to improve performance. In Linux you don't need to do that, there are no 'tsars'.

---

### Post by kallenes on 2009-04-21
Wow, thanks for running those time tests. Didn't mean all the trouble.

My boot up time from ENTER at the GRUB is 1min 50sec.
Which is fine with me.
And my mouse-over menu openings, app launching, is fine. Quick!

My lag is elsewhere (scrolling and app-switching) .. originally i thought it was video. That's when I added the "uxa" option to xorg.conf - that didn't help much.
Removed some not-needed sessions, etc.

Then I started to think of the swap, and maybe the way I've partitioned the install, and the filesystems eg. ext2 ext3

That's when I needed some expert linux help.

I know what your saying. I couldn't agree with you more about Windows wearing out the flash faster. I know that windows requires a page file, and on a separate partition if possible, and multiple ones if possible. :)
They definately help windows performance.

But, since been new to linux .. I don't know "if a swap partition/file will help in performance? Or as others say - only for hibernation?"

Would you create a swap if you were me?
I don't want to create one if it's not going to improve performance.
If i do create a swap, it will definately be on my flash SDHC card along with /home. I really don't care if it wears out - it's only an 8GB.

Maybe it's what i thought of originally -> Intel 945GSE chipset - video???

Thx again for your time and help.

---

### Post by reis.tiago on 2009-04-21
I have a eeepc 901 and decided to not create a swap partition. I haven't noticed any problems by not having it, never had any major performance problem at least :-)

I don't now exactly if having one will definitly wear out the drive, but since I wasn't able to find any definitive anwser on that subject I prefered not to create one.

---

### Post by Herman on 2009-04-21
Well, I have noticed slowness when there's no swap area in a computer with 512MB of RAM, and then normal performance once a swap area has been created.
I agree with you that you shouldn't need any swap file or swap are if you already have 2 GB of RAM. Probably if you had one, your system wouldn't use it, (unless you decide to hibernate). On the other hand, I'm not sure, if your system is looking for a swap area and can't find one, will that slow the system down?
If so, will turning 'swappiness' to 0 help?
I would need to run some more tests to find out unless someone who already knows for sure can tell us.

I think even with a swap area and file system journalling, our SSD drives and flash memories will last long enough. By the time today's flash memory wears out there will be newer, faster, better technology and we'll want to upgrade anyway. I think, let's enjoy it and use it for best performance, if it wears out some day, buy new. That's only my opinion.

It sounds like your performance is not too bad.
I thought you might have been experiencing 'SSD Stuttering', as explained here, [The SSD Anthology: Understanding SSDs and New Drives from OCZ]("http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=1").

I have been reading up on SSD drives and file system performance. I have a USB flash memory stick and I decided to reset its partition table with 224 heads and 56 sectors per track and make the first partition start in sector number 2048 instead of the traditional 63. The ideas behind these ideas are described in this blog, [Aligning Files Systems with SSDs Erase Block Size]("http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/").

 Then I installed Ubuntu Jaunty Jackalope in it two times, once with Ext4 and again with ReiserFS, to try to compare those two file systems and see which is faster.
The flash memory stick I used is the slowest flash memory stick in my collection. It would not be any surprise if installing Ubuntu with an ext3 file system in this particular USB flash memory would take as long a 2 hours and ten minutes.

Following are the results
1. Using Ext4
```
sudo fdisk /dev/sdd
``````
x        (enter expert mode)
H 224    , change the heads to 244
S 56     , change the sectors to 56
``````
n  (create a new partition)
p  (make it  a primary partition)
1  (make it partition number10
1  (make it start after the first track)
1020 (make it end at cylinder 1020
``````
x  (enter expert mode)
b  (move beginning of data in a partition
2048
p
w
``````
mke2fs -t ext4 -E stripe-width=32,resize=500G /dev/sdd1

```Installation time for Ubuntu Jaunty Jackalope Beta from the 'Desktop' Live CD
in the LEC computer was 1 hour and 33 minutes. The first stage took about eight minutes of the 93 total.

Roughly 3 minutes and fifteen seconds to boot up but I made a mistake and didn't start the timer right away.

Two minutes, thirty-nine seconds to open an OOo spreadsheet for the first time
only 9 seconds the subsequent time

Second boot-up was timed more carefully, and it took 3 minutes and thirty-six seconds
Two minutes, thirty-six seconds to open an OOo spreadsheet for the first time
only 8 seconds the subsequent time
====================================================================================

2. Using ReiserFS
Installation time for Ubuntu Jaunty Jackalope Beta from the 'Desktop' Live CD
in the LEC computer was 1 hour and 29 minutes. The first stage took about 11 minutes of the 89 total.

More than 5 minutes and 21 seconds to boot up for the first time. (What went wrong?)

Three minutes, fifty-one seconds to open an OOo spreadsheet for the first time
only 6 seconds the subsequent time

Second boot-up was timed more carefully, and it took 3 minutes and twenty seconds
One minutes, fifty seconds to open an OOo spreadsheet for the first time
only 5.5 seconds the subsequent time

Third boot-up was 3 minutes, 33 seconds
open a spreadsheet: 1 minute, 46 seconds
only 5.5 seconds the subsequent time
====================================================================================
Conclusion: Ext4 and ReiserFS are pretty close, more testing would be necessary, and should be done more carefully too, (not in a hurry).

Later I want to just time a regular ext3 install to check how long it really takes to install normally, with a disc geometry.

---

