---
title: "Grub Error 21"
date: 2008-09-22
forum: General Help
---

### Post by Moon 111 on 2008-09-22
Before I begin I just wanted to mention that I've been searching Google for the past hour and a half and couldn't find anything that I understood.

After installing Ubuntu, I tried to boot it up, but after a going through a few screens it said the following and wouldn't let me past it:


> 
Grub loading stage1.5.

Grub loading, please wait...
Error 21


Can someone explain to me in non-technical terms how to fix this? It really has been driving me crazy,

Thanks in advance,
- Moshe

---

### Post by Elfy on 2008-09-22
Not sure that we can make it non-technical, but we can try and make it painless.

Error 21 usually refers to a disk not existing.
 Can you boot the livecd and then open a terminal from the accessories menu, paste this command it and then post here what it tells you.

```
sudo fdisk -l
```

---

### Post by Moon 111 on 2008-09-22
Thank you *very* much for your response. I really appreciate it.

It returned the following:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec24ec24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec24ec24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS


Thank you very much,
- Moshe

---

### Post by Moon 111 on 2008-09-22
EDIT: My bad... Sorry...

---

### Post by Elfy on 2008-09-22
Is this a wubi installation - did you install it when windows was running - because it would appear that you do not have a linux partition.

---

### Post by Moon 111 on 2008-09-22
That's weird... I *did* install it and I gave it a 30G partition.

Well, I assume I should install it again. Should I do anything differently this time.

---

### Post by Elfy on 2008-09-22
If you installed it as wubi then you wouldn't see a linux partition, which is why I asked if you installed it when windows was running.

Personally I would install it as a dual boot - but then I don't have windows to install it the other way.

If you did install it through windows then I'm not sure how to go about fixing it tbh - but we do need to know, _or_ you could delete it from windows and install it as a normal dual boot.

But before you reinstall it can you clear up how you installed it please.

---

### Post by Moon 111 on 2008-09-22
I put in the CD that I burned my .iso file unto and chose "Install" on the menu after the "loading" page with the progress bar.

By the way, thank you very much for helping me out with this. I really appreciate it.

---

### Post by Elfy on 2008-09-22
You're welcome - one more question then - did you reboot with the cd in and get a screen like the  screenshot or like the first screen shown on this wiki page [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Moon 111 on 2008-09-22
Definitely the screenshot that you attached.

---

### Post by Elfy on 2008-09-22
OK - that is somewhat odd. I think you are going to have to reinstall it - just to check - that was the whole output of the fdisk command in post #3.


Edit - it would be nice to have some idea of what > but after a going through a few screens these were

---

### Post by Moon 111 on 2008-09-22
Oh, those were just the standard (at least I think they are) black screen with white text that goes off before you get a chance to read it.

So I'll reinstall it then post the result of the fdisk function?

---

### Post by Elfy on 2008-09-22
Once you reinstall you should be ok - but if you get a problem again - we'll start from there again :)

Good luck

---

### Post by Moon 111 on 2008-09-22
During (re)installation when I was trying to pick the size for my partition it said something along these lines:

> 
An error occurred while writing the changes to the storage devices.

Resize operation aborted.


What's going on!?

---

### Post by Moon 111 on 2008-09-22
By the way, I'm using Windows on this computer too, if that changes anything (It's not working now though...)

---

### Post by Elfy on 2008-09-22
Try to use the partition editor before you do the install - it's in the system > admin menu, open that and post a screenshot of it and also run the ```
sudo fdisk -l
```command again.

Are you installing this on 'normal' hardware, not using raid or anything like that.

Did you check that the download was good before you burnt it - have you used the chekc cd for defects option on the livecd boot menu.

---

### Post by Moon 111 on 2008-09-22
Screenshot attached. If I need to change stuff in the partition editor, how do I do it?

Here's the result of the fdisk thing:

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec24ec24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec24ec24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS


What is raid?

Yes, I used the feature on the live CD menu.

Thanks again for your help. I'd be getting no where without it...

---

### Post by Moon 111 on 2008-09-22
Can anyone tell me how to use the partition editor?

---

### Post by Elfy on 2008-09-22
Hi - if you don't know what raid is it's likely you've not.

Use the resize tool and then move the slider from the right to give free space for the installer - apply.

Now you could make the partitions or leave the free space for the installer to utilise.

---

### Post by Moon 111 on 2008-09-22
More errors :(

See screenshot (attachment).

---

### Post by Elfy on 2008-09-22
What error do you get if you just let it resize the ntfs - does it get more specific.

What windows do you have - if you have vista you will be better off using the vista tool to shrink the partition.

---

### Post by unutbu on 2008-09-22
I think forestpixie is right -- it might be best to use a Vista partitioner to resize the Vista partition. 
Here are instructions on how to do that:
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

The problem is, I believe, that Vista uses unmovable paging files. So an alternative method to overcome this problem is to "disable virtual memory" or "disable the page file" from within Vista. See post #23: [http://ubuntuforums.org/showthread.php?t=838606&page=3&highlight=Vista](http://ubuntuforums.org/showthread.php?t=838606&page=3&highlight=Vista)
Once the page file is disabled, then you should be able to use GParted to resize the partition.

Edit: I'm guessing you have Vista. Please ignore if I'm wrong :)

---

### Post by Moon 111 on 2008-09-22
Sorry for bumping the thread, but since the computer won't boot up I can't use. I really need to.

Thanks

---

### Post by unutbu on 2008-09-22
To get Vista booting again, try lswest's instructions:
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

This will restore your Vista MBR.

If after following lswest's instructions, you get a message saying "Cannot find NTLDR", then boot from the Ubuntu LiveCD, open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and follow meierfra's instructions here:
[http://ubuntuforums.org/showpost.php?p=5247162&postcount=16](http://ubuntuforums.org/showpost.php?p=5247162&postcount=16)

If you run into any trouble or have any questions, post back here.

Edit: If you need to use meierfra's instructions, you'll have to know the "device name" for your Windows partition. In your case it is either /dev/sda1 or /dev/sdb1 (depending on which hard drive Windows is on). If you are unsure, post and we can give you instruction on how to figure that out.

---

### Post by Moon 111 on 2008-09-22
I actually have XP. Should I follow those same instructions?

I would also appreciate it if you could give me for setting up Ubuntu. I've wanted to setup LAMP for quite a while...

---

### Post by Moon 111 on 2008-09-22
> **forestpixie said:**
> What error do you get if you just let it resize the ntfs - does it get more specific.

What windows do you have - if you have vista you will be better off using the vista tool to shrink the partition.

I have windows XP. Do you mean reinstalling it and give you the error message that it produces?

---

### Post by unutbu on 2008-09-22
Moon 111, to get XP booting again yes, you can use lswest's instructions
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

I'm surprised you are having trouble resizing a Windows XP partition. I thought I knew what was going on, but now I am not sure at all. 

Could you please repost something like your screenshot from post #20, except this time click on the little triangle to the left of the words "Shrink /dev/sda1 from 149.04 GiB to 100.16 GiB". This should display more details regarding the error message.

Once you get Ubuntu installed, here are instructions for setting up LAMP: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Elfy on 2008-09-22
This is a bit odd, I can't understand how it is that you even got a grub error in the first place.

Then there is an unallocated partition which could be a restore partition which in one screenshot is at the beginning and in the second is at the end.

There was a thread a while ago where it was necessary to deal with the restore partition/ or there was a bios problem with regard to the partition, unfortunately I don't remember how it was dealt with.

---

### Post by Moon 111 on 2008-09-22
So, um, what would you recommend doing? Just get XP to boot and dump the live CD?

Oh, btw, I seem to have two drives sda and sdb. Should I be using sdb and not sda? Anything that I'm doing wrong that might explain what's happening?

---

### Post by Elfy on 2008-09-22
Well if there is room on sdb to fit ubuntu then there's nothing to stop you installing it there - it's not fussy about where it goes.

So if you could resize sdb I would do that - at the moment I think I'd be glad to just get it installed and I'm sure you feel the same way.

---

### Post by unutbu on 2008-09-22
Moon 111, here is something that deserves special attention: you have two drives with identical sizes and identical partition tables. In Windows they would usually be called C: drive and D: drive. In Linux they are called /dev/sda and /dev/sdb. 

If when using Windows you only see one drive, then it means you are probably using RAID ([http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)). If you are using RAID, then this could be the reason you are having trouble installing Ubuntu the normal way. If you can confirm that you are using RAID, then you might want to try these instructions for installing Ubuntu on a RAID array: [https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)
Using RAID makes life more complicated, though the benefit of RAID seems to be either faster disk access or data redundancy. However, unless you know what you are doing (which I don't) I think RAID is more of a hinderance than a help. If I found myself with a machine with a RAID array, I think I would disable the RAID and use the two drives normally. But this is something you'll have to think about and decide for yourself. My opinion might just be a reflection of my ignorance.

If on the other hand, you see two drives when using Windows, then you are not using RAID. You still face a tricky situation however: The Ubuntu installer will ask you where you want it to install itself. If you say for example /dev/sda1 (i.e. the first partition on the /dev/sda drive) then you need to be careful that Windows is not in /dev/sda1 or else Ubuntu will overwrite Windows. Since you have two disks that look identical, you need to be extra careful at that step in the installation.

This link shows how to mount a partition using the LiveCD. [http://ubuntuforums.org/showpost.php?p=5586420&postcount=3](http://ubuntuforums.org/showpost.php?p=5586420&postcount=3)
By mounting your /dev/sda1 and /dev/sdb1 partitions, you will be able to use the file browser to look inside the filesystems. You would then be able to determine which drive name (sda or sdb) corresponds to your Windows partition.

---

### Post by Moon 111 on 2008-09-23
> **unutbu said:**
> Moon 111, here is something that deserves special attention: you have two drives with identical sizes and identical partition tables. In Windows they would usually be called C: drive and D: drive. In Linux they are called /dev/sda and /dev/sdb. 

If when using Windows you only see one drive, then it means you are probably using RAID ([http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)). If you are using RAID, then this could be the reason you are having trouble installing Ubuntu the normal way. If you can confirm that you are using RAID, then you might want to try these instructions for installing Ubuntu on a RAID array: [https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)
Using RAID makes life more complicated, though the benefit of RAID seems to be either faster disk access or data redundancy. However, unless you know what you are doing (which I don't) I think RAID is more of a hinderance than a help. If I found myself with a machine with a RAID array, I think I would disable the RAID and use the two drives normally. But this is something you'll have to think about and decide for yourself. My opinion might just be a reflection of my ignorance.

If on the other hand, you see two drives when using Windows, then you are not using RAID. You still face a tricky situation however: The Ubuntu installer will ask you where you want it to install itself. If you say for example /dev/sda1 (i.e. the first partition on the /dev/sda drive) then you need to be careful that Windows is not in /dev/sda1 or else Ubuntu will overwrite Windows. Since you have two disks that look identical, you need to be extra careful at that step in the installation.

This link shows how to mount a partition using the LiveCD. [http://ubuntuforums.org/showpost.php?p=5586420&postcount=3](http://ubuntuforums.org/showpost.php?p=5586420&postcount=3)
By mounting your /dev/sda1 and /dev/sdb1 partitions, you will be able to use the file browser to look inside the filesystems. You would then be able to determine which drive name (sda or sdb) corresponds to your Windows partition.

Yes, I do have RAID it seems. Those instructions though weren't about installing Ubuntu on RAID or at least that's what I understood. Can you post the link to one specific tutorial?

Thank you very much for helping me out. I feel like I'm almost done.

---

### Post by Moon 111 on 2008-09-23
I believe I have RAID 1 if that changes anything...

Any help would be appreciated.

---

### Post by unutbu on 2008-09-23
Hi Moon 111, I should warn you I have no experience with RAID, so my advice could very well be wrong. 

There are three sublinks referenced [https://help.ubuntu.com/community/In...20hard%20disks](https://help.ubuntu.com/community/In...20hard%20disks) which discuss installing Ubuntu on RAID arrays:

[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

The last link states:
> 
NOTE: Many aftermarket motherboards tout 'hardware RAID' but it's really not. Instead, it's a software driver with a slight hardware 'assist' from the motherboard; these systems are known as "FakeRAID" in the Linux community. If you're doing a new install, it is better to use the standard Linux drivers. If you're trying to dual-boot an existing FakeRAID setup, or you're insistent on using it even on a new install, you need to follow these instructions, FakeRaidHowto. 

So it appears you need to know if you have a true hardware RAID or a "FakeRAID" setup.
The second link is for FakeRAID, and the third link is for true hardware RAID.
My understanding of what the first link is for is iffy, but it seems to me it is providing instructions on how to set up an LVM (Logical Volume Manager) on top of a RAID array. What for, I don't know :)

Hopefully one of those links can get you to where you want to go.
If you have more questions on how to install Linux on a RAID array, it might be best to start a new thread with the word "RAID" in the title. That might attract more forum readers with the right knowledge. 

Best of luck!

---

### Post by Moon 111 on 2008-09-23
After spending a dayand a half trying to install ubuntu, I have given up. Perhaps I'll try again someday. For now, how can I undo everything I have done when installing Ubuntu?

Thanks,
- Moshe

---

### Post by unutbu on 2008-09-23
Have you tried using lswest's instructions for restoring the MBR? [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

If that doesn't work, then the solution requires better understanding of RAID than what I have. In this case, start a new thread asking how to restore the Windows MBR on a RAID-1 array.

---

