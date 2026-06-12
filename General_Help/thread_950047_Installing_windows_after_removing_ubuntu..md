---
title: "Installing windows after removing ubuntu."
date: 2008-10-16
forum: General Help
---

### Post by smooth_dudes on 2008-10-16
Here goes, im rather new to linux you see, and i got this new laptop, and i thought: "Why not try ubuntu?"... so i did, i ordered a cd and installed ubuntu.
Ive been using it for a month or so, but yesterday i decided that i wanted to run ubuntu and windows as a dual-boot (so that i could play games or such). 
So i backed up my files and i removed the ubuntu partition using gparted from the liveCD. 
Gparted now says that i have one partition which is unallocated and that the filesystem of that partition is unallocated.
So i thought: "Sweet! Now i can install windows!" - but no, when i try to install windows, i get this blue error screen:
***** stop: 0x0000007B (0xF78D663C,0xC0000034,0x00000000,0x00000000)**

After searching a bit on google, i got the impression that this means that the computer no longer recognizes the boot volume and that this could be the drive as a whole, or merely a single partition.

so now im stuck, i got no idea about what to do, so that i can install windows

---

### Post by rraj.be on 2008-10-16
Just try this. . . 


Using the same Gparted make the unallocated partition as NTFS. . . 

then try with the windows cd. . 

It should work. . 

Further there is no need that you should delete the partition before installing windows over Ubuntu.When you start installing windows on any partition, the first work it does is formating that partition. . 

Ok go ahead . .good luck :)

---

### Post by smooth_dudes on 2008-10-17
In order to make it ntfs i have to create a new partition, i chose to create it as a Primary partition.

But that does not change a thing... same error occurs when i try to install windows.

---

### Post by Rich78 on 2008-10-17
What I would do is create a single ext2 partition and reinstall Ubuntu following the install wizard and create a swap partition as recommended.

When you have a fresh working install of Ubuntu, reboot and use the GParted live cd, resize the main ext partition to allow a second partition of type NTFS to be created.

Then reboot with the Windows disc in and follow the install instructions.

Some MS support on the error you've received:

[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

---

### Post by smooth_dudes on 2008-10-17
> **Rich78 said:**
> When you have a fresh working install of Ubuntu, reboot and use the GParted live cd, resize the main ext partition to allow a second partition of type NTFS to be created.
when i create the second partition of NTFS, should i still keep the swap partition?

---

### Post by Rich78 on 2008-10-17
Yes, the swap partition is used by Ubuntu.  Windows won't see or use that partition.

---

### Post by RD1 on 2008-10-17
Question: Are you trying to put Windows back on using the "Restore Disc" that came with the laptop (or that you burned) or are you using an actual Windows install disc?

When you installed Ubuntu, the Boot Sector was over-written and the Grub bootloader was installed.

The "Restore" discs provided by computer manufacturers do not "install" Windows. They merely restore the state of the preinstalled software. This does not write a new boot sector or install the Windows bootloader.

In order to get Windows back on the computer, you will need an actual "Install" disc. This will write a new boot sector and get you up and running. During the install setup, you will be asked to select a drive partition to install to. Follow the on screen directions and delete all partitions and the create one partition of the size that you want used for Windows. Leave the rest of the drive un-partitioned and allow Ubuntu to use the free space during the subsequent install.

After Windows is installed and working, you can then use your "Restore" disc to get the computer back to "Out of The Box" condition. Then, install Ubuntu.

Good Luck,
Rodger

---

### Post by smooth_dudes on 2008-10-17
> **RD1 said:**
> Question: Are you trying to put Windows back on using the "Restore Disc" that came with the laptop (or that you burned) or are you using an actual Windows install disc?

When you installed Ubuntu, the Boot Sector was over-written and the Grub bootloader was installed.

The "Restore" discs provided by computer manufacturers do not "install" Windows. They merely restore the state of the preinstalled software. This does not write a new boot sector or install the Windows bootloader.

In order to get Windows back on the computer, you will need an actual "Install" disc. This will write a new boot sector and get you up and running. During the install setup, you will be asked to select a drive partition to install to. Follow the on screen directions and delete all partitions and the create one partition of the size that you want used for Windows. Leave the rest of the drive un-partitioned and allow Ubuntu to use the free space during the subsequent install.

After Windows is installed and working, you can then use your "Restore" disc to get the computer back to "Out of The Box" condition. Then, install Ubuntu.

Good Luck,
Rodger
Windows was not installed when i bought the computer. The install disk i have is one that came with my old Dell computer. It contains windows xp and SP1. The installation process does not reach a point where i can actually do anything... it just loads alot of stuff, then goes black for a moment while loading. And then the blue error screen appears.

---

### Post by smooth_dudes on 2008-10-17
Alright sorry for double posting, but i have now tried Rich78's suggestion, and it made no deffirence... the exactly same error occured.

i partioned the disk the disk like this:
/dev/sda3 - ntfs - 19.53 GiB
/dev/sda1 - ext3 - 204.67 GiB (ubuntu installed)
/dev/sda2 - extended - 8.68 GiB
 --> /dev/sda5 linux-swap - 8.68 GiB

any idea how i this can be worked out? or what the reason windows fails is?

---

### Post by dremanu on 2008-10-17
I would boot with the Windows CD. 

Then:

1)Delete all your existing partitions
2)Create a new partition where you'll install Windows; Which should be at least 80gigs large, if you want to play games.
3)Leave the rest of your HDD raw
4)Format the new partition using NTFS (Not the quick option)
5)Go through the windows installation

If it works, then install Ubuntu on the unallocated space of your HD. It will automatically set-it up for you. Just make sure when you're installing it, that you don't choose the partition where you've installed windows, or you'll lose that installation.

---

### Post by smooth_dudes on 2008-10-17
> **dremanu said:**
> I would boot with the Windows CD. 

Then:

1)Delete all your existing partitions
2)Create a new partition where you'll install Windows; Which should be at least 80gigs large, if you want to play games.
3)Leave the rest of your HDD raw
4)Format the new partition using NTFS (Not the quick option)
5)Go through the windows installation

If it works, then install Ubuntu on the unallocated space of your HD. It will automatically set-it up for you. Just make sure when you're installing it, that you don't choose the partition where you've installed windows, or you'll lose that installation.
as i stated in one of my previous posts, i am not able to do something like that from my windows cd! As soon as i boot from it, it starts the installation process, which after a little while fails (the error message i mentioned in the topic).

---

### Post by dremanu on 2008-10-17
That's right, I see it now. I can think of a few things that can be going-on with your situation, for instance:

1) You could have a defective CD. Possible solution: Use your Ubuntu installation, if it's working, to download a copy from the web, burn it to a new CD, and use your key to install into your system.

2) You could have a defective HD, or a defective CD/DVD drive. You can find software to help you run diagnostics on your drive. You may have some defective sectors that are creating a problem for the windows installation. 

3) Perhaps you are overclocking your system. This can crash a fresh installation.

It's most likely to be something to do with your installation CD.

---

### Post by smooth_dudes on 2008-10-17
well im definetly not overclocking my system :P, and i dont think its the dvd drive either, because it can run other cd's...

so you are propably right about the cd, but its just strange, because not very long ago i managed to install windows xp in virtualbox, using that same cd...

---

### Post by jerome1232 on 2008-10-17
I just wanted to point out sometimes those OEM discs will not install on a hardware configuration that's different than the computer they came with. I had an xp install cd from dell or compaq (Don't remember) that would tell me to shove it if I tried to install to any computer that wasn't the original.

---

### Post by smooth_dudes on 2008-10-17
> **jerome1232 said:**
> I just wanted to point out sometimes those OEM discs will not install on a hardware configuration that's different than the computer they came with. I had an xp install cd from dell or compaq (Don't remember) that would tell me to shove it if I tried to install to any computer that wasn't the original.
yeah that makes good sense, but then why can it be installed in virtualbox? is it because virtualbox somehow can eliminate that fact?... and in that case should i just buy a new xp cd? :/

---

### Post by jerome1232 on 2008-10-17
> **smooth_dudes said:**
> yeah that makes good sense, but then why can it be installed in virtualbox? is it because virtualbox somehow can eliminate that fact?... and in that case should i just buy a new xp cd? :/

I don't know seems like if my thought was correct that cd would give problems on virtual box too. Perhaps others were correct and the cd is damaged. I guess since you know it works in a VM you can try it there again for a test.

---

### Post by Ameneon on 2008-10-17
0x7B is the "INACCESSIBLE_BOOT_DEVICE" BSOD, of which typical explanations is virus/malware (unlikely in this case) or missing drivers. Since you state that this is a new laptop, it could well be a driver issue if, say, your system is using a SATA disk or the HDD for whichever reason otherwise is not accessible by Windows (in very old versions, I don't recall if SP1 is sufficiently old or not, HDDs over a certain size were not recognized either), thus what I first would check is simply whether the laptop manufacturer has a driver for their HDD on the support site, I know Dell has that kind of stuff, and I would guess other vendors would as well in some form or another.

Then put that driver on a USB stick or similar (depending on the format it's shipped in you might need to extract and fiddle around a little to get it floating as it'll not be the .exe or .zip version of the driver you need, but rather the extracted version or a file from it.

That'd be my guess at least.

---

### Post by codingquest on 2008-10-17
hi dremanu.....i too faced the same problem...but it was resolved after i uninstalled ubuntu ant then i tried to install windows first and then ubunt......You could try this out......

---

### Post by TeXtonyx on 2008-10-17
When you say you got a new laptop did you mean brand new or new to
you? If it is brand new, do you have a hidden partition which lets
you install a basic OS and drivers. Often the boot key is F11. Or
it should come with a recovery cd if it doesn't come with a regular
OS install cd. dremanu's advice is pretty good.

You don't want to delete all partitions if you have a hidden partition
it might have Vista which has its own partition resizer.

Otherwise, delete all partitions including Ubuntu. Installs have 
failed because during a previous install attempt, the Windows
install files are left on the drive when the install fails.
So have the entire drive unpartitioned and unallocated. 

Try the XP install again, and if you get far enough, install to
the whole drive, don't leave free space for Ubuntu at this point.
If the install doesn't go through the XP +SP1 cd isn't going to
work. I still think my recommendation will work at this point.
After XP is installed, use the Ubuntu live cd to carve out a
partition for Ubuntu. This space (say 20GB+) should be unallocated.

The reason is that when you do the live cd install to hard drive
later, you can pick "use largest free space" guided. Don't mess
with the first choices of resizing your XP partition because it
is slightly more risky. 

If you want your XP install to be very safe, use install grub to
the Ubuntu boot partition at Step 7 under advanced (not hd0).
Otherwise Ubuntu will install to the MBR and you will temp lose
the ability to boot XP if something happens to Ubuntu. This means
you will use free Bootpart to write the 512 boot sector and to
boot.ini on the XP root, C:\

If that sounds tricky, then leave the default in place at step 7
and grub (menu.lst) will boot Ubuntu and provide an XP option.
This method (MBR) is highly reliable, but not the surest way of
maintaining an uninterrupted access to the Windows OS. I think
it is pretty rare to sell a laptop without an OS or recovery cd.

---

### Post by pickboy87 on 2008-10-17
Honestly the problem sounds to me like the OEM disc doesn't like your computer. I would either try to get a hold of a fresh non-OEM version of Windows XP by either a friend, purchasing it, or *other means* and trying that.

Windows should when it asks to install come up with an option to format/delete the partitions. Delete all the partions, format the drives in NTFS and installing windows that way.

---

