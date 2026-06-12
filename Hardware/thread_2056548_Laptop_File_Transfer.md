---
title: "Laptop File Transfer"
date: 2012-09-11
forum: Hardware
---

### Post by Shipper on 2012-09-11
I have a friend who was running Ubuntu on her ASUS netbook. She dropped the netbook, cracking the screen, and, since the machine was a few years old, anyways, decided it wasn't worth a manufacturer repair, and asked me to retrieve files on her hard drive. 

I extracted the drive from the carcass of the netbook and connected it with the SATA cables in my desktop, which was running Windows 7 at the time. When I booted, Windows could see the drive, but couldn't read any of the files. I checked online to see whether there was any way of making file-sharing between operating systems possible, but read somewhere that I wasn't ever going to be able to get Windows 7 to access files on an Ubuntu partition.

Naturally, I installed Ubuntu, but now I have a completely different problem: I distinctly remember creating a 450GB partition, but Ubuntu only sees a 130GB drive called "Ubuntu" and something that it's calling a "107GB filesystem." This utterly mystifies me because, clearly, the 130GB drive can't be my original partition, nor the 107GB; the sum of these partitions is not 450GB, and the drive I'm trying to access is neither 130GB nor 107GB, but 250GB.

Since the numbers don't add up, I'm totally unclear on whether Ubuntu is actually recognizing both drives, or whether it's "partially" recognizing one or both of them.

Keep in mind that I'm completely new to Linux, and hadn't used it at all until last week (though I've grown to like it so much that I think I'll continue using it after all of this is done). I have a decent knowledge of Windows, so I'm not starting totally from scratch, but if someone could please explain to me what is going on, I'd enormously appreciate it. ;)

---

### Post by drdos2006 on 2012-09-11
Disconnect all your drives and connect only your friends drive.

Boot with a live CD, run "gparted", change the flag of your friends Hard Drive from "boot" to not boot. 

Reconnect all the drives again and see if you boot with your machine and that your friends Hard Drive is attached. 

Check your boot sequence in your BIOS as well. Make sure your friends Hard Drive is not in the BIOS sequence.

regards

---

### Post by Paddy Landau on 2012-09-11
Also note that Windows is unable to read Ubuntu's file system (ext4); but Ubuntu is perfectly able to read Windows's file system (NTFS).

---

### Post by westie457 on 2012-09-11
Good suggestion from drdos2006 and a good reminder from PaddyLandau.

You could also install Ext2read to Windows. More info and download from here. 

[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

---

### Post by Paddy Landau on 2012-09-12
> **westie457 said:**
> You could also install Ext2read to Windows. More info and download from here.
Ah, yes, good point. Bear in mind that ext2read is out-of-date, so please install it as read-only (you will be given that option when installing). Doing that will allow you to read the Ubuntu disks, but not write to them, making it safer.

---

### Post by Shipper on 2012-09-20
> **westie457 said:**
> Good suggestion from drdos2006 and a good reminder from PaddyLandau.
 
You could also install Ext2read to Windows. More info and download from here. 
 
[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)
 
Thanks for the recommendation; I think this will turn out to be the easiest solution. I downloaded and installed ext2read. I successfully mounted the Ubuntu partition and I can see all 23GB of files. But when I try copying those files from the Ubuntu partition to my Windows partition, Windows only detects a fraction of them: first it was telling me that it detected only 3.8GB, and now it's saying 4.01GB.
 
 
_[COLOR=#000080][http://imageshack.us/photo/my-images/829/screenshotdbv.png/](http://imageshack.us/photo/my-images/829/screenshotdbv.png/)[/COLOR]_
_[COLOR=#000080][/COLOR]_ 
[COLOR=black]How can I make it copy all of my files? Or are there some file types that I'm simply not going to be able to move?[/COLOR]

---

### Post by Paddy Landau on 2012-09-20
Three potential problems:
[LIST=1]
[*]ext2read is significantly out-of-date. It may be that it simply does not see all of the files.
[*]Windows has more restrictions on file names than does Linux, and it may be that some files cannot be copied.
[*]As the file system was not closed correctly, ext2read may be unable to recover the data correctly.
[/LIST]
I suggest that you boot into Ubuntu. Copy the files from there to Windows.

---

