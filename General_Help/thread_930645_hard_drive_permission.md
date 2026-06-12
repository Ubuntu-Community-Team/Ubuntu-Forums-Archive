---
title: "hard drive permission"
date: 2008-09-26
forum: General Help
---

### Post by lanr01 on 2008-09-26
I have my sytem seeing the 2nd hard drive, but the only way I can use it is logged in as root. how can I change the proerties to allow anyone to use this drive? I looked around and tried changing properties of the drive to allow that, but it wont let in to see the properties to change anything...

Where do I need to go to do this?


Thanks,

---

### Post by scouser73 on 2008-09-26
Hi Ian, open up a terminal, and type **gksudo nautilus** this will fire-up nautilus, from there go to your hard drive, click properties and you can change permissions.

---

### Post by lanr01 on 2008-09-26
> **scouser73 said:**
> Hi Ian, open up a terminal, and type **gksudo nautilus** this will fire-up nautilus, from there go to your hard drive, click properties and you can change permissions.

I have tried that, but it still doesn't give me the use of the properties. I can see where the properties is, but it is very transparent and I can't click on it..

---

### Post by TeXtonyx on 2008-09-26
The next logical step is to try chown from the terminal command line.

---

### Post by lanr01 on 2008-09-26
> **TeXtonyx said:**
> The next logical step is to try chown from the terminal command line.

What is chown? I don't know that one

---

### Post by lanr01 on 2008-09-26
if I right click on the drive icon on my desktop and and pull up properties and click on the permissions tab i get a msg that says the permissions of the "disk" could not be determined.

---

### Post by lanr01 on 2008-09-26
> **TeXtonyx said:**
> The next logical step is to try chown from the terminal command line.

Ok, I figured out that chown was change owner. but when I do try it I get this error msg:

what I did was type chown rick /dev/sdb1 at a command line

and get this:


chown: changing ownership of `/dev/sdb1': Operation not permitted

sdb1 is my 2nd hard drive that I am trying to gain use of... when I setup the partition on this drive, did I maybe not setup a flag or something???

---

### Post by SuperSonic4 on 2008-09-26
Have you tried putting sudo infront of it, especially if root is the owner

I must point out that I don't understand chown so you may want to verify with someone else's reply

---

### Post by emshains on 2008-09-26
Type ```
man chown
```
This will show you wtf is chown!

---

### Post by lanr01 on 2008-09-26
> **SuperSonic4 said:**
> Have you tried putting sudo infront of it, especially if root is the owner

I must point out that I don't understand chown so you may want to verify with someone else's reply

 Yeah, but I still can't get in to do anything to make it useable

 If I was delete the partitions on it and reformat and setup a new partition, would this give me a shot to make it so I can use it?  I can see it there, but I can't add anything to it. The only way I could make a new Directory on it was to drop to root and add the directory. I want to use this drive for all my mp3's and all my downloads and my bbs.. But it wont let me do anything...:confused:

Thanks,

---

### Post by _sAm_ on 2008-09-26
What filesystem has the disk 2 that you cant use? And could you post the chown command you tried?

---

### Post by lanr01 on 2008-09-26
> **_sAm_ said:**
> What filesystem has the disk 2 that you cant use? And could you post the chown command you tried?

I used: sudo chown rick /dev/sdb1

 I tried sudo chown rick /dev/sdb

When I did the 2nd one, I am not sure if it did anything as I saw no error msg and it just returned me to a command line. But after doing that I went back into file manager and I still cant get into the properties for that drive.

as far as file system, it is ext2
 here is a screen shot of gparted for that drive:
[ATTACH]86517[/ATTACH]

---

### Post by kpatz on 2008-09-26
You need to chown the location where the drive is mounted, not the /dev/sdb entry.

So if you have it mounted on /mnt/whatever, do sudo chown rick:rick /mnt/whatever.

---

### Post by lanr01 on 2008-09-26
> **kpatz said:**
> You need to chown the location where the drive is mounted, not the /dev/sdb entry.

So if you have it mounted on /mnt/whatever, do sudo chown rick:rick /mnt/whatever.


Hmmm... Well I am guessing at this point as I too new to this to know for sure, but is the location computer:///  ??????

Here is a shot of the info on this drive when I look at it:
[ATTACH]86518[/ATTACH]

---

### Post by bigbrovar on 2008-09-26
follow this guide i gave a while back [http://ubuntuforums.org/showpost.php?p=5046302&postcount=14](http://ubuntuforums.org/showpost.php?p=5046302&postcount=14) and   [http://ubuntuforums.org/showpost.php?p=5045657&postcount=5](http://ubuntuforums.org/showpost.php?p=5045657&postcount=5)

---

### Post by lanr01 on 2008-09-26
> **bigbrovar said:**
> follow this guide i gave a while back [http://ubuntuforums.org/showpost.php?p=5046302&postcount=14](http://ubuntuforums.org/showpost.php?p=5046302&postcount=14) and   [http://ubuntuforums.org/showpost.php?p=5045657&postcount=5](http://ubuntuforums.org/showpost.php?p=5045657&postcount=5)

thanks so much bigbrovar.. That was what I needed. The visual let me see what I missed.... Now I have all drives working and the system is finally working like I wanted it too.. I just need to get Synchronet installed and be my bbs back up and running again...

---

