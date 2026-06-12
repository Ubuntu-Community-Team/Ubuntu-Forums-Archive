---
title: "Hard Drive Cloning"
date: 2009-05-19
forum: Hardware
---

### Post by emeraldgirl08 on 2009-05-19
I have an older laptop that came with a very slow 4200 rpm Hard Drive. It's a 40 gb and I have XP Pro and Intrepid dual boot on this girl. A friend of mine sent me an 80 gb 5400 HD so now I have a couple of questions.

Is an external drive enclosure for the new HD an absolute necessity? I have one but found out it was for an 3.5 HD. I'll just save that for a storage unit. 

I *have* read a couple of threads and there have been some that suggested a specific sequence of installs. Like installing Windows first, Ubuntu second, fat32 third, or something like that. I don't remember the specifics. I just want the better performance badly. The 4200 rmp HD is a drag!!! I am glad there is going to be bigger storage available w/ the new 80gig but would like the partition so I can optimize it :)

I also have a question about a recovery and OS partition that is installed on my T30 HD. I wasn't shipped any discs along with my laptop. I was wondering if I could clone the Windows and Recovery first- then instead of Intrepid install Jaunty??? If anyone could help me out with these questions I'd appreciate it!

---

### Post by wannadumpwindows on 2009-05-19
For your first question, an external enclosure is not necessary. Just a good idea to protect the drive.

And as far as installing goes, it's usually easier to install Windows first. If you install Ubuntu first, it's most likely going to get wiped out when you try to install Windows alongside it, and then you'll just have to do it all over again.

And you'll most likely instantly notice the performance difference of the two drives. I just upgraded my laptop from an 80 Gb 5400 rpm to a 320 Gb 7200 rpm drive and I'll never look back. It was money WELL spent!

P.S. You might have a look at this thread to get started on cloning your drive, there's not much to it. There are also tons of other resources on the web that will suit you.

Link:
[http://ubuntuforums.org/showthread.php?t=135172]("http://ubuntuforums.org/showthread.php?t=135172")

---

### Post by emeraldgirl08 on 2009-05-19
Thanks for the link!

Unfortunately I want to keep Windows XP Pro. I have an Dell Axim x51v that I use Activesync with. I also prefer the option of just switching over from one OS to the other.

I also did not have my question answered about having NO OS OR RECOVERY DISCS. I just want to clone the Windows XP and recovery partition of my Thinkpad HD first. That's my main concern.

---

### Post by wannadumpwindows on 2009-05-19
The information in that thread will allow you to keep everything you currently have, exactly as is, it will just move it all to the new hard drive. Once you clone the windows install to the new drive, you can upgrade to or install any version of Ubuntu that you please.

As for your other question, I'm guessing you didn't buy recovery discs, or use the utility on your computer to create them. That's how most of them work today. You pay extra for the discs, that's why you have a recovery partition.

P.S. The link in the first post answered your question exactly as far as I can tell. Just because it says Ubuntu, you can use it to clone any partition.

---

### Post by sedawk on 2009-05-19
Have a look at the tool partimage, it can be used to clone
whole partitions and move the data to bigger partitions (on another disk).
You should be able to copy all data from the old disk to the
new disk and enlarge partitions as needed.
Keep in mind to copy also the MBR (once), so booting the
new drive should work.

If you do not have a third disk big enough to store the partition
images you might need (temporarily) a small USB-HDD enclosure to
connect your new drive first in parallel.
(I'm not sure partimage can do a "direct copy" so some extra
 throughs might be needed about where and how to store the
 partitions images ...).

---

### Post by emeraldgirl08 on 2009-05-19
> **sedawk said:**
> Have a look at the tool partimage, it can be used to clone
whole partitions and move the data to bigger partitions (on another disk).
You should be able to copy all data from the old disk to the
new disk and enlarge partitions as needed.
Keep in mind to copy also the MBR (once), so booting the
new drive should work.

If you do not have a third disk big enough to store the partition
images you might need (temporarily) a small USB-HDD enclosure to
connect your new drive first in parallel.
(I'm not sure partimage can do a "direct copy" so some extra
 throughs might be needed about where and how to store the
 partitions images ...).
You use Partimage often? I have a cloning program on Windows called HDClone. I've never done this before and you guys are my advisors on this!

It doesn't matter which OS-based Cloning program I use???

I also forgot the command to view partitions in terminal. If anyone could help I'll buy you a beer :)

---

### Post by wannadumpwindows on 2009-05-19
As long as the cloning program you want to use supports the file systems that you need to clone, you should be able to use anything that you want.

And I'm guessing the command you're looking for is:

```
sudo fdisk -l
```

---

### Post by emeraldgirl08 on 2009-05-19
> **wannadumpwindows said:**
> As long as the cloning program you want to use supports the file systems that you need to clone, you should be able to use anything that you want.

Thanks guys. I'm going to read up on Partimage.

---

### Post by louieb on 2009-05-19
Just replaced the 40 GB 4200 rpm drive in my T30 with a 160GB 5400 rpm drive. What I did was put the new drive in a USB enclosure. Then booted the PC with a  [SystemRescueCd  ]("http://www.sysresccd.org/Main_Page") and used Gparted to copy the partitions one by one to the new drive.  Then changed the MBR to load Ubuntu's GRUB.  

Shut the PC down, replaced the old drive with the new. Boot it and everything worked, Including XP  (XP ran checkdisk the 1st time it booted, but other than that the new drive works just like the old - only faster.

---

### Post by emeraldgirl08 on 2009-05-19
> **louieb said:**
> Just replaced the 40 GB 4200 rpm drive in my T30 with a 160GB 5400 rpm drive. What I did was put the new drive in a USB enclosure. Then booted the PC with a  [SystemRescueCd  ]("http://www.sysresccd.org/Main_Page") and used Gparted to copy the partitions one by one to the new drive.  Then changed the MBR to load Ubuntu's GRUB.  

Shut the PC down, replaced the old drive with the new. Boot it and everything worked, Including XP  (XP ran checkdisk the 1st time it booted, but other that that the new drive works just like the old - only faster.

	\\:D/

Thank you SO MUCH!!! I'm glad I've met someone here who has a T30! I know it's not the most desirable laptop but it was sold to me for a good price and Thinkpads are tanks :)

Okay. It's starting to look like I'll need to buy an 2.0 USB HD enclosure. I was thinking of getting an Ultrabay HD adapter but we'll see which is cheaper! Money is tight these days!

Seeing as I don't have an extra enclosure lying around I'm guessing the enclosure or 2nd HD Adapter is a necessity right???

---

### Post by logos34 on 2009-05-19
Partimage is great--I use it all the time.  But it's not really the best choice in this case, IMHO: it does partitions only, not entire drive, and can't do direct disk-to-disk copies. You need to save the image to a separate partition, then restore from that.

The easiest way your case, I believe, is to use the [COPY function on the **Gparted Live CD**. ]("http://gparted.sourceforge.net/larry/move/move.htm")(direct copy, one disk to a another).  Has a nice, easy to understand gui.  

Install grub bootloader to MBR on new drive (link below).  

Done.

---

### Post by louieb on 2009-05-19
Your Welcome. 

When you get the USB enclosure or caddy. Remember they come in two types. One is for a **IDE / PATA  **drive, the other is for a sata drive. Make sure the one you get is for **IDE / PATA**   There not to expensive, either can be found on eBay for about $10.

---

### Post by emeraldgirl08 on 2009-05-19
Okay guys. I read something about ext4 or something like that for faster loading and performance. What is this all about and how do I partition it in this way??? I'm going into town tonight so I'm checking on external USB cases for sure!!!

I'll be back on late this PM. 

Danke!

---

### Post by logos34 on 2009-05-19
> **emeraldgirl08 said:**
> I read something about ext4 or something like that for faster loading and performance. What is this all about and how do I partition it in this way???

A lot of the info on ext4 is either extremely technical or long-winded.  Here's thumbnail sketch:

> [Support for the EXT4 filesystem]("http://inportb.com/2009/01/15/ubuntuext4-boots-in-214-seconds/") started appearing in the Ubuntu 9.04 daily development images just a few days ago, and early adopters have been experiencing the speed and efficiency of this new format. Compared to EXT3, EXT4 shows marked performance improvements and pulled far ahead of the competition in many respects. Phoronix&#8217;s article on Ubuntu&#8217;s EXT4 support contains some technical benchmarks.

But what does this mean for us regular users? For one, we&#8217;ll now be able to store gargantuan files on the scale 16TB. While that feature would not be useful to most users, the faster read/write speeds would allow most applications to start and work faster. In particular, Softpedia reports a noticeable boot time improvement of 9 seconds, yielding a 21.4-second boot. While this may not seem very much, let&#8217;s remember that Ubuntu and the EXT4 module are still full of debugging code. Once that&#8217;s gone and everything else is stabilized, the system would work even better.



Ext4 info and FAQ

[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)
[http://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions](http://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions)


Some ext4 issues/bugs you should be aware of (might have been fixed in one of the updates already):

[http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems](http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems)
[http://www.ubuntu.com/getubuntu/releasenotes/904#Switching%20to%20ext4%20requires%20manually%20updating%20grub](http://www.ubuntu.com/getubuntu/releasenotes/904#Switching%20to%20ext4%20requires%20manually%20updating%20grub)
[http://www.ubuntu.com/getubuntu/releasenotes/904#Possible%20data-loss%20problems%20resizing%20ext4](http://www.ubuntu.com/getubuntu/releasenotes/904#Possible%20data-loss%20problems%20resizing%20ext4)

You can also convert an existing ext3 installation to ext4, but if you're thinking of this:

> I was wondering if I could clone the Windows and Recovery first- then instead of Intrepid install Jaunty

I'd just do a fresh install of 9.04 and manually partition with ext4 /.  I think only experienced users should attempt conversion at this point.

---

### Post by emeraldgirl08 on 2009-05-20
Okay. I ordered an HD enclosure from fleabay. It should be here by Friday. In the meantime I have a question on the size of partitions and what recommendations people have.

I have around 17gb on XP Pro, 17gb on Intrepid, and the rest is Grub recovery and extended stuff. 

It is a 40 gb HD.

I'm on Windows right now so I can't access terminal. I did notice on Grub boot-up there are three different versions of Intrepid. I'm assuming after certain updates there is a new boot choice??? I've been using the first one on the list which is the newest (I think).

The HD I'm going to use is an 80 gb. From what I understand I can clone the Ibex partition to the new one- can I decrease the size? I'd like to think that 10gb would be enough. Windows could use a small shrinking to about 15 gb. That leaves me 50 gb of storage I'd like to share between Windows and Ibex. The rest is for the IBM Rescue and Recovery portion.

I read somewhere something about a FAT32 partition that Windows and Ibex could share. Is it easy to set it up this way?

---

### Post by logos34 on 2009-05-20
> **emeraldgirl08 said:**
> I did notice on Grub boot-up there are three different versions of Intrepid. I'm assuming after certain updates there is a new boot choice??? I've been using the first one on the list which is the newest (I think).

Those are your kernel updates.  By default it keeps the previous versions. They don't take up much room, but you can remove the oldest if you want. (Or just remove the entry from /boot/grub/menu.lst).  It is recommended to keep the next most recent as a backup.  

> The HD I'm going to use is an 80 gb. From what I understand I can clone the Ibex partition to the new one- can I decrease the size? I'd like to think that 10gb would be enough. Windows could use a small shrinking to about 15 gb. That leaves me 50 gb of storage I'd like to share between Windows and Ibex. The rest is for the IBM Rescue and Recovery portion.

Sure.  Simply use Gparted on the ubuntu live cd to shrink them down first, then clone. Or shrink them afterward, doesn't really matter.
> 
I read somewhere something about a FAT32 partition that Windows and Ibex could share. Is it easy to set it up this way?

No longer necessary.  Ubuntu can read and write to NTFS (using the default NTFS-3G driver).  To read and write to ext3 ubuntu from windows, simply get [fs-driver.]("http://www.fs-driver.org/faq.html") (But it doesn't support ext4)

hope that helps

---

### Post by emeraldgirl08 on 2009-05-21
> Those are your kernel updates. By default it keeps the previous versions. They don't take up much room, but you can remove the oldest if you want. (Or just remove the entry from /boot/grub/menu.lst). It is recommended to keep the next most recent as a backup.
I'd like to remove the oldest one. How do I do this??? I'm not quite sure what to do with the /boot/grub/menu.lst.

---

### Post by logos34 on 2009-05-21
> **emeraldgirl08 said:**
> I'd like to remove the oldest one. How do I do this??? I'm not quite sure what to do with the /boot/grub/menu.lst.

follow this:

[http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall](http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall)

---

### Post by black_shadow on 2009-05-21
Yes it is possible to clone the who;le disk and extend the partition if you follow the following :-
```

http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk
```

Regards Michael

---

### Post by louieb on 2009-05-21
> I have a question on the size of partitionsPerformance starts to go down after a partition gets around 75-80% full. Gparted will show how much data is in the current partition. I would take that and size  the new partition double it when copying the partition to the new drive.  Gparted will copy the old partition to the new drive and letyou to make the size of the new partition larger. (or smaller) at the same time. 

See the link logos43 has in post #11. Thats how I did my copies. 

> .. remove the oldest ... what to do with the /boot/grub/menu.lst...Use Synaptic to remove the old kernel it will handle modifying menu.lst too. 

> The rest is for the IBM Rescue and RecoveryBought my T30 used too. Did not have a recovery partition - just XP. Don't know If you need it.


Would be good for you to post a screen shot of the Gparted window (alt+prt screen) to save it to a file.

---

### Post by emeraldgirl08 on 2009-05-26
Okay. I got my external HD hooked up. I don't see an Desktop icon for my drive. When I go to Places>>Computer there is an USB Drive. I'm assuming that's my external HD.

What is the next step? I need to format it right?

---

### Post by emeraldgirl08 on 2009-05-26
**This is my fdisk -l report w/ external HD plugged-in:**

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1fff1ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2321    18643401    7  HPFS/NTFS
/dev/sda2            4650        4864     1723680   1c  Hidden W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            2322        4649    18699660    5  Extended
/dev/sda5            2322        4546    17872281   83  Linux
/dev/sda6            4547        4649      827316   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by logos34 on 2009-05-26
tell us exactly which partitions you want to clone to the usb (sdb).  Or do you want to do the entire disk?

You don't need to format the drive first.

EDIT:

ok, I went back in read thru the thread again...

Easiest way: Use gparted as louieb and I suggested.  Follow the instructions in the Gparted document "[HOW TO  'MOVE / COPY'  PARTITION]("http://gparted.sourceforge.net/larry/move/move.htm")."  You can copy the ntfs and fat32 partitions from within ubuntu, but to do ubuntu / you'll have to use gparted on the ubuntu live cd (-->System>admin>partition editor).  Reason: root cannot be mounted during copy.

Faster way:  Use [Clonezilla live cd]("http://clonezilla.org/clonezilla-live/") (--> "[Disk-to-disk clone]("http://clonezilla.org/clonezilla-live/doc/")").  Does the whole drive in one shot.  You can start it up and then go get some coffee or whatever.

If you've decided on doing a fresh install of jaunty, then that's one less partition to copy.  But you have to manually specify ext4 if that's what you want, otherwise it will use ex3.

---

### Post by emeraldgirl08 on 2009-05-26
> **logos34 said:**
> tell us exactly which partitions you want to clone to the usb (sdb).  Or do you want to do the entire disk?

I do need the Windows and IBM's Recovery and Rescue Partition (hidden; need because I don't have the OS Disk). I want the setup optimized for speed and convenience. I read that Linux and Windows could share a FAT32 partition. I'd like to try that.

What do you recommend?

---

### Post by logos34 on 2009-05-26
yeah, you could create a shared fat32...especially if you're definitely moving to ext4/jaunty...the fs-driver for windows does not yet support ext4...

I recommend doing the entire disk at once with clonezilla--besides, it will be a good learnign experience with one of the best imaging utilities...Just read thru the doc link I posted, download and burn the cd iso, boot with it and follow the steps.

After it's copied you can go back, expand the extended partition to take up all the empty space on the other half of the disk, then create a fat32 there.)

Partimage is definitely out amongst other reasons because it's support for NTFS is still 'experimental' only (the partitions I restored would get stuck at the login page).

---

### Post by geekygirl on 2009-05-26
> **emeraldgirl08 said:**
> I do need the Windows and IBM's Recovery and Rescue Partition (hidden; need because I don't have the OS Disk). I want the setup optimized for speed and convenience. I read that Linux and Windows could share a FAT32 partition. I'd like to try that.

What do you recommend?

Why not create the recovery discs in XP prior to this? Sony and Toshiba also ship their laptops with a 'recovery partition' which is used  to burn your recovery discs should your HDD become completely stuffed!

They dont give people disks anymore, they give a recovery partition and the tools to burn your own recovery discs (which returns the laptop back to factory settings - complete with bloatware) 

I would imagine that IBM/Lenovo have the same setup in the XP menu somewhere where you can create your discs.

This would probably be the smartest move right now especially if you are mucking around with partitions!!  

:)

---

### Post by louieb on 2009-05-26
The fdisk output shows you have a clean hard drive to work with.  Clonezilla might be a good option. I've used it before because it has a nice front end to partimage which I use to backup before upgrades.

I attached Gparted screen shots of the old and new drive. I'll just go over what I did to get things copied from the old to the new.  Every thing I did was done with Gparted  after booting a  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") . 


[LIST]
[*]select the new drive. (sdb)
[*]create a partition table  - just use the default msdos partition table type. (make sure its the new drive - you do this to the old one and bad things happen)
[LIST]
[*]back to the old drive  (sda) - select partition sda1 (win XP)  and click copy
[*]back to sdb - select the unallocated space - and click paste. Told Gparted how big to make the partition (I gave XP some more space 20GB total).

Clicked apply - should have gone to lunch took awhile for it to copy and grow the partition to the new drive.
[/LIST]
 
[*]did the same sda9 copied to sdb2 (dedicated grub partition - you don't have one)
[*]did the same sda5 copied and resized to sdb3 (my Ubuntu root partition)
[*]need more that 4 partitions so now made sdb4 extended partition.
[LIST]
[*]back to sdb and select the unalllocated space
[*]selected new and type extended - gave it all the remaining unallocated space, then clicked apply.
[/LIST]
 
[*] copied and resized sda6 to sdb5 (my /home partition)
[*]copied my swap partiton  sda8 to sdb6.
[/LIST]
Still had a lot of unallocated space but had what I needed on the new drive to see if would work.

Now I had to change the MBR to load GRUB in sdb2. So I opened a terminal widow.
and  ```
grub 
```two command later the MBR was changed
```
root (hd0,1)
setup (hd0)
quit
```Now the new drive should boot. So took the old drive out and put in the new. When I booted everything worked.

The new drive still has some unallocated space. I'll decide how to use that later when I need it.

---

### Post by emeraldgirl08 on 2009-05-26
Okay. I was helping a family member convert .srt to .sub files and burning an .avi file.

Ugh. It seems I'm the "goto girl" for things like this!!!

](*,)  :)

Thanks for everyone who left me some tips- I appreciate it!!!

I got Gparted Live 0.4.5.2 and System Rescue CD x86 1.2.0 on bootable CD. Haven't tested them out yet. They were pretty big files to DL and now that I've read about Clonezilla ARGH!!! 

As for burning things. I did order an external DVD-writer that just got shipped out today from Nevada. Should be here by Thursday :)

Okay going to read a little more and test my BootCD's.

---

### Post by emeraldgirl08 on 2009-05-27
Okay. I got Clonezilla downloaded. 

There was a little difficulty involved downloading but I have it. I gave it a test boot and it got all the way up to choosing a keyboard layout. I chose to end it there but didn't know how to exit. I pressed alt+ctrl+delete to exit.

*don't laugh*

That froze the screen and ejected the disk. I then held my power button down to immediate shutdown.

Okay. I got the USB 2.0 Ext. HD hooked up and the Clonizilla ready.

---

### Post by logos34 on 2009-05-27
ok, so use the step-by-step I gave you or [look here]("http://http://usalug.org/phpBB2/viewtopic.php?printertopic=1&t=14312&postdays=0&postorder=asc&&start=0&sid=4d208b5f61e01ee5a68a5e624021b159") (nice big pix) [steps 1-2, eight)

basically you want to go:

# Choose "ToRAM" option in the boot menu
# Choose language
# Choose keyboard layout
# Choose "Start Clonezilla"
# Choose "device-to-device" (2nd option)
# Choose "disk_to_local_disk"
# Choose source disk
# Choose target disk
# Start cloning

(*In the step-by-step you can click on each step and it will show you a screenshot at the bottom)

---

### Post by emeraldgirl08 on 2009-05-28
Okay. I used the GParted Live Disc 0.4.5.2 to copy my partitions over to my new HD.

This was a pretty anxiety-filled operation. I don't have a second comp right by me so I used my PDA to view web pages and documents I had saved as reference.

First I copied the NTFS (XP Pro) files to my new drive and pasted them. It took awhile for the clone to finish. I went to look at the contents on my old drive and saw I had not copied the FAT32 hidden partition over. I then copied and pasted that but moved the partition WAY over to the right. That's how it looks in the GParted GUI so I mimicked it. I also mimicked the flags. I hope that was the right thing to do.

I then shutdown the computer by holding down the power button and swapped drives. I DID NOT REBOOT as the instructions clearly stated. Here's where something BAD happened. The HD caddy had a stubborn screw. I slipped and dropped my old HD. 

Four bent pins. I straightened them out and do not know if the old HD will even work now :(

After swapping drives I started the comp up and pressed F12 to select CD-ROM as booting device. I inserted Super Grub Disk 0.9797. This is where I got lost. I just pressed enter throughout the instructions. I picked "Boot Windows" and now I'm typing from my Windows partition.

Is it okay to restart my comp now? Do I need to do something so that Windows will boot on it's own?

---

### Post by louieb on 2009-05-28
So super grub can boot your new XP on your new drive.:KS  Now go back and restart with the Super GRUB CD again.  There is an option in there to put code in the MBR to boot windows.  Forgot where, seem to remember its under the advanced selection.

  There are other ways to make the drive boot straight to windows  describe here [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm") but Super Grub is probably the easiest. 

As far as the bent pins just straighten them out the best you can. Then put the old drive in your USB enclosure and see what happens when you plug it in. My guess is it will probably work. IBM built the T30 almost like a tank.

---

### Post by logos34 on 2009-05-28
> **emeraldgirl08 said:**
> Okay. I used the GParted Live Disc 0.4.5.2 to copy my partitions over to my new HD.

This was a pretty anxiety-filled operation. I don't have a second comp right by me so I used my PDA to view web pages and documents I had saved as reference.

First I copied the NTFS (XP Pro) files to my new drive and pasted them. It took awhile for the clone to finish. I went to look at the contents on my old drive and saw I had not copied the FAT32 hidden partition over. I then copied and pasted that but moved the partition WAY over to the right.

...

After swapping drives I started the comp up and pressed F12 to select CD-ROM as booting device. I inserted Super Grub Disk 0.9797. This is where I got lost. I just pressed enter throughout the instructions. I picked "Boot Windows" and now I'm typing from my Windows partition.

You could have avoided all that by using clonezilla as I suggested in the end.  I would have been faster (though not quite as easy to understand as Gparted), and would have duplicated the disk all in one shot, boot/MBR and everything, leaving no room for error.  You could still have adjusted the partitions afterward, and if you decided to do a fresh install of Jaunty, all you had to do was install over 8.10.

---

### Post by emeraldgirl08 on 2009-05-28
Okay. I rebooted and XP is working :)

No Ubuntu..yet.

I am going to do a system restore and get this girl back to factory reset. I want to start over and install things differently this time. I am using 17 gb for XP. There is around 1.6 for FAT32. The rest is free to do what I want with.

Thanks for all your help!!! 

**Louie and Logos especially! **

Things are kinda slow- not faster. We'll see how that goes in the coming days.

---

### Post by Dngrsone on 2009-05-28
For future reference, there is a product called [HDClone](http://www.miray.de/products/sat.hdclone.html) which will copy the contents of one drive onto another, bit for bit.  I've used it to upgrade several laptops to larger drives, maintaining the already installed operating systems and data and hidden recovery partitions.

---

### Post by emeraldgirl08 on 2009-05-28
> As far as the bent pins just straighten them out the best you can. Then put the old drive in your USB enclosure and see what happens when you plug it in. My guess is it will probably work. IBM built the T30 almost like a tank.
LOL. I just tried the old HD in an enclosure and it works!!! And this is from an unprotected fall from about four feet! My next newer comp is going to be an IBM product. Not too sure about a Lenovo. I hope those are as good as IBM's :)

**Edit:** Dngrsone I do have HDClone but my clone went this way. It's my first clone so I felt comfortable with the advice I was getting here.

---

### Post by Dngrsone on 2009-05-28
No worries, Emerald.  It's one of the tools I have come to rely on, so I spread the gospel.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

