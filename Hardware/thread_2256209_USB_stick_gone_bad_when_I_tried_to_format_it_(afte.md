---
title: "USB stick gone bad when I tried to format it (after windows virus?)"
date: 2014-12-10
forum: Hardware
---

### Post by funked up on 2014-12-10
Hello everyone,
I gave my USB stick (Corsair 16GB Flash Voyager usb 3.0) to a friend (who uses windows) to write me some files. He told me that a virus might got on the usb when he copied the files.
I got the stick but several months got by before I opened these files. They were just some mp3 files of his band. Anyway all this time I used the stick with no problem on my computers which both have Ubuntu 14.04 LTS. I even used the usb stick at work with windows 7 without any problems.

 Until I opened these mp3 files. All the files on the stick started randomly to appear with peculiar names and as I can remember they were different every time I tried to open some files.
So I tried to format the USB stick with disc utilities using the "clear all - slow version".
It started ok but when it got to 99% it stoped with an error message I can't recall because it was something very general like "error formating the disc".

After that only 80KB are shown on the flash drive. And it was a 16GB usb stick. Until that moment I never had a problem with this USB stick and I didn't have it for many years so someone could say that it was time for it to go bad.

So my question is:
Is there a way to format it and make it work again when it only shows up as a 80KB usb stick even with gparted?
It was only one partition.

Thanx in advance.

---

### Post by Elfy on 2014-12-10
Try creating a new Partition Table in gparted first, then create your partition(s)

---

### Post by funked up on 2014-12-10
I can't do anything with 78.00 KiB !
I just have a USB stick with a volume of 78 KB instead of 16 GB. Only 78 KB show up in gparted and disc utility.

---

### Post by mörgæs on 2014-12-11
Please post a screen shot from Gparted.

---

### Post by Elfy on 2014-12-11
> **funked up said:**
> I can't do anything with 78.00 KiB !
I just have a USB stick with a volume of 78 KB instead of 16 GB. Only 78 KB show up in gparted and disc utility.

Did you even check? 

I've had similar when dd has gone awry - a stick with 'x' kB - creating a new partition table - starts again and I have the whole stick available again.

---

### Post by sudodus on 2014-12-11
> **Elfy said:**
> Try creating a new Partition Table in gparted first, then create your partition(s)

+1

Try with ***gparted***. If it is not installed, install with

```
sudo apt-get install gparted
```

Select the pendrive at the top right corner, then select the pull-down menu

[I]Device -- Create Partition Table
[/I]
and after that create a new partition and a file system inside it (FAT32 if you want it to work in Windows too).

---

### Post by funked up on 2014-12-11
> **Elfy said:**
> Did you even check? 

I've had similar when dd has gone awry - a stick with 'x' kB - creating a new partition table - starts again and I have the whole stick available again.

Yes I did check. That's why I said that only 78KB show up in gparted!

Here's a screenshot. It's in greek. I guess you know what everything means...
&#945;&#948;&#953;&#940;&#952;&#949;&#964;&#945; = unavailable/unallocated (google translate)

---

### Post by Elfy on 2014-12-11
> Yes I did check. That's why I said that only 78KB show up in gparted!After creating a new partition table?

---

### Post by sudodus on 2014-12-11
Please [try to] create a new partition table as described in post #6. We hope and think that it will make it possible to use the whole drive again.

---

### Post by funked up on 2014-12-11
I've tried that but it doesn't let you create a new partition with less than 1MB.
It can't even see the rest of the USB which is almost 16GB (minus 78KB).

That's my issue. Where is the rest of the storage memory?

---

### Post by Elfy on 2014-12-11
Partition TABLE 

_Not a partition._

Device -- Create Partition Table - once it has created a new partition table - see how big the stick is.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=258499&d=1418325321[/IMG]

---

### Post by mörgæs on 2014-12-11
Off topic: What do you store in the goat partition? A scapegoat?

---

### Post by Elfy on 2014-12-11
> **mörgæs said:**
> Off topic: What do you store in the goat partition? A scapegoat?

That's Tahr :D

14.10 never managed to get a label :)

---

### Post by sudodus on 2014-12-11
You should try to create a partition ***table***, and after that create a new partition. Use the fourth pull-down menu (from left)
[I]
Device -- Create Partition Table[/I]

 [SIZE=4][FONT=Times New Roman]&#931;&#965;&#963;&#954;&#949;&#965;&#951;[/FONT][/SIZE] /I think it is this pull-down entry/

---

### Post by funked up on 2014-12-11
Elfy, sudodus,
I have done everything you suggested. After creating a partition table (this works) gparted won't let me create any Partition because it sees the USB stick as a volume of only 78.00 KiB and an error message appears which sais that I can't create any partition smaller than -1 (MB). How can I create any Partition bigger than 1MB when only 78KB appear?

I've done this already 3 times before you suggested it and another 3 times after and I still get the same results.

Maybe I wasn't clear: even after creating a partition table only 78KB show up.

---

### Post by sudodus on 2014-12-11
Sorry, we did not realize that this was the case. I have one more suggestion. If that does not help, I think your pendrive is broken beyond saving.

Try to wipe it (overwrite with zeros) with mkusb according to this link

[URL="https://help.ubuntu.com/community/mkusb"]https://help.ubuntu.com/community/mkusb

[/URL]***Edit**:*

Wipe the whole device

```
sudo -H mkusb wipe-whole-device
```

Try again with a new partition table and a new partition after wiping.
[URL="https://help.ubuntu.com/community/mkusb"]
[/URL]

---

### Post by funked up on 2014-12-11
No luck again.. Thanx anyway for your time. I really appreciate it!
If there's anything else you might think that I could try please let me know. As far as I know the flash drive is useless (for) now.

---

### Post by mörgæs on 2014-12-11
Since the above command does not work it's a desperate effort, but anyway: You could try to run it over with Killdisk.

---

### Post by funked up on 2014-12-12
I've also tried KillDisk but it "wipes" and "kills" only the 78KB.
Like all other software I've tried so far, it only recognizes 78KB.

---

### Post by sudodus on 2014-12-13
[This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only, then totally 'bricked'.

---

### Post by Reha_Andrew on 2014-12-16
In disk management, right click on th e unallocated space and create new partition this will help you in getting your space.

---

