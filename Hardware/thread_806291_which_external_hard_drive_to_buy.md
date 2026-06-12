---
title: "which external hard drive to buy?"
date: 2008-05-24
forum: Hardware
---

### Post by grashdur on 2008-05-24
I need to get an external hard drive that's bigger and faster than my 7-year-old 20GB Pockey, and this time I want one that is immediately plug-and-play compatible with Ubuntu, Windows, and Macintosh. Any recommendations?

---

### Post by bwhite82 on 2008-05-24
I could be wrong, but I thought that all external USB drives fall under the category "mass storage devices" and utilize a universal driver in the kernel? So it wouldn't really matter which you got.

---

### Post by Steve413z on 2008-05-24
I usually go with whatever one is the cheapest price per gigabyte. However, I don't look for anything that high performance, cause I just use my external hard drives for backup/etc. 

(check best buy, they often have some really good deals on hard drives, the last 2 external drives i have gotten were western digitals from best buy)

---

### Post by nebben11 on 2008-05-24
You also want to check to see if you have usb 2.0. ubuntu wouldnt see my 80gb 2.5 ide ext hdd on usb 1.1 but after installing a new usb 2.0 nic chiped card it did. I'm now happy as a peach in my mouth ;)

---

### Post by grashdur on 2008-05-25
Thanks for the feedback. 

@ Soldierboy: When I plug my Pockey external HD to my computer running Ubuntu, the drive receives power from the computer and the LED turns on red. The drive doesn't mount on the computer, nor is it listed in the media folder. This is the same behavior I get on a computer running Windows if I haven't yet installed the drivers from the Pockey's little CD. This is why I'm assuming that not all hard drives are immediately compatible with Linux. 

On the other hand, perhaps the external HD is not noticed because it's formatted with NTFS? But I thought Gutsy Gibbon could see NTFS but just not write to it. 

@ nebben11: I'm not sure what USB 2.0 is. Is it included in Gibbon? I also looked in Add/Remove Programs, and in Synaptic Package Manager, but didn't see it listed.

---

### Post by Steve413z on 2008-05-25
> **grashdur said:**
> 
@ nebben11: I'm not sure what USB 2.0 is. Is it included in Gibbon? I also looked in Add/Remove Programs, and in Synaptic Package Manager, but didn't see it listed.

USB 2.0 is a hardware specification, if your computer is less than 8 years old, you should be ok

---

### Post by nebben11 on 2008-05-25
> **grashdur said:**
> 
@ nebben11: I'm not sure what USB 2.0 is. Is it included in Gibbon? I also looked in Add/Remove Programs, and in Synaptic Package Manager, but didn't see it listed.

grashdur is right. I would also try different ports. on my desktop the front is usb v1.1 and the back is usb v2.0 here is a good read on usb [http://www.lammertbies.nl/comm/info/usb-specification.html](http://www.lammertbies.nl/comm/info/usb-specification.html)

---

### Post by grashdur on 2008-05-25
nebben11, thanks for the helpful link. So I see USB version is about the hardware. Since I bought my computer new in 2002 I assume I have version 2.0. Also, previously when I had Windows installed on this same computer, I was able to use the Pockey external drive with no problem (once I installed the driver for Windows). So I think it's an Ubuntu/hardware issue.

---

### Post by nebben11 on 2008-05-25
I did find this:
INSTALLING THE POCKEY FOR USE WITH LINUX
To be able to use Pockey in Linux, take the following
steps.
1. Plug in and turn your Pockey on after Linux has
booted. You should do this in your “root”
account.
2. Next, use whatever partitioning tool to see if the
Pockey is recognized and the partition is seen.
3. Create a mount point in folder mnt. You may
name this folder whatever you want, “pockey” for
example.
4. Next, add the following line into FSTAB:
/dev/sda1 /misc vfat noauto,user 0 0
At this point, you may choose to mount the Pockey
through command line, or you may create an icon
on the desktop for the Pockey.
In order to mount the Pockey using command line,
type the following:
Mount –t vfat /dev/sda1 /pockey

This was taken from page 11 from [http://www.pocketec.net/downloads/POCKETECmanual.pdf](http://www.pocketec.net/downloads/POCKETECmanual.pdf)
let me know if it works for you

---

### Post by nebben11 on 2008-05-25
oh forgot use "sudo" before the commands hence you login as root

---

### Post by grashdur on 2008-05-25
Wow. Sounds cool. 

But in step 2, the device was not listed. I used System Monitor > File Systems. 

And step 3 I don't understand: I don't know how to create a mount point in the folder mnt -- I have the folder, but it's empty.

I do see the fstab file in my /etc folder, but I'll hold off on that until I can resolve the previous steps.

---

### Post by nebben11 on 2008-05-25
Try this it might work
Create a folder in /mnt/ or /media/ and name the folder &#8220;pockey&#8221;
then put this in the terminal 
> sudo mount &#8211;t vfat /dev/sda1 /pockey

---

### Post by grashdur on 2008-06-04
2 nebben11: I'd like to try that out, but I'm having problems: Apparently I don't have permission to create a folder in those folders. I tried logging in as administrator, but still no go. 

I tried going into terminal and typing "sudo su" in order to get root privileges in order to obtain the needed file/folder permissions. This has worked before on a previous install. But still no go: I am not recognized as root, who is the owner of those system folders.

Perhaps the only option in this case is to log in as root, but I've forgotten how I did that before and I don't have any notes on that. 

Help?

---

### Post by grashdur on 2008-06-07
To nebben11: Sudo wasn't working for this purpose, so I figured out again how to log in as root. I created the folder in /mnt, entered the command as you suggested, then made the folder in both /mnt and /media, and tried again. Both times I got the following message: 

mount: mount point /pockey does not exist

Then I went back to those Pockey manual instructions, and also tried making the recommended change to the fstab file. I tried the same command again to mount the Pockey, but got the same error message. 

But I did manage to find the Pockey listed among my devices -- perhaps because this time I plugged it into the other USB port. 

What I see is: 82801CA/CAM USB Controller > UHCI Host Controller > POCKEY FLOTEC

But I still can't see the Pockey showing up anywhere else, nor find any way to access its files. I just rebooted, and tried again entering the command to mount the device. Still no go. 

What do you think, shall I throw in the towel? For now I think I'll see if I can contact the company, and if no results from that I'll give up.

---

