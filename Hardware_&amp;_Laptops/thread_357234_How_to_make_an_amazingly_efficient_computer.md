---
title: "How to make an amazingly efficient computer"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by CheshireMac on 2007-02-09
Hey folks. I'm trying to make my own, customized machine . . .and it needs to be lightning fast. I've been thinking about alternate storage methods, and I want to know if I can put Ubuntu, or maybe Xubuntu on a small flash drive . . .maybe a 2gb SD card? That would free up an intense amount of memory, would it not?
 
I could mount it as it's own drive and use my other two as stand-alone storage, no?

---

### Post by Haegin on 2007-02-09
If you want a lightning fast machine go with something really light on the window manager side (fluxbox, icewm etc) or just cli for the most speed. Use dash as the shell and mingetty for logins. Run as little as possible and run it all on the best hardware possible. 
Hard drive wise I think either a usb 2 flash card or a sata 2 (aka sata 300) drive or possibly a western digital raptor which claims to be the fastest sata drive available (even though it is only sata 1 ([http://www.wdc.com/en/products/products.asp?driveid=189&language=en)](http://www.wdc.com/en/products/products.asp?driveid=189&language=en)).
Add in ludicrous amounts of RAM and a dual (or quad!) core CPU and you have a pretty fast system.
Then turn on stuff like preloading and hdparm and all those other performance tweaks and you should be running pretty hot.
Finally grab a dvorak keyboard and learn to type faster and reduce the only limiting factor left - you.
Also if you can get the swap on a really fast hard drive then you would boost system performance but when I ran fluxbox (v lightweight) i never used more than 200mb ram out of a gig so you could probably do away with swap given enough ram.

---

### Post by Redeyes_Gambit on 2007-02-09
One thing you should make note of is that if you install to a USB flash medium that your BIOS must support booting to a USB device! Also, from what I have read/tried, getting Ubuntu to install to a USB flash drive is a pretty painful process.

If you are really gung-ho on installing to flash, I would recommend using Compact Flash for two reasons. One, compact flash (I believe) has the fastest transfer speeds of all the flash memory. Two, CF is just about pin compatible with an IDE header so you can grab one of these cool gizmos: [http://www.mini-box.com/s.nl/sc.8/category.14/.f](http://www.mini-box.com/s.nl/sc.8/category.14/.f) and make your CF look like a real (non USB) HDD to your BIOS and Ubuntu, thus eliminating A LOT of headaches.

Another thing you should know about installing to flash memory; Though flash has a lower seek-time (the time it takes for a storage device to find the data being requested) flash has a MUCH lower sustained transfer rate than a HDD. So, having an OS installed to flash *would* be cool because it would decrease load/access times, if you will be doing something that requires a heavy sustained transfer rate (such as video editing/encoding) a hard drive would be preferred.

One last idea, why not run from the RAM completely? This will give you the utmost, absolute fastest possible transfer rates/sustained speed. The drawback of course is that RAM is volatile, meaning you turn off your computer and all data on the RAM is toast. A UPS (Un-interruptible Power Supply, basically a big battery) would be absolutely necessary. Also, you would have to have a LOT of RAM. 4 Gigs probably. Two or three would be a RAM disk that you would install (*)Ubuntu to, and the other 1 gig would have to be system memory. Also, you could never upgrade your kernel since that requires a restart. Just an idea, and an inconvenient one at that, but an idea none the less.

---

### Post by tht00 on 2007-02-09
> **CheshireMac said:**
> Hey folks. I'm trying to make my own, customized machine . . .and it needs to be lightning fast. I've been thinking about alternate storage methods, and I want to know if I can put Ubuntu, or maybe Xubuntu on a small flash drive . . .maybe a 2gb SD card? That would free up an intense amount of memory, would it not?
 
I could mount it as it's own drive and use my other two as stand-alone storage, no?

I would stay away from booting from flash.  First off, I'm not sure if it is that much faster than a hard disk.  Also, it seems you have a preconception that the more disk space you have (more 'memory'), the faster it will be. The term 'memory' in computers is usually used very generically and can be attributed to a number of different systems.  Don't get hung up on 'memory'.

Second, the hard disk is only accessed when reading or writing data.  Mostly, you see reading when booting and loading programs.  Once programs are open, they don't use the hard drive unless opening or saving data.  So, for example, with a resource intensive game, the only advantage you'd get in having a faster storage medium is with loading.  Once the game is loaded, there won't be any difference whether you're running it from the slowest or fastest disk drive (unless swap space is used).

In the case of swap space, it's really best to avoid using it at all.  Swap space (virtual memory) is essentially RAM that is on the hard drive.  Compared to RAM, it is extremely slow.  It can help if you don't have much RAM or if an application 'runs away'.  I'm running Ubuntu on 1GB of ram with absolutely no trouble and without having the need to use the swap space.

One last thing would be that flash will wear out after repeated writes (hard drives will too, but from what I understand, not nearly as quickly).

So really, if you want an 'efficient' computer, I'd say you should focus on 1) a good processor, 2) enough RAM, 3) a decent HDD, and 4) a video card (even basic) -- frees up some CPU time.

---

### Post by Haegin on 2007-02-09
[quote=Redeyes_Gambit]
One last idea, why not run from the RAM completely? This will give you the utmost, absolute fastest possible transfer rates/sustained speed. The drawback of course is that RAM is volatile, meaning you turn off your computer and all data on the RAM is toast. A UPS (Un-interruptible Power Supply, basically a big battery) would be absolutely necessary. Also, you would have to have a LOT of RAM. 4 Gigs probably. Two or three would be a RAM disk that you would install (*)Ubuntu to, and the other 1 gig would have to be system memory. Also, you could never upgrade your kernel since that requires a restart. Just an idea, and an inconvenient one at that, but an idea none the less.
[/quote]

I am sure that with some effort you could get a system that boots to the ram and runs in the ram and then when it shuts down it writes the disk image back to a normal hard drive - this would need lots of ram still and would be slower to shutdown and boot up (you need to write several gigs of data when you shutdown though this could be reduced if you kept your docs on a normal drive) but it would be much faster to run.

Depends on how lazy you are I guess - fast hardware and a stripped down install is gonna give you a good performance increase and that may be enough for you.

---

### Post by Redeyes_Gambit on 2007-02-09
Yea, having a persistent auto backup of the RAM disk at shutdown would take care of the whole volatile problem. I just figured this would be too much of a hassle as you would probably have to modify your init.d yes? Yea, too much of a hassle I agree. A stripped down install would be easier.

---

### Post by CheshireMac on 2007-02-09
> **tht00 said:**
> I would stay away from booting from flash. First off, I'm not sure if it is that much faster than a hard disk. Also, it seems you have a preconception that the more disk space you have (more 'memory'), the faster it will be. The term 'memory' in computers is usually used very generically and can be attributed to a number of different systems. Don't get hung up on 'memory'.
 
Second, the hard disk is only accessed when reading or writing data. Mostly, you see reading when booting and loading programs. Once programs are open, they don't use the hard drive unless opening or saving data. So, for example, with a resource intensive game, the only advantage you'd get in having a faster storage medium is with loading. Once the game is loaded, there won't be any difference whether you're running it from the slowest or fastest disk drive (unless swap space is used).
 
In the case of swap space, it's really best to avoid using it at all. Swap space (virtual memory) is essentially RAM that is on the hard drive. Compared to RAM, it is extremely slow. It can help if you don't have much RAM or if an application 'runs away'. I'm running Ubuntu on 1GB of ram with absolutely no trouble and without having the need to use the swap space.
 
One last thing would be that flash will wear out after repeated writes (hard drives will too, but from what I understand, not nearly as quickly).
 
So really, if you want an 'efficient' computer, I'd say you should focus on 1) a good processor, 2) enough RAM, 3) a decent HDD, and 4) a video card (even basic) -- frees up some CPU time.
 
Okay . . . I understand the difference between Read Only and Random Access . . .my issue is not in terminology. Here's what I'm saying : I don't care which medium I store the install on. I'm looking to find which has the best fidelity, and which has the fastest seek times . . .and a happy medium between the two. Another thought I had was storing the install on whatever memory, and doing manual upgrades through a back up, and then transferring the upgraded version to the install . . .I doubt that it would work, but is there a possibility? 
Also, the idea I'm running with here in general is separation of OS from everything else . . .Maybe just a very small HD with nothing else on it . . .argh!! there are so many ways to arrange a computer. ~LOL~

---

### Post by Redeyes_Gambit on 2007-02-09
> **CheshireMac said:**
>  . . .argh!! there are so many ways to arrange a computer. ~LOL~

LOL, that there is. Personally, I think a CF with the flash to IDE converter would be the best blend between easy-ness (no extraneous software configuration, no need to get used to a new window manager etc) and speed (high random access speeds, despite low sustained transfer speeds) but if you have no problem switching to an alternative window manager that is also a pretty good option as it will give you speed benefits without needing to buy any extra hardware.


As for upgrading via a backup, yea it might be possible. seems like it would work anyway. But, if the whole point is speed do you really want to have to backup the whole OS, upgrade the backup, then move the OS back to memory? Seems like one big pitstop unfortunately.

---

### Post by Redeyes_Gambit on 2007-02-09
Oh, and as for the whole limited number of writes thing brought up by the quite correct tht00, yes this is true. Flash memory can only withstand a limited number of writes, however according to wikipedia:

"...(most commercially available flash products are guaranteed to withstand 1 million programming cycles)." 

And that...

"This (limited number of writes) effect is partially offset by some chip firmware or file system drivers by counting the writes and dynamically remapping the blocks in order to spread the write operations between the sectors. This technique is called wear levelling. Another mechanism is to perform write verification and remapping to spare sectors in case of write failure, which is named Bad Block Management (BBM)."

So, the question is will you stress the flash memory hard enough to where it will write over the same sector 1,000,000 times? And, how does this compare to a hard drive which has many moving parts which wear themselves? I personally don't have an answer.

---

### Post by CheshireMac on 2007-02-09
> **Redeyes_Gambit said:**
> LOL, that there is. Personally, I think a CF with the flash to IDE converter would be the best blend between easy-ness (no extraneous software configuration, no need to get used to a new window manager etc) and speed (high random access speeds, despite low sustained transfer speeds) but if you have no problem switching to an alternative window manager that is also a pretty good option as it will give you speed benefits without needing to buy any extra hardware.
 
 
As for upgrading via a backup, yea it might be possible. seems like it would work anyway. But, if the whole point is speed do you really want to have to backup the whole OS, upgrade the backup, then move the OS back to memory? Seems like one big pitstop unfortunately.
Just doing some reading . . .holographic discs seem pretty promising . . .3.9TB in a CD!!! Now if only it didn't seem like such a waste of space . . .and the reader is $15,000 ...that's a new VW for me. ~LOL~ But I can imagine a time in the near future when gaming and OSs are so dynamic and interactive that the TB will replace the GB as the common acronym for disc space . . . and the GB will replace the MB for RAM. Til then, it's still just 3D and Old-School Windows concepts. Can't wait for VR to take hold as a perfected science/art. Imagine if your monitor looked like goggles and your interface was controlled by gloves . . .invisible keyboards, REAL point&click, REAL drag&drop . . .and instead of just Windows, you could have a whole HOUSE! 
I have a concept of future computing that turns the internet, gaming, OS operation, and communications into one single environment . . .It's a slowly developing concept, but I am looking for anyone that wants to join in discussions . . .my email's available in my profile, and I think this could be a cool idea to develop in a community-style discussion. 
But I digress . . . I think that the best option for my query would be a very small HD, only storing the OS install . . .and mount all my other devices along side it. Also, mentioned above was the swap being RAM in a hard disc . . .is that universally true? My reason for asking is that I thought of a slightly larger HD being used for install, and OS memory, and leave the rest of the RAM for apps, internet, etc.

---

### Post by nihilocrat on 2007-02-14
> **CheshireMac said:**
> Also, mentioned above was the swap being RAM in a hard disc . . .is that universally true? My reason for asking is that I thought of a slightly larger HD being used for install, and OS memory, and leave the rest of the RAM for apps, internet, etc.

Yes, that's basically true. When your system runs out of RAM it will start writing to your swap space. The swap space is set aside so that when it has to do that, it has its own partition so it can be done as quickly as possible. It's usually a good idea (and easy, considering the amount of RAM we have on systems these days) to just avoid using so much memory that the OS starts writing to swap. You can see memory statistics (in megabytes) with:
```
free -m
```
Which should be fairly easy to understand.

I would suggest installing a server distro of Ubuntu and then building up a desktop, piece-by-piece, with apps that take up as little space as possible. 2 GB should be plenty to get this done. I was able to fit a Debian install with fluxbox and a few apps on a 500 meg harddrive a few years ago, so you should have plenty of space for apps and such. Of course, you'd want to store all of your 'heavy' data (media, namely) on a 'real' harddrive, probably mounted as /home. I also agree with everyone else that using a flash-to-IDE adapter thing would be a good idea.

---

### Post by CheshireMac on 2007-02-14
> **nihilocrat said:**
> Yes, that's basically true. When your system runs out of RAM it will start writing to your swap space. The swap space is set aside so that when it has to do that, it has its own partition so it can be done as quickly as possible. It's usually a good idea (and easy, considering the amount of RAM we have on systems these days) to just avoid using so much memory that the OS starts writing to swap. You can see memory statistics (in megabytes) with:
```
free -m
```Which should be fairly easy to understand.

I would suggest installing a server distro of Ubuntu and then building up a desktop, piece-by-piece, with apps that take up as little space as possible. 2 GB should be plenty to get this done. I was able to fit a Debian install with fluxbox and a few apps on a 500 meg harddrive a few years ago, so you should have plenty of space for apps and such. Of course, you'd want to store all of your 'heavy' data (media, namely) on a 'real' harddrive, probably mounted as /home. I also agree with everyone else that using a flash-to-IDE adapter thing would be a good idea.
Two questions from this: 1)Is the swap space volatile? 2)Are you suggesting Server editions because they are stripped down or another reason?

---

### Post by link141 on 2007-02-14
[quote=CheshireMac]1)Is the swap space volatile?[/quote]

The answer is, no.  Because swap is usually on a nonvolatile harddrive, the data isn't lost when you turn it off.  **However**, I think the system usually clears the swap data on boot/shutdown to make room for future sessions.  What did you have in mind with the swap?

> 2)Are you suggesting Server editions because they are stripped down or another reason?

Yes.  I think the server edition doesn't have a desktop environment (and many other applications) installed by default because it would cause too much overhead and bloat, when you want it to just be a server, and for it perform fast.  Installing the server edition would give you a chance to build your desktop from the ground up, with only the applications you want, to make your computer run as fast as possible. 

hope this helped,
cheers

---

### Post by zero-9376 on 2007-02-14
dont know if this has been mentioned yet but you could get a gigabyte i-ram which sits in a pci slot takes upto 4gb of ddr and looks like a sata drive to the computer. Also uses battery to preserve data (apparently it can still be corrupted so might look at regular backups), run the os off that and store everything on other drives, pretty sure this is what people use when trying to set benchmark records.

---

### Post by KAL9000 on 2007-02-14
Swap files (within windows atleast) are used to keep a certain % of system memory free so when you run an application it doesnt need to crapitself trying to write it all to the disk before it opens what app you need.

Having 1 HDD with seveal small partitions on it is just as slow as 1 huge one. the only way you will see a speed again from apps on one partition and the OS on annother is if those are on seperate physical disks.

Basic rule. Multiplying partitions on a physical drive devides its read/write speed if you try to read from them all.
Multiplying Physical hard disks multiplies your read/write speeds when accessing them all.

If you want speed Get a raid controler and stripe two WD raptors. install the OS on that. then get two more and use that for your apps :P

shame on Ebuyer they are £90 a piece.

When you say efficent I assumeyou mean something with a few bottle necks as possible. well in most desktop systems the HDD seek/read time is the main slow down.

---

### Post by benow on 2007-02-17
You could run it in a 4G iRAM:

[http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2180&ProductName=GC-RAMDISK](http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2180&ProductName=GC-RAMDISK)

---

