---
title: "External USB HDD NTFS messed up"
date: 2012-11-16
forum: Hardware
---

### Post by Peltsi on 2012-11-16
Hi,

I bought an external usb-2.5" sata adapter from ebay, and installed a 1TB drive on it to use as a backup medium and data transfer between computers. Works 100% on windows computers.

Problem: I cannot use the hdd on 2 of my linux computers. The other is running ubuntu 12.04, other has xubuntu 12.04. This laptop with xubuntu also has windows installed, and on windows the hdd works.
First of all, i tried to create an ntfs partition on my other linux box. Partition created ok, but after copying some files into it it got messed and would no longer work. So, I created the partition on my windows computer.. No problems there. Can write & read as many times as I care and it works. But, plug it onto a linux box, and after some time of use it gets messed up. First time chkdsk on windows was able to correct it (some files got corrupt in the process) but on second try nothing short of repartitioning would fix it.

After the first reformat I only used it on my windows computers (been a few months after that..) but yesterday I wanted to try it again on a linux computer, to see if maybe some patch had fixed the problem. Copied some 20gb of files into the hdd, which seemed to go ok, but after hooking up the drive to a windows computer it now seems it's messed up again, and chkdsk cannot fix it anymore. 

Xubuntu still is able to see the volume, but many of the file- & folder names are corrupt, as are some of the files too.. So no joy.

Short of buying another usb-hdd adapter(and crossing my fingers it'll work), is there anything else I can try before that?

---

### Post by BicyclerBoy on 2012-11-16
Really ugly problem..

I have a Seagate 750GB 2.5 USB HDD formatted hpfs/ntfs & have used with lucid 10.04 winXP & 12.04.

I formatted this with 12.04 (ntfs-ng 2012.1.15).

After coping 35GB music (5000 files) (lucid 10.04 ntfs-ng 2010.3.6) I had one filename problem, name contained an illegal character; all files were okay.
I checked with winXP disk check program.

I have regularly copied multiple files of size 2GB to 6GB (with lucid 10.04) without any problem..

Do you have ntfs-ng & libntfs-ng packages installed ?

---

### Post by Peltsi on 2012-11-17
Hi,

Thanks for your reply. I don't have either of those packages installed.. Seems like they're not available from standard repositories either?

The problem likely seems to be either with the 1TB sized partition or the USB-sata hardware. I have a smaller NTFS partition on the internal HDD on this laptop, which has remained perfect despite intense cross-OS usage.

---

### Post by BicyclerBoy on 2012-11-17
I could well believe there might be a problem with larger than 2TB drives or partitions..

libntfs10 is in "universe" (The Linux-NTFS project)
ntfs-ng is std package.

I was nervous that ntfs support in linux was not reliable so I would have installed the later libntfs on all machines...

You could try to partition the drive (in full updated winXP) to parts of size 500GB.

The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/))
maybe you can find some clues there..

---

### Post by ptsubin on 2012-11-21
Did you try with any other file system type? In my case with the same USB SATA bridge, everything including the partition table gets corrupted. But mine works fine under Windows and Ubuntu 12.10.

---

### Post by BicyclerBoy on 2012-11-21
How do you know what the USB-sata bridge h/w was ?

Did the OP post this somewhere?

Note: the Seagate Go-flex 2.5" USB3 is rock solid..(so far).

---

### Post by Peltsi on 2013-01-14
Hi again,

Been a while since I played with this matter, but today I tried to see if some other file system would work for this HDD when working from linux. But the result is, no matter what the filesystem is, It even fails to create the partition.(Or manages to create it, but it's completely unusable)
Again, working from windows 7(on this very same computer), it works perfect, so it looks like I'm stuck using this disk only from windows.

I posted the details of my hardware to this other thread; [http://ubuntuforums.org/showthread.php?t=2085782](http://ubuntuforums.org/showthread.php?t=2085782) (USB-SATA hardware in my case too is the Super top M6116 sata bridge)
Sorry, should have also posted it here. 

You can find out what your USB-SATA converter is by typing lsusb in terminal. It will list all the connected USB devices.

---

### Post by BicyclerBoy on 2013-01-14
Don't get offended..
But you do get what you pay for.
If it was Seagate or WD you would (likely never) had a problem.

Buy a decent adapter & reuse your HDD..

---

### Post by Peltsi on 2013-01-15
I see your point.

But, as it's working 100% on windows, I see there is no problems in the hardware, just something broken on linux causing it not to work. So to fix the problem properly is to fix the underlying software problem :)

Too bad I don't even have a clue where to start.

---

### Post by BicyclerBoy on 2013-01-15
I do see your point as well..

Your device is probably a clone of some generic (functioning) device.
I imagine there is some patch in windows driver or a undocumented work-around in windows.

You could find the USB IDs etc & check if there is any known issues in driver..
lsusb
Is the USB adapter mentioned in (when plugged in):
dmesg

---

### Post by Peltsi on 2013-01-16
[LEFT]May have found the problem and possible solution;
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082215)
Now i just need to figure out how to remove such patch...
[/LEFT]

---

### Post by Peltsi on 2013-01-16
Ok tried rebuilding the driver from sources, but no go.. Something wrong with my setup, as the created .ko file differs about 10% of the original size. And not surprising, it does not work.
Is there a quide for dummies available how to build and install a driver module from sources?

---

### Post by Peltsi on 2013-01-20
Finally got it to work by recompiling the whole kernel after fixing the problematic header file in the sources.

---

### Post by Fremont_Cunningham on 2013-02-08
This is a serious problem. Shipping an OS that without warning currupts an HD - even if it is USB-attached - is not a good thing to do.
Ubuntu 12.04.1 + super top M6116 SATA bridge trashed all the data on my old HD, but I do have a backup. Ubuntu trashed the drive every time - without fail.
Details:
I have 2 test systems: a desktop AMD 64 bit machine running windows7 and a Laptop AND64-bit triple-boot machine runing Ubuntu 12.04.1/Windows7/WinXP.
The HD is the old WD 350Gig HD from the laptop, which now has a new 500G HD internally.
The 350Gig had has 3 partitions, each around 100G. I don't think this is a partition size problem.
Format - ONLY NTFS is commonly supported betweem Windows7 and Ubuntu. Originally the HD was ext3, which Windows7 does not understand, but Ubuntu mounted it ok, and within a few minutes corrupted it - during read only operations!
Sincce then all tests have been with NTFS format.
The super top M6116 SATA bridge works FINE every time on the Deskop Win7 system and on the Laptop using Win7. It FAILS every time using Ubuntu on the Laptop.
So - its not a problem in the super top M6116 SATA bridge (unless the M6116 chip has a bug that Windows drivers are compensating for.)
The problem is not in the Computer hardware or BIOS as Laptop+Win7 works, Laptop+Ubuntu fails.
Peltsi's post about rebuilding the driver is very interesting, but I am a bit loth to try rebuilding kernel things - I need the laptop for work.
Is this serious problem being looked at by Canonical gurus?

---

### Post by Peltsi on 2013-02-23
Hi,

At least the bug has been reported and status is "triaged", so I think they're looking into it. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1082215)

M6116 is a very common adapter, there must be a really big bunch of people wondering why their external hdd broke with linux.. And like this thread proves many times others will just blaim the "crappy" adapter, which for some weird reason works perfect in windows.

I also use this laptop for work, installing / uninstallin new kernels imo is quite safe, so if you really need the hdd go for it. Before official fix it's the best option.

---

### Post by BicyclerBoy on 2013-02-23
@ Fremont et al..

Why do you feel that Ubuntu (& linux) are responsible.
Your choice to use FOSS OS & kernel.
There is no guarantee of any h/w support.
It is your responsibility to check h/w compatibility.
You have no right to complain, but you are free to report problems & fix them.

You must take responsibility for being willing to commit your important data to some cheap clone brand adapter.

If you choose to reward Seagate there would be no issue. 

If there is blame then it should lie with M6116 silicon or its firmware designer.
You can bet that the designers of M6116 adapter worked with Microsoft to patch windows & get thru' MS certification testlab.
Did they contact linux kernel devs?..

---

### Post by Peltsi on 2013-02-24
There is absolutely nothing wrong in the M6116 chip or it's firmware. The linux USB storage driver just has a fatal bug, that's all. See the launchpad bug report for yourself. if you fail to believe me.

---

