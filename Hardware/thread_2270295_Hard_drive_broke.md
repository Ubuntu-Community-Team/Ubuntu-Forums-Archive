---
title: "Hard drive broke?"
date: 2015-03-21
forum: Hardware
---

### Post by david366 on 2015-03-21
Hello guys, 

I'm new to Ubuntu and any hardware issues. Cosnider me 100% ignorant to this type of thing and please help where you can.

My laptop said "operating system not found" which is confusing. I've read I can run ubuntu on my broken laptop to see if the HDD is broke and if not, retrieve my files.

I've tried reading the how-to guide but there's a lot of things i'm not 100% sure what they are. Is anyone able to guide me through this?

It may be the case that the HDD is just broke, but I thought i'd give this a shot.

Is it best to install ubuntu via a CD? or USB? I have ubuntu saved on an external hard drive and changed my broken latop (vio BIOS) to boot via external device. But I'm getting the same thing.

I may not have installed ubuntu correctly on the HDD (it seems that way) so any help is appreciated

Thanks so much in advance guys

---

### Post by Bashing-om on 2015-03-21
david366; Hi ! Welcome to the forum.

It is perfectly acceptable to be 'new'. We do work at that level.
I will start this ball rolling, see where it takes us.

Nope, my bet is that the hard drive it's self is good.

What we often see with the error " operating system not found " is that UEFI/secure boot is not properly configured.

So let's clear that up.

Is this a UEFI capable system ? Please advise us of what system you are installing ubuntu onto.
Are you dual booting ? And IF so, what other systems are installed.
Can you now boot a liveDVD OR liveUSB ? - either will do .

Once we know what hardware, and that you can boot an install medium - liveDVD(USB) - then we have a close look at the hard drive(s).

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by david366 on 2015-03-21
> **Bashing-om said:**
> david366; Hi ! Welcome to the forum.

It is perfectly acceptable to be 'new'. We do work at that level.
I will start this ball rolling, see where it takes us.

Nope, my bet is that the hard drive it's self is good.

What we often see with the error " operating system not found " is that UEFI/secure boot is not properly configured.

So let's clear that up.

Is this a UEFI capable system ? Please advise us of what system you are installing ubuntu onto.
Are you dual booting ? And IF so, what other systems are installed.
Can you now boot a liveDVD OR liveUSB ? - either will do .

Once we know what hardware, and that you can boot an install medium - liveDVD(USB) - then we have a close look at the hard drive(s).
[INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]



Hello. Thanks for your reply. Really appreciate it.

I tried installing ubuntu on to an external hard drive and tried booting the laptop (Sony Vaio e-series) via the external hard drive. Changed the boot order to external device to boot up. 

But i'm not sure it's been installed correctly as there are other files etc on the external HDD. Should I install it on to a CD? or would a USB stick work just as good? Does ubuntu need to be the only thing installed on to it?

I want to make sure I install it on to the USB/CD correctly.

Not sure what UEFI compatible is...

Thanks so far!

---

### Post by Bashing-om on 2015-03-21
david366; Hey;

Sony Vaio e-series -> which one ? as the 14A runs with hybrid graphics, Getting graphics to work under these conditions can sometime be a challenge.

I ask again, any problem booting the install medium ? either a DVD or USB ?
We will need this live medium in order to trouble shoot.

Booting a liveDVD(USB) is the place to start.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by weatherman2 on 2015-03-22
Dave, a USB stick is the best approach - and yes (unless you know what you are doing), you will want to use the whole USB drive for Ubuntu.  In fact, everything will be erased by default if you try to use a USB drive for this.  I'd get a clean USB flash drive, 2GB or larger is probably best.  (They are pretty cheap these days.) 

There are lots of demos on YouTube I think.  You first download that big .ISO file from Ubuntu, then you need to use something to put that image from the ISO file onto the USB drive.  You can't just copy it - it must be "imaged" on there by software that knows how to do it.  Try something like Unetbootin if you have another Windows computer to use temporarily, to prepare the USB drive.  

FYI, if your Sony is really, really old (2006 or older?), you may not even be able to boot off of USB.  You can use a DVD disc too if you want, but nowadays booting from USB is probably the best approach, if laptop can do it.

As for the comment about UEFI above: that would apply if your Sony had Windows 8 or 8.1 on it.  If it had Windows 7, Vista, or XP, it probably doesn't use "UEFI" (for secure booting) so I wouldn't worry about that.

---

### Post by david366 on 2015-03-25
Thanks guys! Going to try get a USB that's the correct size and run it off that. When I turn my laptop on with a USB in (with uuntu) will it automatically start via the USB? Or will I have to update BIOS then it will run?

The laptop is about 5/6 years old. So around 2009.

Sorry for the late reply! Been busy. I'll keep you informed and any more help is appreciated!

---

### Post by weatherman2 on 2015-03-25
You should be able to boot from USB from a model from 2009.  I don't have a lot of experience with Sony laptops.  On some laptops you can hit a key (like F12) to get a boot menu upon startup and choose the USB drive from the menu.  But you should probably go into BIOS Setup after you've plugged in the USB drive and look for an option to boot from it.  You might plug in whatever USB drive you have now (without installing Ubuntu, just to to plug it in) and see if in your BIOS Setup you have the option to boot it.  If you do, then you should be OK with whatever new USB flash drive you buy for this purpose.

---

### Post by david366 on 2015-03-27
Ok guys so I booted it through ubuntu thanks for the tips!

Now... on the system it shows "309GB volume" under devices. I presume this is the hard drive. It says there's 10,000+ items. But I can't see anything under any files!

Is my hard drive passed repair? :/   It's confusing that it can see there's 10,000+ files though. I guess there still there somehow.... Strange!

Any help is appreciated :)

---

### Post by Mark Phelps on 2015-03-27
Since you can boot into Ubuntu, let's get a look at what partitions are on the drive.  Open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  Post the results back here.

---

### Post by david366 on 2015-03-27
Im working on 2 laptops here. Hope this works! And have no idea what i'm reading... I fear the worst but here's to hoping!

[IMG][IMG]http://i60.tinypic.com/o2vi9.jpg[/IMG][/IMG]

---

### Post by Bashing-om on 2015-03-27
david366; Hey, hey

your:
> 
I may not have installed ubuntu correctly on the HDD (it seems that way) so any help is appreciated


In that last 'fdisk' output there is no partition devoted to ubuntu ( default file system type ext4); all are Windows.

So, what ya want to do now ? 
Try and fix Windows and then set up for dual booting ubuntu ?
Wipe Windows and install ubuntu as the sole operating system ( not recommended ! ) 

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by weatherman2 on 2015-03-27
David, to mount the partition with your files, go to the left column and find the "File Folder" icon (not the one that says "install Ubuntu").  Open a folder, then you should see a list of devices or partitions you can mount.  Something like this:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

(This is for an older version of Ubuntu so may look slightly different.)

In Windows Vista and 7, your files are probably under the /Users folder (in XP, look in Documents and Settings).  There is no such thing as a C: in Linux.  And / slashes are used instead of \ slashes that Windows uses - but they are equivalent.

If your files are there - find an external or portable hard drive and plug it into another USB port on the Sony.  Then you can drag-and-drop the files from the internal drive over to the external drive to save/copy them!

---

### Post by Unterseeboot_234 on 2015-03-28
I just want to put in my observation about what a bad HDD looks like when installing Ubuntu. The whatever version of Ubuntu would install and then I began to see a series of problems. Basically, none of the customizations, tweaking or updates became permanent. I suspect that during the brand-new install the drive will accept the first good sector and start recording. After that, ubuntu (or whatever OS) assumes the entire partition of the HDD is available for storage and bad files begin to happen.

I've got an old IBM-IDE drive with 500-meg capacity. It still works. My recent experiences is these modern high-capacity replacement drives (100gig or higher) have a shorter lifespan than my CMOS battery. Today, just one manufacturer makes all HDD under several brand names.

---

### Post by david366 on 2015-03-29
When I click the hard drive there are no files anywhere. It recognizes there are 10,000+ files but I cant see them to transfer or edit. The folders are there but no files visible..

Anyone know if the files are still retrievable if it seems to recognize there's 10,000+ files the but they just aren't viewable.

---

### Post by Bashing-om on 2015-03-29
david366; Welp'

We can certainly try ! Be advised I am no longer  Windows literate, and have no interest in Windows. However, try;
From the liveDVD, try ubuntu mode -> terminal:
```

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/sda2 /mnt/windows
ls -al /mnt/windows

``` 
(may have to install the ntfs-3g package, I do not recall ) where the target here is the 'sda2' file system. If the files you want are elsewhere, change 'sda2' to other partition identifier 'sda3' .

See where I am coming from .. with my thought processes, it is always CLI as the 1st line of approach.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Mark Phelps on 2015-03-29
Did this PC come preinstalled with Windows? IF so, my guess as to the partitions and their usage is as follows:
1) Recovery
2) Boot Loader
3) OS

If this is correct, then sda2 would need to have the boot flag set in order for Windows to boot from it -- and it does not.  So, the first thing I would try is booting into Ubuntu, launching GParted, and seeing it you can set the boot flag on sda2.  And then see if the PC boots into Windows.

---

### Post by Bashing-om on 2015-03-29
Yeah Mark !

There just is no substitute for experience.

[INDENT][INDENT]a little help goes a long long way
[/INDENT][/INDENT]

---

### Post by weatherman2 on 2015-03-29
> **david366 said:**
> When I click the hard drive there are no files anywhere. It recognizes there are 10,000+ files but I cant see them to transfer or edit. The folders are there but no files visible..

Anyone know if the files are still retrievable if it seems to recognize there's 10,000+ files the but they just aren't viewable.

David, you don't actually view the files on your "hard drive" - you view files on partitions within your hard drive.  I'm not nitpicking over terminology here - it's an important distinction.  Your hard drive has three partitions.  Your files are in one of them.  You should try to mount the partitions, using the mouse, from the file fold menu.  Of course, we can't actually see what you see on your screen - but the names may not make sense in the list.   They may look like machine gibberish - letters and numbers, not "C:" like you would see in Windows. (Bashing-om's suggestion should work too though /dev/sda3 is really the one you want not sda2 - but it requires typing commands in a terminal window, and some people aren't comfortable with that.)

Can you post another screen shot like you did above but showing what your "folders" window looks like?

FYI, you may also want to run a Windows program called chkdsk on your partitions.  This is a Windows-based tool that will fix errors in the WIndows filesystem and can allow you to access files that weren't visible before.  If you happen to have a Windows boot disc, you would need to boot that first and run chkdsk from there.  Then there are lots of web-based instructions to guide you through running the chkdsk command from a Windows disc.

---

