---
title: "Did I set up raid right?"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by Roasted on 2006-08-30
Trying to do a mirror format. I found the raid controller or something in bios, and ended up erasing everything on the disc and reinstalling the operating system.

Few questions...

For one, when I set up raid and I reboot, it says press f10 to go into the raid configuration utility. When I do, one drive is listed. Is that normal? Is that the drive that's mirroring? 

Secondly, when I reboot I can't get into the operating system. I'm on another PC now typing this out, just for the record. I have ubuntu reinstalling again, hoping that was the issue. When I went to reinstall Linux, I just "erased" the first disc prior to installing. I assume that'll do the same to the second disc?

Then, thirdly, when I rebooted I got an error 5 with grub. No clue what that means... ](*,)

---

### Post by Roasted on 2006-08-30
K, now all I'm getting is "disk boot failure. please insert system disk and hit enter"

Now I can't boot for shit. I think it's a bios setting... but everything looks okay to me. But I've never dealt with raid... ](*,) ](*,) ](*,) ](*,)

---

### Post by gerbman on 2006-08-30
Are you attempting hardware or software RAID? If you're going the hardware route, then you need to set things up in your BIOS somewhere. The hardware will manage the RAID array, and your OS will only see one drive. The setup will depend on the specific controller card you're using. 

If you're using software RAID, then you shouldn't need to set anything up in the BIOS. Use the Ubuntu Alternate install CD and configure RAID during setup (if you need help just ask). Software will take care of managing the RAID array, but will give you the same result (maybe not as fast, but definitely usable).

---

### Post by Roasted on 2006-08-30
I guess I'm going the hardware route, because I set up raid with a setting in bios. I enabled it. Then when I restarted it said hit F10 to set up raid, so I did.

Now everytime I reboot it'll display a drive and say something about healthy raid array: 250.1gb WD etc etc or something. I guess that's normal, since there's only one that lists. I guess I set it up right?


But now I'm having issues just getting linux to boot on these HDD's. I just got done reformatting and it's doing a full installation right now. Can you give me any tips about what to do when the installation is finished? Anything I should know?

---

### Post by Roasted on 2006-08-30
](*,)

---

### Post by gerbman on 2006-08-30
> **Roasted said:**
> I guess I'm going the hardware route, because I set up raid with a setting in bios. I enabled it. Then when I restarted it said hit F10 to set up raid, so I did.

Now everytime I reboot it'll display a drive and say something about healthy raid array: 250.1gb WD etc etc or something. I guess that's normal, since there's only one that lists. I guess I set it up right?


But now I'm having issues just getting linux to boot on these HDD's. I just got done reformatting and it's doing a full installation right now. Can you give me any tips about what to do when the installation is finished? Anything I should know?When you did the installation, did the installer see only a single disk (250GB WD)? If so, then I think you've successfully set up a hardware RAID array. However, if the installer recognized two disks, then the RAID array is not being used. This is what happened to my installation - I set the RAID 1 array up in the BIOS, but the installer still recognized two disks. I had to resort to a software RAID 1 install from the Ubuntu Alternate disk, but I'm still really happy with it. I can walk you through the steps depending on your situation.

---

### Post by Roasted on 2006-08-31
Is there any die hard way to know FOR SURE your mirrored HDD is fully functional and copying everything? I don't want to just guess, I want to know for a positive fact that everything works right.

I disabled the RAID feature to get Linux installed, I was having some issues. Right now, I've got a single SATA drive with everything on it and running. The other drive is formatted and empty right now. I plan to do another hardware RAID to set it up again. If I set it up again through hardware, then will everything just auto-transfer to the 2nd drive?

---

### Post by gerbman on 2006-08-31
> **Roasted said:**
> Is there any die hard way to know FOR SURE your mirrored HDD is fully functional and copying everything?Yes, but it will depend on whether you're using hardware or software RAID. I am using software RAID 1, and use 'mdadm' to see exactly what the RAID array is doing (synching, failing, reconstructing, etc.). 'mdadm' also allows you to simulate disk failures, so you'll know exactly how the system will react when it actually happens. If you're using hardware RAID, then you'll need to use a vendor-provided monitoring tool (an application in the BIOS, etc.)

> I disabled the RAID feature to get Linux installed, I was having some issues. Right now, I've got a single SATA drive with everything on it and running. The other drive is formatted and empty right now. I plan to do another hardware RAID to set it up again. If I set it up again through hardware, then will everything just auto-transfer to the 2nd drive?Again, it depends on the setup. See if your controller supports it. 'mdadm' supports exactly this. If I add a drive to the RAID 1 array, mdadm will automatically synch all the drives in the array.

---

### Post by Roasted on 2006-08-31
It sounds like software raid is more ideal. How can I obtain the software for this?

---

### Post by gerbman on 2006-08-31
> **Roasted said:**
> It sounds like software raid is more ideal. How can I obtain the software for this?For me, it is ideal. It's free (true hardware RAID cards can be expensive), sufficiently fast, and easy to monitor. Might as well give it a shot before you upgrade your hardware.

To install a RAID 1 system, first decide what type of partition layout you want. Personally, I like having one partition for the root filesystem (/), one partition for my home directories (/home), one storage partition (/mnt/storage), and a swap partition.

Next decide which partitions you want to mirror, keeping in mind that software RAID is a little slow when it comes to reading/writing data. For this reason, I only mirror my home and storage partitions. The way software RAID 1 works is that you can only mirror one partition per RAID array, so I have two RAID arrays (md0 and md1) corresponding to home and storage, respectively.

All of this is easily set up using the Ubuntu Alternate install disk. When it's time to edit your partition table:

1) Create any non-mirrored partitions on the first drive (root and swap, in my case), marking the root partition on the first drive as "bootable". Set their filesystem types as you normally would (EXT3 and SWAP for my root and swap partitions).

2) For each partition you want to mirror (home and storage in my case), create a partition with filesystem type "RAID" on _each_ disk (keep partitions in the same array the same size). So, in my case, I have two RAID partitions on each drive - the first partition on each drive is the home RAID 1 array, and the second partition on each drive is the storage RAID 1 array.

3) Start the RAID configuration utility listed in the partition setup menu. For my system, I created two RAID 1 arrays. Each array has 2 active partitions and 0 spare partitions. The active partitions for the home array are the first RAID partitions on each drive. The active partitions for the storage array are the second RAID partitions on each drive.

4) Now you'll see, in addition to your physical drives, two RAID devices listed by the partitioner. Set up EXT3 partitions in each RAID device that take up the entire device (the first RAID device is my home partition, the second is my storage partition). Make sure to specify the mount points accordingly.

5) Save all changes and continue setup. The installer should take care of everything (GRUB, fstab, etc.).

As I mentioned, you can use mdadm to monitor the RAID array.

If you have any questions just ask!

---

### Post by Roasted on 2006-08-31
I don't think I'd get into partitions. I'd like to have just two big open discs. These hard drives have 16meg of buffer so hopefully I won't see any decline in write speed as opposed to my 8meg buffer IDE drive I used before.

Where on the LiveCD do I go to set up software RAID? It'll be a little while till I'm home to test it so I figured I'd ask a while.

---

### Post by gerbman on 2006-08-31
> **Roasted said:**
> I don't think I'd get into partitions. I'd like to have just two big open discs. These hard drives have 16meg of buffer so hopefully I won't see any decline in write speed as opposed to my 8meg buffer IDE drive I used before.If that's the case, then it's even easier. Just allocate a single RAID partition on each drive that takes up the entire drive. Next, configure RAID by creating a single array using the two RAID partitions. Mount the array at / and mark it as "bootable".

I noticed a *significant* speedup when I stopped mirroring my / partition (just mirroring my home and storage partitions). I use 2 Maxtor 250GB, 7200 RPM, 16MB cache drives. Try it for yourself though.> Where on the LiveCD do I go to set up software RAID?It's not on the LiveCD. You'll need to download the Alternate install CD and use that.

---

### Post by Roasted on 2006-08-31
The speedup you encountered, was it a huge night and day difference? Was it just while writing, or was it also while executing programs as well? I'd THINK it would only apply to writing, but figured I'd ask.

Also - little off topic, can you use an IDE and SATA drive on the same system? Nobody seems to know, and my bench lab instructor advises against it. I just want to hook up an IDE drive for about an hour to transfer everything to my SATA drive. 

Where do I obtain this alternate install disc? Can I download it? If so, burn as an image and boot?

---

### Post by gerbman on 2006-09-01
Something funny is going on with my connection, sorry if this is a duplicate.

> **Roasted said:**
> The speedup you encountered, was it a huge night and day difference? Was it just while writing, or was it also while executing programs as well?It was definitely noticeable, especially when booting and when the CPU load was heavy. I'm using 2 250GB, 7200 RPM, 16MB cache drives.

> Also - little off topic, can you use an IDE and SATA drive on the same system? Nobody seems to know, and my bench lab instructor advises against it. I just want to hook up an IDE drive for about an hour to transfer everything to my SATA drive.I had to do the same thing. It shouldn't cause any problems.

> Where do I obtain this alternate install disc? Can I download it? If so, burn as an image and boot?You can download the image from the same place as the other CDs:  [www.ubuntulinux.org](www.ubuntulinux.org). Just make sure to get the Alternate installer, then burn it to CD and boot it up.

---

### Post by Roasted on 2006-09-01
This is getting old. I talked to my cousin and he suggests that I go with hardware raid, he sets up arrays all day long, it's part of his job. I said okay fine. So I go through prepared to format my disks and reinstall linux from the get-go on the new raid1 setup. Well, when I did that, I rebooted. Now, my system will POST, but nothing happens. Screen goes black. The screen stays black.

What the hell is going on? I'm back on my IDE drives now, problem free, and loving it. I'm starting to wonder why I dumped money into a problem like this. :mad: :mad: :mad: :mad: :mad:

---

### Post by gerbman on 2006-09-01
> **Roasted said:**
> This is getting old. I talked to my cousin and he suggests that I go with hardware raid, he sets up arrays all day long, it's part of his job. I said okay fine. So I go through prepared to format my disks and reinstall linux from the get-go on the new raid1 setup. Well, when I did that, I rebooted. Now, my system will POST, but nothing happens. Screen goes black. The screen stays black.

What the hell is going on? I'm back on my IDE drives now, problem free, and loving it. I'm starting to wonder why I dumped money into a problem like this. :mad: :mad: :mad: :mad: :mad:Sorry to hear about the troubles. A couple questions:

1) When you installed the system on the hardware RAID, did one drive show up in the installer or did you see both drives?

2) Is there a setting in your BIOS to boot from the RAID array instead of either drive by itself?

3) Can you return the card you bought? Hardware RAID is better if it works...but it doesn't seem to be working...

---

### Post by Roasted on 2006-09-01
The hardware raid is just a setting I found in bios. There's no "card" or anything.

When I set up raid, it had 2 screens. It had on one side "free drives" and the other "array drives." Array drives had nothing, and my two WD disks were under free drives. I moved both to array drives, then I went to another screen. At all times I saw both disks, except when I restarted. When I'd restart it would display after POST Healthy RAID Array WD 250.1 8349 or some shit. But that's all it'd say, for ONE disk. So after POST, it would "update" me and show me that the array is still active and running (I guess that's what it meant).

---

### Post by gerbman on 2006-09-01
> **Roasted said:**
> The hardware raid is just a setting I found in bios. There's no "card" or anything.

When I set up raid, it had 2 screens. It had on one side "free drives" and the other "array drives." Array drives had nothing, and my two WD disks were under free drives. I moved both to array drives, then I went to another screen. At all times I saw both disks, except when I restarted. When I'd restart it would display after POST Healthy RAID Array WD 250.1 8349 or some shit. But that's all it'd say, for ONE disk. So after POST, it would "update" me and show me that the array is still active and running (I guess that's what it meant).I mean, how many disks were recognized by Ubuntu when you were installing the OS?

---

### Post by Roasted on 2006-09-01
Two.

---

### Post by gerbman on 2006-09-01
> **Roasted said:**
> Two.Right, so the fact that your BIOS identifies the disks as a RAID array is irrelevant. You'll need to use software RAID, which is definitely possible, but you don't sound like you want to bother with it. In any case, good luck.

---

### Post by Roasted on 2006-09-01
I came across these pictures of the BIOS on my motherboard. Check them out.

Now, this is normal, only having one thing listed, right? If I see this, that means I have successfully setup RAID 1 mirroring. Right?

[IMG]http://www.msicomputer.com/support/tshooting/k8n2.jpg[/IMG]



Now, with this picture. Should I have BOTH drives on the right, or just one? I figured I'd only need ONE drive on the right, because only one drive is the true "array" disk. But when I keep one on left, one on the right, it says invalid number of drives selected.

[IMG]http://www.msicomputer.com/support/tshooting/k8n3.jpg[/IMG]



This next picture is normal, seeing just one drive listed... right? I'm assuming that the other drive not listed would be the boot drive, while this one I'm looking at on this screen is the mirroring array drive... correct?

[IMG]http://www.msicomputer.com/support/tshooting/k8n4.jpg[/IMG]

---

### Post by Roasted on 2006-09-01
All right... this is getting old. I went through and tried to set it up again. Everything seemed fine, but then I got disk boot error when I tried to boot. So much for that.

To give you folks some detail of what I see, in BIOS, under "Array List" I see the following.

Boot - yes. ID - 1. Status - Healthy. 

So there's only one drive listed under array list. Is that good?

Then under Array Detail (which I believe is the next screen), I see the following.

Adapt-     Channel-      Master/Slave-     Index-     
1           1            Master            0       WD250
1           0            Master            1       WD250


Then as I reboot, it says DETECTING ARRAY and lists one drive. It lists the drive tagged "0" and it's listed as "Healthy." 

Everything to me looks good. So why the hell am I getting disk boot error?!?!?!


Oh, another important thing, or so I think... when I booted from the LiveCD and installed Ubuntu, it has 2 disks to choose from. If RAID was set up right, shouldn't only 1 be listed? :frown:

---

### Post by gerbman on 2006-09-02
I went though the exact same thing. The BIOS reported that I had a healthy RAID 1 array running; however, the Ubuntu installer still saw two separate disks. If we had a true hardware RAID setup, Ubuntu would only see one disk. I don't know exactly what is going on, but in all my fooling around I could not get hardware RAID 1 to work. My suggestion is to follow the steps I outlined above for software RAID.

---

### Post by Roasted on 2006-09-02
Yeah, I know. :( But there's no reason that this hardware raid is rejecting. ](*,)

---

### Post by dmizer on 2006-09-02
your nvidia raid controller should have come with a floppy ... did you use it?

perhaps it's time to contact nvidia for support on this one.  i don't think this is an ubuntu problem, i think this is either 1) a problem with how your trying to configure your raid, or 2) there is something physically wrong with the raid controller.

edit:
did a bit more research on this.  i've never dealt with nvidia raid before, but it doesn't look to me like it's going to be compatable with linux.  there's a disk you'll have to use for raid drivers.  which means that the nvidia raid is not a hardware raid anyway ... something like those pesky winmodems where the cpu does most of the work rather than the hardware.

true raid hardware is not cheap.  just like hardware modems are not cheap.

---

### Post by HAARP on 2006-09-02
Warning: What you're attempting to do in the BIOS IS a Software RAID! Unless you have a really expensive ($200+) RAID controller, you're using Fake-RAID™
Your BIOS does nothing but tell a driver that you want to use RAID. This driver does the RAID stuff, hence Software. I'm pretty sure there is no Linux driver for whatever board you have, so you should see 2 drives in Linux.
You can use the alternate install CD to set up a real Linux-Software-RAID (which is faster than Fake-RAID!), but you should use an extra partition for /boot. That's about it.
I did the same with RAID0. Works fine.

You CAN use the BIOS to set up your RAID. There is a tool called dmraid which supports Fake-RAIDs. But you can't have the array in your root dir / this way, and it's slower

---

### Post by Roasted on 2006-09-02
So realistically set up 2 partiions... One for /boot, one for everything else. Then I should be good to go?

---

### Post by HAARP on 2006-09-02
Set up swap partitions. I'd use 512MB per drive **(hda1: 512MB; hdb1: 512MB)**
Use the rest of the drives to set up one big partition **(hda2: 60GB; hdb2: 60GB)** - ***But on one drive, leave about 30MB at the end!!!***
There you will set up the boot partition. **(hda3: 30MB)**
Download and burn the Alternative install CD. Boot from it. Tell the installer to format and use the 30MB partition for /boot, and to create an array out of **hda2** and **hdb2**. It's called **md** or something, you'll find it. Once you've set RAID up, you most probably will have a **md0** device. Tell the installer to format it and mount it in **/**

Bold partitions are ***examples***!!

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> So realistically set up 2 partiions... One for /boot, one for everything else. Then I should be good to go?If you want a /boot partition that's fine, but you don't need one. I originally mirrored three partitions (/, /home, and /mnt/storage). Now I'm just mirroring /home and /mnt/storage. Both setups worked for me.

---

### Post by Roasted on 2006-09-02
What's the advantage to splitting up these partitions instead of one huge partition? Speed? Efficiency?

---

### Post by HAARP on 2006-09-02
Swap partitions is something you most probably will need. You can't partitionate an array, so they need extra physical partition(s)
Having 2 of them half the size speeds things up.

I'm not sure if you need a boot partition with RAID1, but it won't hurt.
When using RAID0, you can't read from the array unless the driver is loaded. You can't load the driver unless you can read the array. That's what boot-partitions are for.

---

### Post by gerbman on 2006-09-02
Having a separate /home partition is _extremely_ useful because it allows you to reinstall Linux without wiping out the home directories. All of your personal settings/data/preferences are stored in your home directory, and it's a pain to reconfigure everything after reinstalling (or upgrading, if you do a clean install). During installation, mount your home partition at /home to reuse your old home partition (make sure not to format the partition).

Another reason to have separate partitions is speed (when using RAID). A RAID 1 array can only mirror a single partition, so one option is to install Linux on one big partition (with a swap partition, of course). However, as I mentioned above, mirroring the root (/) partition slowed my system down noticeably (7200 RPM, 16 MB cache drives). By splitting the install into /, /home, /mnt/storage, and swap partitions, I was able to mirror only those partitions (/home and /mnt/storage) that I wanted to, and was able to keep a separate /home partition for later reinstalls.

---

### Post by Roasted on 2006-09-02
ok ok,  I'm getting a little confused. 

Bottom line is, for optimum performance I should set up at least 3 partitions.

First partition - 512 megabytes, for the swap.
Second partition - The bulk of my hard drive (probably 220 gig worth) for regular data.
Third partition - 30 megabytes for the boot section.

Y/N?

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> ok ok,  I'm getting a little confused. 

Bottom line is, for optimum performance I should set up at least 3 partitions.

First partition - 512 megabytes, for the swap.
Second partition - The bulk of my hard drive (probably 220 gig worth) for regular data.
Third partition - 30 megabytes for the boot section.

Y/N?People have different preferences, but I find the following to be best for me:

Partition 1 (10 GB):  /
Partition 2 (25 GB):  /home 
Partition 3 (172 GB):  /mnt/storage
Partition 4 (1 GB):  swap 

I have made RAID 1 arrays for partitions 2 and 3 as described in my earlier post. If you need clarifications on how to make the RAID arrays, just ask.

---

### Post by Roasted on 2006-09-02
Okay. New problem. Imagine that, eh?

I put in the liveCD and went to install server. Was that right? Anyway that's what I did. I set up raid in the way I thought was right, installed the system, rebooted, disk boot failure.

What the f*** is with disk boot failure. It happens all the f***ing time with these drives, yet I know they work cause they're fine when I use them individually.

There isn't some kind of how-to with pictures to walk me through this, is there? :frown:

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> I put in the liveCD and went to install server. Was that right? Anyway that's what I did.The server install might work for RAID, but I've only ever used the non-server install from the Alternate CD. You might want to try it.> I set up raid in the way I thought was right, installed the system, rebooted, disk boot failure.In the installer, you need to mark the root partition as "bootable". There is an option to do this when you are configuring the partition (setting the filesystem type, size, etc.). Make sure this is set.

---

### Post by Roasted on 2006-09-02
What menu do I go to when I put the alternate CD in? Was I right when going to the server install?

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> What menu do I go to when I put the alternate CD in? Was I right when going to the server install?The option you want is "Install in text mode"

---

### Post by Roasted on 2006-09-02
Oh damnit. That's why.

Is the rest basically a walk through? I'll know exactly what I need to do when I see the screen?

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> Oh damnit. That's why.

Is the rest basically a walk through? I'll know exactly what I need to do when I see the screen?The only screens that might not be totally intuitive are the partitioning ones, so have a look at them and post back with any questions.

---

### Post by Roasted on 2006-09-02
So am I to set up the raid first with the alternate disk, then remove the disk, reboot with the livecd in, AND THEN install the OS?

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> So am I to set up the raid first with the alternate disk, then remove the disk, reboot with the livecd in, AND THEN install the OS?No, everything is done in the text-mode installer from the Alternate CD.

---

### Post by Roasted on 2006-09-02
And that'll install the EXACT same Ubuntu OS that I have on my livecd?

---

### Post by gerbman on 2006-09-02
> **Roasted said:**
> And that'll install the EXACT same Ubuntu OS that I have on my livecd?Yup, it's the same exact thing :) They made the LiveCD because most people like a graphical installer, but there is no difference between the two in the end.

---

### Post by Roasted on 2006-09-02
Ran into a problem. While I was setting up the partitions I got a little bit confused, so I ended up settling with a 5 gig swap and a 246 gig (remainder) primary EXT3 partition. I wasn't sure where boot was or what it was labeled, and I got confused by it only being on one drive... just didn't make sense to me. 

Anyway, I got into this screen where I choose raid 0, 1, 5, or cancel. I chose 1, and got the following error:

No unused partition of the type linux raid autodetect are available. Please create such a partition, or delete an already used multidisk device to free its partitions. If you have such partitions, they may contain actual file systems and are therefore not available for use by this configuration utility.

Now, what I did was I went back and deleted my EXT3 partitions on both drives. Still, I got the same error.

What did I do wrong? Was I only supposed to set up ONE drive and let the other one empty with ZERO partitions, then the RAID1 setup would go through and mirror the second drive?


btw reason I used a 5 gig swap is when I went in to delete the existing partitions, the swap was 6.5 gig or something. I figured I'd just use 5.

---

### Post by gerbman on 2006-09-02
You're headed in the right direction, but misunderstanding a couple things. I'll try to clarify. First off, I would suggest a swap partition no larger than 1 GB (any larger isn't usually necessary). Next, a little about software RAID 1 arrays:

A software RAID 1 array is only able to mirror a single partition. You can have that partition mirrored on a number of disks, but every RAID 1 array should be viewed as a single partition. So, if you want multiple partitions to be mirrored (like my suggested partition layout) you'll need multiple RAID 1 arrays. For example, say we want to create a RAID 1 array for your /home partition with a size of 30 GB:

1) Using the text insatller, create one 30 GB partition on each drive with a filesystem type "RAID".

2) Choose the RAID configuration utility and create a RAID 1 array using 2 active partitions and 0 spare partitions. Select the partitions created in step (1) as the active partitions. Exit to the main partitioner screen.

3) A new RAID 1 array has been added that has a capacity of 30 GB. Create a single EXT3 partition on this device that takes up the full 30 GB. Set the mount point to /home.

4) Done.

You'll repeat these steps for any partition you want to mirror (including the root (/) partition). I wouldn't bother with a separate /boot partition.../boot will be included automatically under your root partition by default. Also, make sure your root partition is marked "bootable".

Hope that helps a little.

---

### Post by Roasted on 2006-09-02
Do you have aim? :( There's just a few things I want to get clear and I think it's getting a little useless to use the forums and having to wait for a response.

If so, can you PM it to me?

---

### Post by Roasted on 2006-09-03
Okay. Following the directions of gerbman, I successfully installed RAID1 on my hard disk drives as well as Ubuntu and Grub. But when I boot, it hangs at "boot from cd." 

As normal, it'll say "boot from cd" two times in a row, then quickly GRUB will take over and it'll boot into Linux. Here, it just hangs at boot from cd. Nothing I can do, at all. Immediately after my system POSTs, it detects the healthy array. So I assume my raid setup is just fine.

Can anybody help? Why can't I boot? BIOS settings are fine... ](*,)

---

### Post by Roasted on 2006-09-03
accidental dbl post.

---

### Post by Roasted on 2006-09-03
I figured I'd update some pictures so you folks can see what I'm looking at. Tell me if anything is wrong.


First of all, when I boot up I see this screen.
[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000759.jpg[/IMG]


After pressing F10 and entering the RAID setup...
[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000752.jpg[/IMG]


If I hit enter I see this...
[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000748.jpg[/IMG]


Regular BIOS Screenshots:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000757.jpg[/IMG]

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000758.jpg[/IMG]



After booting from the Alternate CD that I used to set up RAID:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000760.jpg[/IMG]


When I go to manually edit the partition table:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000761.jpg[/IMG]



And the final result where it hangs and never boots up:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000756.jpg[/IMG]

---

### Post by HAARP on 2006-09-03
First of all, deactivate Fake-RAID in the BIOS.
Secondly, why leave 1GB free one the second disk? Use this as swap or something.
Thirdly, leave the partition editor. There should be a option called **md** or something which allows you to set up the RAID

---

### Post by gerbman on 2006-09-03
> **HAARP said:**
> Secondly, why leave 1GB free one the second disk? Use this as swap or something.I agree you can use it for something, but I wouldn't use it for swap. 1GB should be plenty of swap.

Roasted, if you only did what is shown in your screenshots, then you have missed a few steps. You need to enter the RAID setup utility and create the array using the two RAID partitions as active partitions. Please post the following:

1) Exactly which partitions you marked as "bootable"
2) A screenshot showing the final partition layout, which should include the RAID device added with the RAID config utility.

One final thing...I'm wondering if it matters whether or not the swap partition is at the beginning or end of the drive. In all the tutorials I've read the swap partition is always at the end. Can someone else answer this question? Does the bootable partition need to be at the beginning of the drive?

---

### Post by HAARP on 2006-09-03
Swap should be at the beginning of the drive, since it's faster there.
Boot can be at the beginning because older bootloaders have a 1024-cylinders-limit which prevents them from booting from a partition not at the beginning. Doesn't matter with today's bootloaders

> **gerbman said:**
> I agree you can use it for something, but I wouldn't use it for swap. 1GB should be plenty of swap.


Well, make 1x512MB per drive then. Even better, because the kernel supports "raiding" multiple swap partitions. Get the system running and I'll show you how.

---

### Post by Roasted on 2006-09-03
[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000761.jpg[/IMG]

Notice the B directly after 250.0 GB and K? When I selected that partition to be bootable, that B popped up. I assume that's bootable, then.

When I disabled the fake raid in the bios, I got ERROR 17 - cannot mount selected partiion. :frown:


Also, someone just told me they noticed in the last screen the raid controller and usb controller are both using irq 10.


Whoa, so when I set up both of the 250 gig partitions as RAID, then the other thing popped up in the list, something about RAID, and I ran that utility, I'm supposed to do that to both partitions? I only did it for the first one.

I'm surprised I can't find a step by step how-to on this. ](*,)

---

### Post by HAARP on 2006-09-03
When running the **md** (multiple disk) tool, **md0** should pop up in that list.

---

### Post by Roasted on 2006-09-03
Okay. We're still having problems here.

My boot sequence is - floppy, cd, hdd.

I have raid in my bios disabled. When it is disabled, if I go to hard disk boot priority, I have both drives listed, plus something that says "add in cards" or something like that.

If I enable raid in my bios, when I go to hard disk boot priority, only one drive is listed, along with add in cards.

When I boot up, I get error 17: unable to load partition. If I go back to hard disk boot priority when raid is disabled (which I have been letting it disabled), and I switch the two disks (knocking disk 1 down to the 2nd slow, and disk 2 up to the first slot) and boot up, it'll hang at "boot from cd" which is immediately after "verifying dmi pool data." It'll just sit there. Forever. Waiting.

Based off of the following picture, can you tell me if I did anything wrong? 

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000780.jpg[/IMG]

Note how the primary partition of drive A is bootable (you can tell by the B just after the size of the partition). 

So here's my theory. Drive A is bootable. When I boot from drive A, it gives me error 17 unable to load partition. When I switch the hard disk boot priority, and set B above A, then it'll sit at "boot from cd" and never do anything else. In that case, it's trying to boot from drive B, yet drive B isn't set to be bootable so it just hangs out. BUT, as I said, when I boot from drive A I get the error 17. 

How can I get around this?

---

### Post by HAARP on 2006-09-03
Why is the RAID 250GB big when you've got 2 partitions with 250GB **each**?

Did the installer install grub on sda?

---

### Post by Roasted on 2006-09-03
It's raid1 setup. Mirroring. I'm not combining the space of the 2 drives, just copying one another.

---

### Post by neptune39 on 2006-09-03
Isnt that right as he is setting up a mirrored RAID? SO he should end up with 250gb total. I've been reading this thread and its really helping. Im having trouble setting up a RAID 0, I think ive set it up right but GRUB will not install, any ideas? Cheers.

---

### Post by neptune39 on 2006-09-03
Ok seems i posted too quickly as I got it too work, not sure but adding the boot partition seemed to help. Thanks for your help guys (even though it was for someone else:p)

---

### Post by Roasted on 2006-09-03
Whoa whoa, bro. What'd you do to get it to work? You added a boot partition?

---

### Post by HAARP on 2006-09-03
Damn, I'm stupid! Of course its 250GB..forgot it is RAID1....

> **Roasted said:**
> Whoa whoa, bro. What'd you do to get it to work? You added a boot partition?

That did the job for him because he has a RAID0. As I said earlier, you can't boot or load drivers from a RAID0 unless you can read from it. You can't read from it unless the drivers are loaded. That's what boot partitions are for.
Since data in RAID1 is mirrored, you should be able to load the drivers from ONE of the disks before mounting the array as a whole. But you can try adding a boot partition.

---

### Post by Roasted on 2006-09-03
So... no idea what's wrong then? I told myself by Sunday I'd get this working... and there's only so many hours in a day. :( 

What about what neptune said, something about a boot section or something?

---

### Post by HAARP on 2006-09-03
> **Roasted said:**
> So... no idea what's wrong then? I told myself by Sunday I'd get this working... and there's only so many hours in a day. :( 

What about what neptune said, something about a boot section or something?

I edited my last post.

---

### Post by Roasted on 2006-09-03
Not sure how that helps me... I feel like I'm S.O.L. :(

---

### Post by HAARP on 2006-09-03
I've already asked: Did the installer set up grub?
Try diverting about 30MB from one drive for a boot partition. Tell it to be mounted into /boot and set the bootable flag

---

### Post by Roasted on 2006-09-03
I'll try that. And yes, it set up grub.

Grub tries to boot the drive, but I get error 17 with grub, which is unable to load partition.

---

### Post by neptune39 on 2006-09-03
You could try to set up Raid 0 as its simple, if you don't get it working then it might show you that something is wrong with the what your doing. I think now after trying a RAID 0 i would be more prepared for RAID 1.

Question for others, when should I choose RAID 5 over RAID 0. How much space do I lose, how do I recover from a faliure and can I add drives to the array later or is that not possible through a software array. I going to use 2x250gb and 1 200gb if that is important.

---

### Post by HAARP on 2006-09-03
Actually, RAID1 should be even simpler than 0, since no files are being split.

RAID5 depends on what you need. Speed? Redundancy? 5 is, if at all, only a little bit faster than one drive, but it puts quite a load on the CPU compared to other RAID levels. I'd only use it with a real hardware-controller that offloads this.

> **Roasted said:**
> I'll try that.

OK. If that doesn't work, I have one last idea. But let's see first.

Right; I'm off to bed.

---

### Post by Roasted on 2006-09-03
I think *THINK* I got it working.

All I did differently was add a 50 mb partition for /boot.

Now, when I booted up, I got no error. I just got the usual ok, booting to kernel thing you see every time you restart. I log in, no errors. Great. Cool. 

But I want to make sure it's FULLY functional. When I went to system-disks, I saw I had 4 disk drives. This, to me, made me think of the partitions I made because the "4th hard drive" in the list said unallocated space, which would be the 32.9 megabytes of empty space I had leftover as "free space" from earlier.

Just look at these pictures and see what you think.

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000784.jpg[/IMG]

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-1-5.png[/IMG]

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-2-3.png[/IMG]

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-3-1.png[/IMG]

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-4-1.png[/IMG]

Is there ANY POSSIBLE WAY I can make for a DAMN SURE FACT that my second drive is in fact mirroring every single flippin thing that Hard Drive A is doing. I just have so little trust in this thing now considering what I went through to get it to work.

And another thing, why in the hell does a simple 50 gig partition to specifically store the boot files suddenly make it boot? I just don't see what the difference is from having the boot files in the main partition vs it's own partition...

---

### Post by neptune39 on 2006-09-04
Could you just remove one drive to test the other, the try the other way around?

---

### Post by Roasted on 2006-09-04
Okay. Few questions here.

1. In order to get these drives to boot just fine with RAID 1 fully enabled, I had to create a /boot partition on one of the drives. I chose drive A. I was unable to create this partition on both drives, I got an error when I tried to write the partitions to the disk. So I stuck to just using a single /boot partition on drive A. Bam, works fine. But what if drive A dies? Would drive B boot just fine by itself with no /boot partition? I know when I "thought" I got RAID 1 to work, I installed Linux on a single drive and it booted just fine, and I KNOW I set no partitions for it. So, my question is, if drive A goes down, would B be okay to fully boot on its own without the /boot partition that drive A contained? Why do I need the /boot partition? Is it because of having a RAID Array?

2. Assuming drive A did go down, what would I do? I know I'd have to get a replacement hard disk drive, but then what? Would I just plug it in? How would I activate the new drive to fully sync with the existing hard disk drive? Also, the BIG question here is, how would I set a partition on the NEW drive A for /boot, AND have it fully sync with drive B? How would I do all of this?

---

### Post by HAARP on 2006-09-04
Well, you won't be able to boot at all if the drive with the boot partition fails. As far as I've read and heard, you should be able to boot a RAID1 directly without a boot partition, but this doesn't seem to work here. My guess is, that the data layout on a single normal drive isn't the same as on a single RAID1 drive.
This is how booting works:
The BIOS tells the drive to boot. At the very beginning of that drive, even before any partitions, there's some information, including the location of the bootloader. In your case, this location is the boot partition. It then loads the bootloader, which in turn loads the kernel and the system.
When the drive fails, the BIOS can't tell the drive to boot anymore, it's dead. No booting, regardless of your RAID1
Now my idea is, to have another boot partition on drive B. If A fails, you tell the BIOS to boot from B, and everything is fine.
So we have 2 boot partitions, 1 on each drive. Works fine, but as far as I know, you can't mount 2 partitions in 1 directory. This directory is /boot. This dir get's updated with every kernel update, so the boot partitions need to be kept in sync. RAID1 would be perfect for this, but if we do this, we're at the beginning again: Not being able to boot from RAID1.
So either we try to actually boot from RAID1, or we use a script or something to keep the 2 partitions in sync manually. The latter should be easier, and can be automated. I could give you instructions for that.

By the way, your partitions setup is -really- ugly. My recommendation:
sda1: 50MB boot
sda2: 512MB swap
sda3: rest data

sdb1: 50MB boot
sdb2: 512MB swap
sdb3: rest data

Now we just keep the boot partitions in sync with a automated script, and you should still be able to boot, even if a drive fails. You will just need to change the boot drive in the BIOS

---

### Post by Roasted on 2006-09-04
Okay. Explain this then. I set up each drive like this:

512 mb swap
250.4 gb raid
50 mb boot

on BOTH drives.

I got this error:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1000787.jpg[/IMG]

You're telling me it's possible. The computer is telling me it's not. Why?

---

### Post by HAARP on 2006-09-04
No, it's not possible to mount both into /boot.
Just mount the one on the first drive in /boot, we'll set the rest up when the system is running.

---

### Post by Roasted on 2006-09-04
Uh? So... I'm a little confused. You're telling me it's possible to set a boot partition for each drive, but only one drive can have the actual boot partition mounted?

---

### Post by HAARP on 2006-09-04
Exactly. You can't mount 2 things into one folder. Perhaps that's possible, but I don't know how.

---

### Post by Roasted on 2006-09-04
repost due to forums slow speed. ](*,)

---

### Post by Roasted on 2006-09-04
Okay. New problem. I redid the partitions, trying to see why I needed /boot in its own partition while everybody else didn't.

Here's my setup. 

[IMG]http://i2.photobucket.com/albums/y36/Roasted/weeeeee.jpg[/IMG]

When I boot, I get error 17 unable to load partition. It doesn't even give me a list of things to choose from... just, BAM, error 17 unable to load partition.

Why? WHY do I NEED a /boot partition in order to boot? I don't get it.

---

### Post by HAARP on 2006-09-04
My guess is that the MBR does point to the actual RAID-array instead of the partition. which can't work, since RAID drivers aren't loaded yet at that stage. We'll see what we can do about that.

---

### Post by Roasted on 2006-09-04
I wonder why it's not seeing the MBR. That's kind of strange... 

Just answer this for me.

Say I set up Drive A like this:

50 mb /boot
512 mb swap
Remaining space RAID

Then I set up Drive B like this:

512 mb swap
Remaining space RAID

If Drive A dies, my stuff is still on Drive B. When I get a new hard disk drive to REPLACE Drive A, what would I do to get them to sync together, and therefore copy the files from B back onto the new A drive? Would I have to set up the partitions on A? Just tell me what I'd do...

---

### Post by neptune39 on 2006-09-04
Can you add a 30mb boot partition to the raid array instead, this would mean both drives have the boot partion because of the mirroring and shoulod be able to boot independant.

So you have swap and raid on each drive and then in the array a 30mb boot and the rest is free to be partioned as you need.

---

### Post by HAARP on 2006-09-04
Just create a new partition on drive A, it should sany the next time it is started.

> **neptune39 said:**
> Can you add a 30mb boot partition to the raid array instead, this would mean both drives have the boot partion because of the mirroring and shoulod be able to boot independant.

So you have swap and raid on each drive and then in the array a 30mb boot and the rest is free to be partioned as you need.

1. We've already figured out that we can't boot from RAID1, so we need a boot partition. Making the boot partition RAID1 would be stupid now, wouldn't it?
Besides, you can't create partitions on top of a RAID array, sicne the array is already based on partitions.

---

### Post by Roasted on 2006-09-04
I just don't see why I can't somehow make a boot partition that both drives share. I mean, WHY can't I add a boot partition on BOTH drives, but it only be mounted on Drive A? 

That's ABSOLUTELY FINE if I have to go into BIOS to change sh*t around to get Drive B to boot by itself (assuming Drive A would someday die). What I don't want to do, is be stuck unable to use my computer cause one drive died. That's why I got these drives to set up RAID 1, so I could continue using it until my new drive came. Period. :(

---

### Post by HAARP on 2006-09-04
Well, I've got one last idea to get it going the proper way. Contact me.

---

### Post by neptune39 on 2006-09-04
> **HAARP said:**
> 
1. We've already figured out that we can't boot from RAID1, so we need a boot partition. Making the boot partition RAID1 would be stupid now, wouldn't it?
 

Just trying to help mate...:-#

---

### Post by gerbman on 2006-09-04
> **neptune39 said:**
> Just trying to help mate...:-#Don't take it personally neptune, some of us lack what I would call "forum grace".

---

### Post by neptune39 on 2006-09-04
I don't take anything personally... I hate you all...:twisted: 

:-D

---

### Post by Roasted on 2006-09-04
Still not sure what I'm doing yet. 

It's just so hard for me to believe that setting up raid1 is this difficult. I just can't see why you can't control the second drive to directly mirror anything, including partitions, that the first drive does.

But, whatever. Since I can't get the boot loader onto my second drive, if drive A goes down which has the boot loader, what steps would I take to install a NEW Drive A while keeping my information on Drive B intact?

---

### Post by gerbman on 2006-09-05
> **Roasted said:**
> It's just so hard for me to believe that setting up raid1 is this difficult. I just can't see why you can't control the second drive to directly mirror anything, including partitions, that the first drive does.This is a limitation of software RAID. Hardware RAID 1 would be totally transparent to the system.> But, whatever. Since I can't get the boot loader onto my second drive, if drive A goes down which has the boot loader, what steps would I take to install a NEW Drive A while keeping my information on Drive B intact?An interesting note:  if you reboot with the LiveCD, mdadm will automatically recognize your RAID drives and create the /dev/md0 node. So, let's say you lose drive A. When you boot the LiveCD, you should still have a working /dev/md0 (it will just contain the single working drive). You can then create a partition on your new drive A and add it to the md0 array. When you add it, the system will start copying all data from drive B to to the new partition on drive A. This is all great - the only problem is that /dev/md0 doesn't show up in the installer as a candidate install drive. In the installer, you need to be able to mount /dev/md0 as your home (or whatever) directory. If someone can tell us how to get md0 to show up in the installer, we'll be set.

---

### Post by Roasted on 2006-09-05
How much is it to get a hardware raid card or whatever?

This?

[http://www.newegg.com/Product/Product.asp?Item=N82E16816132001](http://www.newegg.com/Product/Product.asp?Item=N82E16816132001)

---

### Post by gerbman on 2006-09-05
We talked about this via PM, but for the benefit of others, that is probably not a true hardware RAID card. Vendors seems to be vague about it, but I think you'll end up paying more than $100 for one.

---

### Post by Roasted on 2006-09-05
Okay. The hell with this software raid. Tomorrow I'm going to read about how to set up scripts, since I've never done it with linux yet.

What I'm going to do is use my first SATA drive as my main drive, and run linux solely off of that. Then I'll set up a script to back up my pictures/music/music videos/homemade porn videos/pictures of my awesome hyundai elantra on my 2nd SATA drive once a day. 

I don't have a problem reinstalling linux if my drive dies, as long as I have a backup of my important stuff. It's just too much to understand right now with raid, assuming my boot drive died in raid and how to work around that. Blah, whatever. DAMN YOU RAID! 

I'll report back with my failure/success story with the script. :cool:

---

### Post by HAARP on 2006-09-05
Well, in this case, you can still have a RAID1. Just with only A bootable.

---

### Post by neptune39 on 2006-09-05
Just out of interest roasted i tried to do what you tried, i.e raid 1 through the installer with out the boot partition and I got the same error, so we must be missing a step, if you had another drive you could install ubuntu on then that would allow you to have the OS separate from the the raid array and would probally give you the best security.

---

### Post by Roasted on 2006-09-05
> **HAARP said:**
> Well, in this case, you can still have a RAID1. Just with only A bootable.

Yeah, true. But here's the way I look at it...

If I set up RAID1 like I did earlier with only A being bootable, it'll be harder to get the array running again as opposed to using the script method. With getting RAID1 working again, I'd have to repartition the new Drive A (assuming A died in the first place) and I'd have to install the boot loader on the first partition of the new drive A, then somehow sync them together. It just seems confusing, and more work than it has to be.

With the script, all I'd be doing is running Linux off of a single hard drive. Then, using the script, copy certain folders over every hour/day/week/month/whatever I specify. So, if my boot drive dies, order a new one, load the full OS, and just copy my music/pictures/music videos back over to drive A. BAM. Just seems easier, and more logical. 

I just have to read up on these cron scripts now. Might anybody suggest a decent site and/or a how-to guide for this?

---

### Post by HAARP on 2006-09-05
Uhm, actually you can't easily backup the boot sector. If drive A fails, you will have to rewrite the bootsector no matter if you backup with scripts or by using RAID1
The only way I can think of to backup the bootsector is to use special programs, it's quite complicated. Or by backing up in raw mode, but that would mean you're doing a full-blown backup everytime.

---

### Post by Roasted on 2006-09-05
Yeah I get what you mean, but in reality I'm doing nothing different than I did with windows.

A would be my linux drive. That's it. Period. Just A. B would just hang out here and sit there waiting to be used. I'd just throw my pictures, music, etc on that drive as a backup. So, if drive A dies, then YES I'll have to go through a COMPLETE reinstallation of linux... BUT BUT BUT BUT BUTTTTTT!!! I'll still have my music, pictures, etc, on drive B. When A gets up and running, I'll just copy them back over.

Now, if B dies. Big deal, I'll still have my functional operating system drive, just buy a new drive to replace it, throw it in, and slap my pictures back on it.

The only thing is, the script would do this automatically for me (as far as writing my pictures and music to the second drive. Later, if a drive fails, I'd have to manually dig them out). 

Question! 

I'm about to format my 2 SATA drives and set one up as my main drive. Should I partition it? Like 50 meg boot, 512 swap, and remainder EXT3? Or is swap only used for RAID? Or should I just let the drive as a big ole partition? Annnnnnnnd lastly should I use the LiveCD or Alternate CD for this?

---

### Post by HAARP on 2006-09-05
I've got a nice little backup script right here.

---

### Post by gerbman on 2006-09-05
> **Roasted said:**
> I'm about to format my 2 SATA drives and set one up as my main drive. Should I partition it? Like 50 meg boot, 512 swap, and remainder EXT3? Or is swap only used for RAID? Or should I just let the drive as a big ole partition? Annnnnnnnd lastly should I use the LiveCD or Alternate CD for this?I would seriously consider making a separate partition just for /home. It will save you tons of time if you reinstall in the future because all your program settings and user data will be re-used. I've never see the point of a separate /boot partition...maybe someone can explain that to me. The LiveCD should work fine for this purpose.

---

### Post by HAARP on 2006-09-05
> **gerbman said:**
> I would seriously consider making a separate partition just for /home. It will save you tons of time if you reinstall in the future because all your program settings and user data will be re-used.

you'll end up with a full home partition. No, thanks.

mv home home2
*install new OS*
rm -r home
mv home2 home

Whats the problem?

---

### Post by gerbman on 2006-09-05
> **HAARP said:**
> you'll end up with a full home partition. No, thanks.

mv home home2
*install new OS*
rm -r home
mv home2 home

Whats the problem?Why would you end up with a full home partition?

---

### Post by HAARP on 2006-09-05
> **gerbman said:**
> Why would you end up with a full home partition?

You always end up with full partitions if you don't use the full space for one partition. Trust me on this one :/

---

### Post by gerbman on 2006-09-05
> **HAARP said:**
> You always end up with full partitions if you don't use the full space for one partition. Trust me on this one :/Obligatory Office Space quote:  "Mmmm...I'm going to have to go ahead and...disagree with you on this one".

It depends on your usage and size of disks. I can't see myself filling up 25GB of home space when I have 170GB of storage. Just won't happen. Your situation might be different.

---

### Post by Roasted on 2006-09-05
Uh, I put EVERYTHING in my home folder. Is that bad? I have my pictures, music, music videos, shared folder for frostwire, and all my torrents download to there.

---

### Post by gerbman on 2006-09-06
> **Roasted said:**
> Uh, I put EVERYTHING in my home folder. Is that bad? I have my pictures, music, music videos, shared folder for frostwire, and all my torrents download to there.That is fine.

---

### Post by Roasted on 2006-09-07
Is that how you guys organize your stuff? Music, pictures, downloads, etc to the home folder?

---

### Post by HAARP on 2006-09-07
I backup everything. That includes home folders.

---

### Post by Roasted on 2006-09-07
Yeah, but Haarp where do you put your music and pictures and such? Store them in HOME?

---

