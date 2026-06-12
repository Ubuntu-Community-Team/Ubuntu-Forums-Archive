---
title: "The weirdest thing : my USB stick has changed size??!!!"
date: 2009-07-11
forum: Hardware
---

### Post by delhian on 2009-07-11
Hi everyone! 

I don't really know if this has happened to anyone already or if a topic has already been made for that problem, but this is the first time I've ever seen this. I'm not entirely a beginner on Ubuntu or Linux or computers in general, but I'm far from being a professional. Anyway... 

I bought a 4Go USB stick about two months ago to install Jaunty on my Netbook. Everything worked absolutely fine, Ubuntu works like a charm, everything's perfect. 
I erased every data on my stick in the meantime (which was probably the dumbest idea ever), so I have absolutely nothing on it (I even checked hidden files... nada!). 

Today I wanted to reinstall my system, for stupid reasons not even worth mentioning, and I tried the process again... I was very surprised when Unetbootin told me I had not enough place left on my stick. I checked the properties and it is true : I only have 945Mo left, 4Ko used. But what I really don't get is that the properties indicate that 945Mo is the total size of the USB stick!! 

So my question is : how the hell did that happen and what can I do to rectify it? 

Any ideas?

Lena

---

### Post by earthpigg on 2009-07-11
> **delhian said:**
> 
So my question is : how the hell did that happen and what can I do to rectify it? 

Any ideas?

Lena

who knows how it happened?

easiest way to fix it is probably to format it using gparted, since you have nothing important on it.

```
sudo apt-get install gparted
```

system -> administration -> partition editor


make sure you dont format or partition the wrong drive by mistake!

---

### Post by delhian on 2009-07-11
Thanks for your answer Earthpigg... I thought about formatting about a minute after posting the thread. 
So I just tried it... and it failed! I get it less and less. 

It said there was an error and (again stupidly) I quit Gparted and tried to do it again, only to find that it couldn't act on the stick anymore : the space is said to be "non-allocated" and I can't change anything anymore. The size is the same. 

I'll try to format it in a terminal, although I doubt it would change anything.


Edit : Nope, doesn't change anything... I really really don't get what happened (and I know I shouldn't even try to understand... but hey!).

---

### Post by ajgreeny on 2009-07-11
Your original problem is that the files you deleted will have gone to the local Trash of the usb stick, so will be there, but not visible normally.  I always delete files from my usb drives but fully deleting them (shift + Delete) or right click and use the delete option I set in nautilus preferences.

I think you should be able to empty the trash by showing hidden files and folders and deleting it that way, but as I never need to do it, I'm not certain.  Look in the usb for *.local/share/Trash/files* and you may find the files you deleted.

I do not understand why formatting the usb drive has not restored the full size.  I have often formatted my usb flash drive in the past using gparted, but just remember you must unmount the drive before you can do anything to it.

---

### Post by delhian on 2009-07-11
Thanks for your reply ajgreeny, 

The thing is, as I said, that I did check the hidden files but without success which is the reason why I thought about reformatting... I always check the hidden files when I delete files as well. 

This is extremely frustrating... but I can't help laughing because I think this is too weird!

---

### Post by lindsay7 on 2009-07-11
Read this, I have used this hp tool and it works great.


[http://www.pendrivelinux.com/restoring-your-usb-key-partition/](http://www.pendrivelinux.com/restoring-your-usb-key-partition/)

---

### Post by delhian on 2009-07-11
Hey Lindsay7 and thanks for your reply. 

I'm trying, really... but it still doesn't work. Although I did discover thanks to this tutorial you gave me that there is like an "expert mode" and maybe this is what I should learn how to use. The problem is, it's getting a bit hard for me to understand anything, so I'll try to think it over tomorrow. Thank you all for your help! 

Lena

---

### Post by ajgreeny on 2009-07-11
What exactly was the gparted error you got?  Try again with the drive plugged in but unmounted.  Delete all the partitions you see on the drive, make a new one and then format it to the filesystem you prefer, usually fat32 on a flash drive, but you could choose whatever you want, ntfs or ext3 (but not ext3 if you use it in windows as well).  I can not see any good reason why this would not work; as I said, I have done it in the past without problem.

---

### Post by lindsay7 on 2009-07-11
If you have windows you can just download the HP utility that is shown and clean up your usb with that.

---

### Post by delhian on 2009-07-12
Right, so first of, I don't have Windows at all, so I had to use the manual formatting. 
As for Gparted, the message was there was an error, I can't remember what exactly. I have tried different things inbetween and now the USB stick doesn't even mount... 
When I try to force it it says that there is an error in the file system and suggests that I try the following command : 
$ dmesg | tail 
Which I did (twice), of course, and obtained the following informations : 

The first time : 
[13361.516645] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[13361.521785] sd 4:0:0:0: [sdc] 7827456 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[13361.522501] sd 4:0:0:0: [sdc] Write Protect is off
[13361.522516] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[13361.522526] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[13361.522546]  sdc:
[13361.542935] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[13361.543262] sd 4:0:0:0: Attached scsi generic sg2 type 0
[13371.318212] FAT: bogus number of reserved sectors
[13371.318234] VFS: Can't find a valid FAT filesystem on dev sdc.


So obviously, my disk is still 4Go even if I can't have access to the available space... and as I said, now I can't mount it anyway. 

Has anyone other ideas? Otherwise, well... I'll just have to reinstall my system with my external harddrive... I use my key for that one reason only anyway.

---

### Post by earthpigg on 2009-07-12
> the space is said to be "non-allocated" and I can't change anything anymore.

like the attachment?

right click -> create new partition! :P

---

