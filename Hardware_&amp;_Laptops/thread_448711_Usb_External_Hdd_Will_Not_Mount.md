---
title: "Usb External Hdd Will Not Mount"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by Alex-Mcedonia on 2007-05-19
Hi I've had Ubuntu 7.04 for a few days now. I have a IBM(LENOVO) R60e Laptop  Model:0657-3pu 
everything is working fine after a few adjustments. There is only one problem I have a USB EXTERNAL HARD DRIVE Seagate Free Agent Desktop 250GB. The drive was working great under 6.10 but now the only way that I can mount it is to turn the power off and then turn it on.  This works and the drive is shown but when I try to unmount it says that I cant so I have to do it the insecure way. If someone can give me any type of help it will be greatly appreciated. 

Thanks in advance...

---

### Post by tbg58 on 2007-05-27
Had the same problem with my Seagate external 250GB drive.  It auto-mounted fine under Dapper and Edgy, but no joy on Feisty. 
Here's how you can mount it manually.

First do 
sudo fdisk -l
This lists hard drives.  You'll get all your present devices right away, then after a short pause (USB/Disk latency I suppose) you'll see the Seagate drive if it's hooked up and on and your OS sees it as a device.  Mine shows up as device sdc, and the vfat partition is sdc1.

Make a directory as the mount point:
sudo mkdir /media/seagate
Mount the drive
sudo mount -t vfat /dev/sdc1 /media/seagate -o iocharset=utf8,umask=000

Then you can do a df -h to list drives.  You should be able to navigate now.

I'll be back shortly -- on my drive I don't like the vfat format on the file system -- it has an upper limit of 4GB file size and I want to save my backup DVD images on it, so I intend to reformat it using ext3.   When I'm done I'll post a message with instructions on how to do so.  It'll be a new thread, but I'll put "Format Seagate External USB drive with ext3" in the title so it'll be easy to find.

Hope this helps!
Good luck!

Rob in Memphis

---

### Post by tbg58 on 2007-05-28
After I reformatted the drive as ext3, it automounts with no problems.
[http://ubuntuforums.org/showthread.php?t=456689&highlight=seagate+250gb+usb](http://ubuntuforums.org/showthread.php?t=456689&highlight=seagate+250gb+usb)

Hope this helps!
Good luck!
Rob

---

### Post by Alex-Mcedonia on 2007-05-28
Thanks dude I'm just going to reformat the drive in ext3. I have one question: After I reformat the drive in ext3 when i stick it to a windows computer will it recognize it and can it be used ?

---

### Post by Alex-Mcedonia on 2007-05-28
Mine is a ntfs i have the ntfs-config tool and even when I enable write suport I cant get it to write on it. Did you have this problem?

---

### Post by oxygala on 2007-05-29
If you don't have software reading ext3 partitions on windows, no. But if you format it to fat32, it will work both on linux and windows.

> **Alex-Mcedonia said:**
> Thanks dude I'm just going to reformat the drive in ext3. I have one question: After I reformat the drive in ext3 when i stick it to a windows computer will it recognize it and can it be used ?

---

### Post by Rogers on 2007-05-29
[http://www.fs-driver.org/](http://www.fs-driver.org/) <-- this is a windows driver than can read ext2/3.  Have your cake and eat it to!  :KS:KS:KS:KS:KS:KS: :D

---

### Post by willough on 2007-05-29
I have a similar situation and two questions. I have a Seagate 320gb external which I now have formatted for ext3.  It mounts automatically but it appears with the locked symbol next to it when I view it as root.  Even though I have changed both the user and the group to myself all the files open read-only; I am unable to change this whether I am root via Nautilus or myself as user.   There is no entry for this drive in fstab though I have read elsewhere that an entry is not necessarily needed there for an external drive.  Is that true and what do I need to do to change the permissions so I can read write from these files?  Thanks.

---

### Post by RTrev on 2007-07-02
> **willough said:**
> I have a similar situation and two questions. I have a Seagate 320gb external which I now have formatted for ext3.  It mounts automatically but it appears with the locked symbol next to it when I view it as root.  Even though I have changed both the user and the group to myself all the files open read-only; I am unable to change this whether I am root via Nautilus or myself as user.   There is no entry for this drive in fstab though I have read elsewhere that an entry is not necessarily needed there for an external drive.  Is that true and what do I need to do to change the permissions so I can read write from these files?  Thanks.

I realize this is a very old thread, but I'm hoping perhaps it can be revived.  :)

My wife and I just found a deal on a Seagate Free Agent 500GB USB external drive, and all I've done so far is power it up and plug it in.  It came up in Feisty 64-bit just fine, but as the above note indicates, it was mounted a root.  Changing to root, I still can't write to the drive.  I haven't done the fdisk/reformat step yet, because from the sound of the note above I will have the same problem, and perhaps have ruined any chance of returning the drive if that turns out to be necessary.

There is very little in the way of documentation, at least that I've found, but I've seen passing mention of the ability to password protect this drive.  Is it possible that, even after an fdisk and creating a new file system, this password protection could still be in effect?  Perhaps it's something in the firmware of the device?

Does anyone have any suggestions as to whether or how to proceed at this point?  I notice this thread left off with no resolution having been presented, which might be a bad sign.  :(

We probably should have done some research before purchasing this, but it simply didn't occur to me that a drive might be password-protected and they wouldn't tell the purchaser how to get in.  I have a copy of Windows XP in a VMware Server virtual machine.. perhaps I should see what happens in Windows.  If there is some kind of weird password protection, perhaps Windows has a driver that understands it?

Thanks for any thoughts!

Bob

---

### Post by whistlerspa on 2007-09-10
There is an NTFS configuration tool in Synaptic that you can install which enable read/write access to the drive. I installed this and it worked for about a week but now I can't access the drive at all - it just stopped working.

---

### Post by whistlerspa on 2007-09-10
Ok so now after one more reboot with the drive plugged in it's working again - now I'm really confused.

---

