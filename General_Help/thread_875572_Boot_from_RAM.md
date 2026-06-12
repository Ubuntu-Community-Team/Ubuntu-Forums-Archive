---
title: "Boot from RAM?"
date: 2008-07-31
forum: General Help
---

### Post by blackbinary on 2008-07-31
I want the boot process to be very swift in ubuntu. I have 3GB of ram, so I thought I could do this. I do play many games, so the optimal setup for me would be that when i boot the computer, it reads from the ram instead of from HDD, thus making the boot very quick. Once the computer has loaded (automatic login on), it releases this information to the HDD, clearing up the ram for other uses. 

Also, I would like to be able to dedicate ram to a certain application (in this case a game), would I be able to do either of these things, and could someone point me in the direction of a how-to, or explain it here? I am fairly new to Ubuntu, so many complicated things may go over my head. 


Thanks, i appreciate any help.

---

### Post by tamoneya on 2008-07-31
you cant store data on RAM when the computer is off so that means that you cant boot from RAM since just 1 second ago the power was off.

Sorry.

---

### Post by lisati on 2008-07-31
I agree that booting from RAM is likely to be problematical/impossible. Another possibility that comes to mind is to use a USB memory stick, which might be a more practical option to explore.

---

### Post by tamoneya on 2008-07-31
> **lisati said:**
> I agree that booting from RAM is likely to be problematical/impossible. Another possibility that comes to mind is to use a USB memory stick, which might be a more practical option to explore.

Thats a decent idea.  Also its pretty simple to do.  Just partition it and put /boot on the USB drive.  Also when you add to fstab you should make sure to add with the UUID instead of with the device node.

---

### Post by blackbinary on 2008-07-31
Oh sure, it can't be saved to the ram, but if I understand it correctly, wehn the OS boots, it is reading info from the HDD, I assumed this was a large amount, but it may very likely be transfering it straight to ram anyways, in which case there isnt much i can do. What about for dedicating ram to a specific application?

---

### Post by tamoneya on 2008-07-31
> **blackbinary said:**
> Oh sure, it can't be saved to the ram, but if I understand it correctly, wehn the OS boots, it is reading info from the HDD, I assumed this was a large amount, but it may very likely be transfering it straight to ram anyways, in which case there isnt much i can do. What about for dedicating ram to a specific application?

In order to dedicate ram to specific applications you could make a RAM disk.  You can then mount it to your filesystem and put whatever you want on it.  

[http://ubuntuforums.org/showthread.php?t=89490](http://ubuntuforums.org/showthread.php?t=89490)

---

### Post by kgk on 2008-07-31
> **blackbinary said:**
> I want the boot process to be very swift in ubuntu. I have 3GB of ram, so I thought I could do this. I do play many games, so the optimal setup for me would be that when i boot the computer, it reads from the ram instead of from HDD, thus making the boot very quick. Once the computer has loaded (automatic login on), it releases this information to the HDD, clearing up the ram for other uses. 

Also, I would like to be able to dedicate ram to a certain application (in this case a game), would I be able to do either of these things, and could someone point me in the direction of a how-to, or explain it here? I am fairly new to Ubuntu, so many complicated things may go over my head. 


Thanks, i appreciate any help.

RAM memory is only able to store data when there is a current flowing through it.  Therefore, when you turn off your computer, all the information on the RAM is lost. (Part of the reason it takes a minute or longer to boot OSes on average computers).

All RAM currently used by mainstream computers is "volatile", meaning data is stored as electric charge or current flows.  Once the juice is shut off, everything is lost.

What you're asking requires MRAM, which is ridiculously expensive and still under development.


Now what I think you're asking is 2 things:

1.  A way to quicken your boot times

2.  A way to manually assign RAM space to applications



1.  What you're likely going to want in that case is a Solid State Disk.  They are relatively new and still somewhat expensive, but OCZ and other manufacturers have come down in price quite a bit recently.  You can purchase a small (~32GB) SSD to run the Operating System and main applications from and then a larger traditional hard drive to store media, large data, etc.

The seek time on SSDs is fractions of seconds, so that will likely get you as close to an "instant on" scenario as you want.

Or if you don't want to spend the money on an SSD, you can boot from a USB thumb drive.  But you'll want to find one that has quick access times, and they are usually quite a bit more expensive than your run of the mill usb sticks.

2.  Don't.  The operating system assigns RAM to various applications as needed, and with 3GB, you'll likely never run into an issue where you're maxing that out.  Unless there's some glitch with a particular piece of software and it isn't being allocated enough RAM (rare), just ignore that idea alltogether.  Most applications are perfectly capable of telling the OS how much RAM they need.

---

### Post by blackbinary on 2008-07-31
thanks tamoneya!

As for your post kgk, if you read above i realize that information can't be stored in the ram because it requires power to store information. What I was thinking is that ubuntu normally reads more then is optimal from the disk, where this info could be put onto the ram when booting because of the quantity I have. 

I am not particular with an 'instant-on' scenario as you suggest, nor do I plan on paying such amount of money for an SSD. I was just thinking of how best to take advantage of the amount of memory I have. 

As for your USB idea, I doubt that will really work, since USB is capped at 480mbps, where-as a harddrive is not. Even with flash memory having faster seek times, it is still bottlenecked by the interface. 

In regard to assigning ram to an application, there are a few cases where ram isn't optimally used. This happened to me when i was running windows too. In this case, 512 was the maximum this application was assigned. Which, when the rest is using 128ish, really isn't right. 
Also, photoshop for example uses scratchdisks, among other things this controls how many 'undo' commands you can make. While photoshop itself can only use 2GB of ram, the scratchdisk can be assigned as much as you like. By default this 2gb of ram includes the scratchdisk, limiting how big it may be. This means if I want a large scratchdisk, I will suffer performance wise because PS has less memory to work with. Hence allowing it to use more memory, or storing the scratchdisk elsewhere are my options.

Perhaps an alternative for boot times is to cut down on what is loaded on boot. For example, I know ubuntu when booting spits out errors about fd0, which is the floppy drive, a device I do not have installed. If I could stop it for checking for this, it would boot a few seconds faster. There are other services I am sure I do not need right at start up, and it would be nice to resign these services to only startup when needed. 

Again thanks for the help thus-far, and any help to come!

---

### Post by jocko on 2008-07-31
> **blackbinary said:**
> What I was thinking is that ubuntu normally reads more then is optimal from the disk, where this info could be put onto the ram when booting because of the quantity I have.

So instead of reading it directly from the disk to ram, you want it to read it from the disk to a ramdisk and then from the ramdisk to ram?
Won't that just add an unnecessary step? Perhaps not, if reading to the ramdisk is quicker than the sum of the disk reading that happens on a normal boot...

There is this [tutorial on the wiki]("https://wiki.ubuntu.com/BootToRAM") and this [thread in the forums]("http://ubuntuforums.org/showthread.php?t=432961&highlight=ramdisk+boot") that may help you to do what you want.
Edit: the tutorial describes how to load a live session from a hard disk to ram, but I see no reason why it should not be possible to set it to mount a real /home partition to make it more persistent (no idea how, though. and it's probably not possible to install new packages that will stay installed across boots.).

---

### Post by tamoneya on 2008-07-31
> **jocko said:**
> So instead of reading it directly from the disk to ram, you want it to read it from the disk to a ramdisk and then from the ramdisk to ram?
Won't that just add an unnecessary step? Perhaps not, if reading to the ramdisk is quicker than the sum of the disk reading that happens on a normal boot...

There is this [tutorial on the wiki]("https://wiki.ubuntu.com/BootToRAM") and this [thread in the forums]("http://ubuntuforums.org/showthread.php?t=432961&highlight=ramdisk+boot") that may help you to do what you want.
Edit: the tutorial describes how to load a live session from a hard disk to ram, but I see no reason why it should not be possible to set it to mount a real /home partition to make it more persistent (no idea how, though. and it's probably not possible to install new packages that will stay installed across boots.).

My ram disk idea was intended to be separate from the boot time stuff.  I was thinking that you would use the ram disk during normal operation of the computer.

---

### Post by LowSky on 2008-07-31
Why not use Hibernate? It boots quicker than a normal shutdown.

But so you know Gigabyte makes a RAM hard Drive, that run on battery power, kinda like how CMOS works, all you need is to supply the RAM
[http://www.radioshack.com/product/index.jsp?productId=2459400](http://www.radioshack.com/product/index.jsp?productId=2459400)
[http://www.tomshardware.com/reviews/gigabyte,1111.html](http://www.tomshardware.com/reviews/gigabyte,1111.html)

---

### Post by hessiess on 2008-07-31
try a distro like arch or gentoo, becouse you can set everything up yourself, you only load what is absolutly nesoserry which mackes booting faster

---

