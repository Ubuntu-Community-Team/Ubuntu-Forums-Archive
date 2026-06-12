---
title: "Dual Boot Vista/Ubuntu Partition Share Problem"
date: 2008-11-17
forum: General Help
---

### Post by thurst on 2008-11-17
Hello everyone,
I just installed my first version of Linux yesterday by dual booting my laptop with Ubuntu. I followed this guide:
[http://www.daryl.mu/2008/03/05/howto...-media-direct/](http://www.daryl.mu/2008/03/05/howto...-media-direct/)
I have a XPS M1330 and I have it so I can triple boot with the Media Direct button to play DVD's without the harddrive running.
-I made the /home partition ext3
-I installed FS-Driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) in Vista
-I named the /home partition 'Z:' and Vista can see it but it says it needs to be formatted.
-When I load the Partition Editor from Ubuntu it shows my whole HD (250 gb) as 'unallocated 232.88 GiB'.
-When I load the Disk Manager I see 5 partitions:
[IMG]http://www.public.iastate.edu/~thurst/DM.jpg[/IMG]
I really don't want to reinstall Ubuntu or Vista or Media Direct. Can anybody help me share a 190 GB partition between Ubuntu and Vista?
Thanks

---

### Post by cariboo on 2008-11-17
It looks like you have Ubuntu installed already, what is it you are trying to do? 

The link you posted gives me a 404 error. From the sounds of it the howto has you doing thngs that are not needed in my opinion. here is a link to a much beter installation howto:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

The above is a visual guide, that will help you set up the system

---

### Post by thurst on 2008-11-17
Sorry about the 404 link... Here is a working one for the guide that I used
[http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)
I do have the triple boot working among Vista/Ubuntu/Dell Media Direct.  I am just having a problem sharing the /home partition between Vista and Ubuntu.  I can access the /home partition in Ubuntu just fine. 
After I installed the FS-driver, I can now see the /home partition in Vista but it says something like "The drive needs to be formatted".  I want to be able to access the 190 GB partition from both Vista and Ubuntu without reinstalling everything.

---

### Post by Marius Derekus on 2008-11-17
Ubuntu recognizes windows partitions, but i don't think windows recognizes ubuntu partitions. I think Windows just thinks it is a corrupt drive since it does not (if i am correct) know what an ubuntu partition is. I don't know if you can fix that. Ubuntu is specifically made to recognize a windows partition since you will be installing it on either a Mac or Windows computer. Windows is not made to know what an ubuntu pertition is

---

### Post by Marius Derekus on 2008-11-17
Maybe there is something you can download on the internet that allows windows to access ubuntu files.

---

### Post by thurst on 2008-11-17
The FS-Driver was supposed to let vista access the ext3 partition according to the guide.
What do you suggest I do?
I really don't want to reinstall everything.  
Should I format the drive in Vista?
Should I somehow delete the partition from ubuntu and then remake the partition in Vista?

---

### Post by Marcus Derekus on 2008-11-18
What do you wnat to use this partition for

---

### Post by Marius Derekus on 2008-11-18
It is mainly made to read ext2 partitions. Did you read this: [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3) if you do what it says it claims you will be able to access ext3 partitions

---

### Post by thurst on 2008-11-18
I did not read that before but I still don't know how it helps.  I installed the FS-Driver but it didn't work.  Perhaps I should try to reinstall it. 
I want to use the shared partition for all of my media files so I can access them from Ubuntu and Vista.

---

### Post by Arup on 2008-11-18
Have you installed SMB?

---

### Post by thurst on 2008-11-18
I haven't installed SMB.  I don't really know what that is.

---

### Post by Th3Professor on 2008-11-18
...i wouldn't share a partition between vista and /home.

---

### Post by thurst on 2008-11-18
I think it's a great idea so that I can keep all of my songs and photos in one place and access them at anytime.

---

### Post by Marius Derekus on 2008-11-18
> **thurst said:**
> I did not read that before but I still don't know how it helps.  I installed the FS-Driver but it didn't work.  Perhaps I should try to reinstall it. 
I want to use the shared partition for all of my media files so I can access them from Ubuntu and Vista.

It matters because unless you do what they say on that page (which even i find a bit confusing) it WON'T read **ext3** partitions. The program is made to read **ext2** partitions.

---

### Post by Marius Derekus on 2008-11-18
> **thurst said:**
> I think it's a great idea so that I can keep all of my songs and photos in one place and access them at anytime.

Put them all in Windows. Or if you don't want to, then make a separate ntfs partition, then you should have no problem because ubuntu and windows can read that (in case you did not know, which you probably did, ntfs is a windows partition)I don't know about this third OS thingy you have, but it probably does as well.

---

### Post by Mark Phelps on 2008-11-18
My suggestion, which works for me, is to create a logical FAT32 partition.  Both Windows and Ubuntu can read and write such a partition without any problems.  Unless you plan on creating 4GB-sized files, such a partion will work quite well.

---

