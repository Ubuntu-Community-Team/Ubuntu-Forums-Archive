---
title: "usb external hard drive."
date: 2009-08-09
forum: Hardware
---

### Post by jherskow on 2009-08-09
hi, im a bit of a noob, but i heard i might have trouble, so im gonna ask b4 i buy anything:


i want to buy a usb external hard drive (no power source needed). and i wan to use it to store files, and to move files between linux and windows, just like i can with my ipod and with my flash usb stick.

should i just go ahead and do it and it will work? or do i need to worry about fat32 and ntfs and drivers and programs and all sorts of incompatibility stuff that i don't understand?

just need a quick awnswer,

thanks,

jherskow.


(running jaunty and unr)

---

### Post by .nedberg on 2009-08-09
Stick with fat32 and you will have no problem. NTFS should also work fine, but I always use fat when I want to switch a disk from Win to Linux.

---

### Post by jherskow on 2009-08-09
thx for the response!

the one that i can afford is ntfs. is that going to be a problem for me?

---

### Post by .nedberg on 2009-08-09
No, I don't think it will be a problem. And you could always format it to fat32 with gparted. Windows will not let you make a fat32 partition over 32GB (IIRC), so you will have to use something else to format it. Using it in Windows is no porblem.

NTFS can be tricky with file permissions, but from the use you describe, I don't think that will be a problem for you. I never had any problems. Just remember to unmount before you unplug, both in Linux and Windows!

Limitations of FAT32 in Windows: [http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

Also, remember that FAT32 has a max filesize of 4GB! Windows can read and write to ext file systems (Linux "defaults") with the addition af a driver...

---

### Post by Narada on 2009-08-09
NTFS will work fine in Linux with ntfs-3g.

---

### Post by jherskow on 2009-08-09
> **Narada said:**
> NTFS will work fine in Linux with ntfs-3g.


what is ntfs-3g?

do i need to install/configure it?

---

### Post by .nedberg on 2009-08-09
I think ntfs-3g is installed in a standard Ubuntu. Else you can install it with
```

sudo apt-get install ntfs-3g

```
or search in Synaptic

---

### Post by Narada on 2009-08-09
> The ntfs-3g driver is an open source, GPL licensed, third generation Linux NTFS driver which was implemented by the Linux-NTFS project. It provides full read-write access to NTFS, excluding access to encrypted files, writing compressed files, changing file ownership, access right. 
If it's not installed already, I think
```
sudo apt-get install ntfs-3g
```
will cover it.

-edit-
Bah, beaten to the punch. :P

---

### Post by daniel.v on 2009-08-09
ntfs-3g seems to be part of the stock Ubuntu 9.04 install. You can either click on* **[COLOR=Red]System -> Administration -> Synaptic Package Manager[/COLOR]***, then you'll be prompted for your regular user password, and then click on search on the right side, and enter** [COLOR=Red]*ntfs-3g*[/COLOR]**, and click on search.

or....

Applications -> Accessories -> Terminal
once at the term window, you can type 
***grep ntfs-3g /var/log/dpkg.log***

You should be fine just plugging in your external drive and seeing the system put an icon on the desktop, then a nautilus window should open showing you the contents of said drive. Just as a hint, before I plug in an external USB hard drive, I like to open a term window and type ***tail -f /var/log/messages***. This will show the log file in real time. I do this just to see how the system recognizes the unit. 

If you want to check the partitioning scheme on your new drive, you can do 
***fdisk -l /dev/sdbx***
(where sdbx would be whatever your system calls the drive; it could be something else.)

Since NTFS* is apparently very-well supported in Linux* nowadays, I would not recommend using FAT32*, except where you're going to have a small partition. Your mileage may vary, but I have noticed in the past that FAT32 would fragment quickly and a lot. 

By the way, if you notice any issues with data not writing properly to your external drive, the drive may be defective. Ask on the forum what to do before taking a chance on losing any information. 

Note: All trademarks belong to their respective owner(s).

---

### Post by jherskow on 2009-08-21
Ok, just went and got myself a 500gb WDpassport.
checked ntfs- it's there.

plugged it in.....

nothing. the hard drive's little LED went on, but no response.

please help me, or else i just wasted a large amount of cash (non-returnable) on a shiny new brick.

thanks,

jherskow

---

### Post by jherskow on 2009-08-21
ok, reformatted from fat32 to ntfs, works now, insofar as it shows up and everything. so i started to back stuff up. (allot of stuff) 
so icome back an hour or so later (its on usb 1.1) and the "file operations" window is blanked out, and system monitor says the status is "uninterruptable" and i cannot acsess the drive or anything. the computer was frozen and i couldn't even kill the process. in the end i had to reboot. im not going to try that again till i hear from you guys.

aaarrrrggghhhh.

jherskow.

---

### Post by .nedberg on 2009-08-22
Sad to hear that it is not working for you. It should!

This is what I would do:


[LIST=1]
[*]Do a reformat, preferably from a Windows machine
[*]Be sure to "Safe remove" from windows
[*]Connect to Ubuntu
[*]Start moving things over, little by little, not everything at once
[/LIST]

When you have transfered everything unmount the disk and check that everything is there with a Windows machine.

---

### Post by jherskow on 2009-08-22
yeah, thanks, ill definitely do it little by little now,.

thank!... i wish i had usb 2.0 on this old thing though....so slow!

thanks guys!

---

