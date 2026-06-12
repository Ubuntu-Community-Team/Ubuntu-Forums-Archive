---
title: "Cant reinstall Ubuntu"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by jsweeny on 2009-09-09
I had Ubuntu installed on my computer and then these it said there was a dump error.  After restarting I get Error 18 something about the selected cylinder exceeds max supported by bios.  So I tried to reinstall and now it stops at 5% of scanning partition. Any ideas?  Is my hard drive shot.  I can run it off the disc but just cant install.

---

### Post by lindsay7 on 2009-09-09
I would reformat the drive and try to install again.

---

### Post by QIII on 2009-09-09
Were you installing as a dual boot system?

---

### Post by jsweeny on 2009-09-09
I tried to reformat and it freezes with a progress bar that says formatting partition.  I also am not trying to do dual boot only single boot.  Is it possible that my hard drive is shot.  I can run it from the disc.

---

### Post by lindsay7 on 2009-09-09
How are you trying to format.  What are you using to do this?

---

### Post by jsweeny on 2009-09-09
I am inserting the disc and selecting install Ubuntu. Any guidance in much appreciated.  Thanks.

---

### Post by lindsay7 on 2009-09-09
Start your computer with the live Ubuntu disk.  Go to System/Administration and choose Partition Editor or Gparted (I do not remember which it will list).  Find your drive where you want to install Ubuntu and Format the dirve with the ext3 file system.  You may have more then one partition set up, so in that case delete any partitions until you just have one. 

Once this is done, I would exit out of the live ubuntu  and restart the computer so that you start out fresh. Go ahead and try to install Ubuntu.  If you disk is clean and formated you should be able to follow the installation steps.

---

### Post by jsweeny on 2009-09-10
Ok so I went into the partition editor.  I see two items.  The first one is /dev/sda/1  file system unknown  and has a black box next to it.  It also has a yellow triangle with a exclimation point in it, and size is 146.14 GiB.  The second one is /dev/sda/2 and has a set of keys next to it.  The file system is extended with a white box next to it.  And it is 2.86 GiB in size.  After I deleted the first one it now says unallocated, and the file system says un allocated with a grey box next to it.  It is still 146.14GiB in size.  

Then I clicked on the unallocated partition and then clicked on new.  I am going to leave all the defalts and change the file system to ext3 and then follow your instructions. After I did this the unallocated partition changed to New Partiotion #1 and the file system now says ext3 so here we go. I will post again with the results.

---

### Post by jsweeny on 2009-09-10
So I did all of this and then I realized that there was a place to select a different partition in the upper right hand corner.  it was called dev/sdb/ and i changed the file system on that one to ext3.  Then I tried to install again and when I get to step 3 I get a window that says Warning Device /dev/sdb has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTA. This is the message that I have gotten for the last few times that I tried to install.  The next thing that happends is that there is a progress bar that stays at 50% and says starting up partitioner.  Below the progress bar it says scanning discs.

Now when I run the live disc and try to go to the partition editor it won't open.  It tries but then just stops with the partioion editor.

---

### Post by lindsay7 on 2009-09-10
How many drives does your computer have?  Do you have any usb drives attached?

---

### Post by jsweeny on 2009-09-11
Huh, I do have a 1GB flash drive in one of the ports.  I'll try removing it.

---

### Post by jsweeny on 2009-09-11
So we are making progress.  I was able to get farther on the install.  But it still froze.  When I went to install it again it said that Ubuntu was already on there and do I  want to install it side by side.  So I quit the install and tried to restart but now it says Grub starting please wait... Then below it it says error 15.  But...we are making progress.  Thanks for the help and any help beyond this would be greatly appreciated.

---

### Post by lindsay7 on 2009-09-11
I still think you need to use Gparted to clean up you disk drive by deleting any partitions and formating the drive so that it is just one clean partition, then install Ubuntu again.

---

### Post by jsweeny on 2009-09-12
It freezes when I try to format the drive.  It freezes when I try to install.  Don't really know what else to do.  Do you think that it is shot??

---

### Post by lindsay7 on 2009-09-12
I do not know what to think. Can you try to format the drive using windows?

---

### Post by aljoriz on 2009-09-12
run ubuntu on live and use the gparted to partition your drive.  How about using the entire drive for ext3 file system?

---

### Post by jsweeny on 2009-09-12
I would like to give a screen shot of gparted but I don't know how.  If you could instruct me on how to do that you would see what I see.  Any idea??

---

### Post by lindsay7 on 2009-09-12
Look under Applications/Accesories and find a screen shot tool, take the shot and save to your desktop or other place that you can find.  when you open a post, look for the paper clip on the menu bar. Attach the file from there.

---

### Post by lindsay7 on 2009-09-12
Are you sure that you are unmounting the drive before you try to work on it. Try right clicking the drive when you are in Gparted. Or, you can download and burn Gparted to cd disk which will start up your computer when it is installed in the cd drive. This will insure that your drive will be unmounted when you work on it.

---

### Post by jocko on 2009-09-12
> **lindsay7 said:**
> Look under Applications/Accesories and find a screen shot tool, take the shot and save to your desktop or other place that you can find.  when you open a post, look for the paper clip on the menu bar. Attach the file from there.
Or just press the "Print Scrn" button on your keyboard...

---

### Post by jsweeny on 2009-09-12
I cant attach it, it says invalid file.

---

### Post by lindsay7 on 2009-09-12
Click on the paper clip, pick one of the Browse buttons and go to where your screen shot file is located, then click on upload.  Then click on the paper clip again and attach to your post.

---

### Post by jsweeny on 2009-09-12
It won't upload.  I clicked on upload and it says upload error invalid file.

---

### Post by lindsay7 on 2009-09-12
Screen shots end with .png.  What application are you using.

---

### Post by jsweeny on 2009-09-12
[ATTACH]128378[/ATTACH]

[ATTACH]128379[/ATTACH]
Here are the latest screen shots that I have taken.  I have deleted all I can delete.  I have had it down to only one partition with the ext 3.  But it doesn't seem to matter no matter what I do It always freezes when I try to install.  Now it says that Ubuntu is already installed but it wont run.  It says loading Grub error 15.  I have come to the conclusion that I will have to run this machine off the disc and not boot. Thanks for your help unless these secreen shots help.

---

### Post by jocko on 2009-09-13
> **jsweeny said:**
> [ATTACH]128378[/ATTACH]

[ATTACH]128379[/ATTACH]
Here are the latest screen shots that I have taken.  I have deleted all I can delete.  I have had it down to only one partition with the ext 3.  But it doesn't seem to matter no matter what I do It always freezes when I try to install.  Now it says that Ubuntu is already installed but it wont run.  It says loading Grub error 15.  I have come to the conclusion that I will have to run this machine off the disc and not boot. Thanks for your help unless these secreen shots help.
You need to unmount all partitions before you try to delete them, just like the message in the screenshot says. Right-click the partitions and select "unmount" in the menu. When they are unmounted, the key symbols next to them will disappear.

---

### Post by lindsay7 on 2009-09-13
> **lindsay7 said:**
> Are you sure that you are unmounting the drive before you try to work on it. Try right clicking the drive when you are in Gparted. Or, you can download and burn Gparted to cd disk which will start up your computer when it is installed in the cd drive. This will insure that your drive will be unmounted when you work on it.



The problem is you are not unmounting the drives. see above.  You do have an installation. you need to delete of these partitions and create a new one.  Look at the Gparted documentation for help.

---

### Post by jsweeny on 2009-09-14
Thanks I will try this and get back to you asap.

---

### Post by jsweeny on 2009-09-14
Right clicked on every item listed in the screen shot and unmount is not an option for any of them.  I was going to take a screen shot and post it but the network manager is not working right now.  Going to restart and try again tomorrow. Thanks.

---

### Post by rhardie on 2009-09-14
I am having a similar problem; I had Ubuntu 8.10 dual booted successfully on a system with 3 hard drives and used it extensively.  I wanted a totally Linux system and attempted to load Kubuntu.  Kubuntu absolutely WILL NOT load successfully now.

I actually had to re-install Windows XP Pro again to use my system and make this post.  :-(

I'm going to make my own thread titled "Kubuntu won't Load After Successful Ubuntu Dual Boot"

rhardie

---

### Post by jsweeny on 2009-09-14
Here is the screen shot of what I am not able to do, unmount.  What do you think.  Can I do it from the install menu when it asks me where I want to install?[ATTACH]128564[/ATTACH]

[ATTACH]128565[/ATTACH]

---

### Post by jocko on 2009-09-14
> **jsweeny said:**
> Here is the screen shot of what I am not able to do, unmount.  What do you think.  Can I do it from the install menu when it asks me where I want to install?[ATTACH]128564[/ATTACH]

[ATTACH]128565[/ATTACH]
Well, you can't unmount free space or the partitions that are already unmounted, and to  unmount the swap partitions you have to turn off swap.
Close gparted and run this command in a terminal:
```
sudo swapoff -a
```Then open up gparted again and use it to delete all partitions.

---

### Post by jsweeny on 2009-09-14
Deleted a post that I had already put screen shtos.

---

### Post by jsweeny on 2009-09-14
Is this where I'm supposed to start?[ATTACH]128573[/ATTACH]

---

### Post by lindsay7 on 2009-09-14
Yes, good job. Now click on the unallocated space and choose Partition from the top menu bar and choose "new" then format the space as ext3, then you can install Ubuntu.

---

### Post by jsweeny on 2009-09-14
Ok, so I did exactly as you stated.  Clicked on partition and changed from the ext2 to ext3 and clicked on add.  After about a minute into the operation it froze.  After I restarted with the live disc, this is what I ended up with.  [ATTACH]128584[/ATTACH]  So I will try again and see what happens.  Any idea why it keeps locking up?

---

### Post by jsweeny on 2009-09-14
[ATTACH]128585[/ATTACH] This is what I get when I right click on the partition and click information.

---

### Post by lindsay7 on 2009-09-14
try to click on check  and see what you get, then click on format and format ext3.[ATTACH]128589[/ATTACH]

---

### Post by jsweeny on 2009-09-15
So I did exactly what you told me to format to the ext3 file extension.  And I was able to do that and when I installed it froze on me again.  I am pretty sure that I have a bad hard drive.  Thanks for all the help.

---

### Post by lindsay7 on 2009-09-15
Sorry to hear that.  Good luck on to you.

---

