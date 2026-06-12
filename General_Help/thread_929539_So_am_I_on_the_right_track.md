---
title: "So am I on the right track?"
date: 2008-09-25
forum: General Help
---

### Post by 357mag on 2008-09-25
Okay I think I may actually try to install Ubuntu and create a dual-boot environment with XP. I have two SATA drives inside my computer. I already have XP installed on the first one. My plan is to put the Ubuntu install disc in the drive and install Ubuntu on the second hard drive. I'm planning on just putting Ubuntu on the entire drive with no extra partitioning to keep things simple.

I assume there will be a point in the installation program when it will ask me where the GRUB boot loader should go. I do not want to install it to the MBR of Windows. For me I feel it would be better to install it on the Linux drive.

After that I will need to either do one of two things I believe. Either install BootPart and let BootPart automatically take the information from the GRUB loader and place it in the boot.ini file of Windows...

Or open up a Terminal Window and type that goofy looking command and save the contents of the file to either my Flash Drive or my USB drive. Then go into Windows and copy that file and place it into the boot.ini file.

Speaking of which when you are in the Terminal Window and you type that copy command to copy the contents of the GRUB loader, how do you save it to the external drive? Do you just press Enter and it's saved?

Based upon what I've researched I guess this is what I gotta do.

Sound correct?

---

### Post by justsomedude on 2008-09-25
BootPart shouldn't be neccessary...

Backup all your data first, we're all human and make mistakes (except me :D).

Use the alternate CD to install Ubuntu, the live CD will give you no options where to install GRUB (if memory serves me right).

Install Ubuntu (and GRUB) to your second drive.

Go to your BIOS and set your second hard drive to be your primary boot device.

If Windows doesn`t boot from GRUB, we can take of it afterwards.

---

### Post by 357mag on 2008-09-25
So are you saying if I go into the BIOS and set it so my computer now boots from my second drive, which would be where Ubuntu is installed, it should also give me the option to boot into XP?

---

### Post by justsomedude on 2008-09-25
> **357mag said:**
> So are you saying if I go into the BIOS and set it so my computer now boots from my second drive, which would be where Ubuntu is installed, it should also give me the option to boot into XP?

Yes it should.

However, you can never be sure 100% and it may require us to change a config file. Nothing major, you'll get in touch with your inner geek in no time.

Be aware that these separated setups are a little more tricky than installing two operating systems on one drive. New users often go this route because they think it's the safest approach. While there is some merit to this thought, it's a little more difficult to set up.

But don't worry, we'll get you through this. 

Again, use the alternate CD to install, the live CD will kill the Windows MBR.

---

### Post by 357mag on 2008-09-25
I see. I guess I still kinda like the idea of using the Windows boot loader to load both operating systems. I've done quite a bit of reading on that and I guess I kinda like that approach. 

I could first try it that way and if I can't get it to work or it's too much frustration, I could try it the other way.

I guess it is just a preference of mine.

---

### Post by 357mag on 2008-09-25
It looks like Ubuntu shows both my internal drives plus my Flash Drive. I also have two DVD burners, but those don't appear to be showing up. I noticed that when I inserted an audio disk in one of them, then it said Audio Disk on the Desktop.

When I get this installed will my two optical drives show up? Or do I gotta do something to make them show up?

---

### Post by justsomedude on 2008-09-25
Go to *Places --> Computer*

Your drives should work... :)

---

### Post by 357mag on 2008-09-25
Okay I see all my drives listed under the Computer Browser. Why don't all the drives show on the Desktop though? Is there a way to send icons representing the optical drives to the Desktop?

I also noticed that it shows another USB drive even though I don't have it hooked up to my computer. But I do have the USB cable connected to the back of my machine. Funny.

---

### Post by justsomedude on 2008-09-25
> **357mag said:**
> Okay I see all my drives listed under the Computer Browser. Why don't all the drives show on the Desktop though? Is there a way to send icons representing the optical drives to the Desktop?

Not that I know of.

Your drives will automatically show once you actually insert a cd though. These are only virtual representations to help you anyway, Linux has no idea what a "drive" is. ;)

---

### Post by kokkus on 2008-09-25
Here's a tip.
Ubuntu can read the HDD with windows installed but windows will not read the partition with ubuntu installed as long as it isn't already NTSF,
so install your windows programs, music, videos etc. on the windows HHD so both the OS can read it.

---

### Post by 357mag on 2008-09-25
When you want to eject a disc do you always have to use the context menu on the drive icon and hit Eject? Or is there a way to make pressing the button on the drive itself work?

---

### Post by kokkus on 2008-09-25
When you insert the cd, don't you push a little button then so the cd goes in? Click the same button to eject it.
Or was that totally not what you ment?

---

### Post by justsomedude on 2008-09-25
Both ways should work, as long as the drive is not in use.

---

### Post by 357mag on 2008-09-25
No doesn't quite work. Strange. When I press the button on my lower drive the tray does eject. But when I press the button on my upper drive, nothing happens.

---

### Post by justsomedude on 2008-09-25
Is it possible the Ubuntu Live CD is in there? ;)

---

### Post by 357mag on 2008-09-25
Yes. That is very, very possible. He he.

---

### Post by TeXtonyx on 2008-09-25
The Live cd works for placing grub in the Ubuntu boot partition, step 7, under Advanced. 
If for instance sda is your first drive and sdb is your second drive, choose sdb1 for grub. 
After installing, Ubunt will reboot to XP.  Then run Bootpart from the Dos prompt
C:\>bootpart <enter>  which will generate something like the report below:
Physical number of disk 0 : 56d9f43b
 0 : C:* type=7  (HPFS/NTFS), size= 59568988 KB, Lba Pos=63
 1 : C:  type=f  (Win95 XInt 13 extended), size= 20844337 KB, Lba Pos=119138040
 2 : C:  type=b   (Win95 Fat32), size= 489951 KB, Lba Pos=159846813
 3 : C:  type=5   (Extended), size= 19462747 KB, Lba Pos=119138041
 4 : C:  type=83    (Linux native), size= 19462684 KB, Lba Pos=119138166
 5 : C:  type=5    (Extended), size= 891607 KB, Lba Pos=158063535
 6 : C:  type=82     (Linux swap), size= 891576 KB, Lba Pos=158063598
Physical number of disk 1 : 7e915766
 7 : D:  type=83  (Linux native), size= 8144923 KB, Lba Pos=63
 8 : D:  type=83  (Linux native), size= 12209400 KB, Lba Pos=16289910
TeX: Your report will also show a D swap partition.  You will use the first type 83 on D
C:\>bootpart 7 ubuntu.bin Ubuntu <enter > writes the 512 sectors of ubuntu.bin and
places this line in boot.ini  C:\ubuntu.bin="Ubuntu"  providing a Ubuntu boot choice.
This is the best way. The first time I used the dd command after creating a small fat32
partition on the first drive (sda). Then used the live boot cd again to open up a terminal
in Ubuntu and typed sudo mkdir /mnt/fat32 <enter> 
then mount -t vfat /dev/sda2 /mnt /fat32  <enter>
then dd if=/dev/hda2 of=/mnt/fat32 /ubuntu.bin bs=512 count=1 <enter>
then still from Ubuntu terminal, cd /mnt/fat32 <enter>  then ls <enter> see if its there
Then reboot: Use My Compter to go to your fat32 partition and copy ubuntu.bin to C:\
Then you have to change boot.ini from write only permissions by 1*right-clicking* and 
then type into boot.ini  C:\ubuntu.bin="Ubuntu" Save and restore write permission.
TeX: So you can see why I think that method is more work than using Bootpart.
Later from Ubuntu you will take these steps:
Code:
sudo apt-get install ntfs-config
sudo ntfs-config
This employs the ntfs driver ntfs-3g, and writes to fstab so you can read/write Win XP.
If you choose  /media rather than /mnt it displays automatically on the desktop.
Here is a fine tutorial which works well if you substitute "Ubuntu" for "OpenSuse".
[http://www.swerdna.net.au/linhowtoboot1.html](http://www.swerdna.net.au/linhowtoboot1.html) 1*then choose Properties*

---

### Post by 357mag on 2008-09-25
That was quite a complex post. I have a few more questions:

1. My processor is the Intel Quad Core 2.40 Ghz. I'm not sure but I think this has 64 bit support. Should I download the 64 bit version of the Alternate CD instead of the normal Desktop version?

2. This partitioning business. It appears that I can choose Use Entire Disk or Manual. If I choose Use Entire Disk does Ubuntu do everything automatically for me as far as determining the sizes of the swap partition and the home partition and all that?
I watched a video on YouTube and most everyone was choosing Manual and entering in sizes for all these partitions.

---

### Post by justsomedude on 2008-09-25
> **357mag said:**
> That was quite a complex post. I have a few more questions:

1. My processor is the Intel Quad Core 2.40 Ghz. I'm not sure but I think this has 64 bit support. Should I download the 64 bit version of the Alternate CD instead of the normal Desktop version?

What's the exact cpu model? How much RAM do you have?

> 2. This partitioning business. It appears that I can choose Use Entire Disk or Manual. If I choose Use Entire Disk does Ubuntu do everything automatically for me as far as determining the sizes of the swap partition and the home partition and all that?
I watched a video on YouTube and most everyone was choosing Manual and entering in sizes for all these partitions.

Ubuntu does everything automatically for you, however it does not setup a separate /home partition by default. So, manually setting up partitions is actually a good idea.

---

### Post by TeXtonyx on 2008-09-25
[http://blogs.msdn.com/oldnewthing/archive/2004/08/18/216493.aspx](http://blogs.msdn.com/oldnewthing/archive/2004/08/18/216493.aspx)
If you have 4GB of ram memory which is the max for Windows XP Pro, you can use
the /3GB switch in boot.ini which helps if you use any memory intensive applications,
because it can be used to minimize disk writes. To use more than 4GB of memory, one
must use a x-64 OS and a mainboard which is also compliant. 
But for Linux, I don't think there is a 4GB memory limitation. Plus, there are so few
programs are written to optimize x-64 capability. The main  concern would be drivers for 
your hardware.

---

### Post by 357mag on 2008-09-25
I don't have the box anymore but I believe I have the Intel Core 2 Quad Q6600 Kentsfield. I think most of these have 64 bit support.

I have 3 GB of RAM.

I'm really just going to be using Ubuntu for the following things:

1. Internet surfing
2. Checking email
3. Listening to CD's while surfing
4. Printing articles from the web

That's all I'm planning to do in Linux. I will use XP for all my other work. So for me it should be a simple set up.

So if I choose Use Entire Disk then Ubuntu will set up all needed partitions for me automatically then?

---

### Post by TeXtonyx on 2008-09-25
"So if I choose Use Entire Disk then Ubuntu will set up all needed partitions for me automatically then?"

Yes, just be sure you are installing to your second drive, sdb, not your first drive.  
Linux labels the first drive 0, so then the second drive is 1, remember that in the future.
Your boot partition (not MBR) for the grubloader will likely be sb1.

---

### Post by 357mag on 2008-09-25
I downloaded the 64 bit version. The guy on YouTube said that version allows Ubuntu to take advantage of the Quad Core 64 bit processor.

---

