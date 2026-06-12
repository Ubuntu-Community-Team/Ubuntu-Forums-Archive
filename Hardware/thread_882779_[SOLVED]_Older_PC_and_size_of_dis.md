---
title: "[SOLVED] Older PC and size of dis"
date: 2008-08-07
forum: Hardware
---

### Post by graabein on 2008-08-07
Hi, I recently got a [Compaq Evo D51S]("http://www.epinions.com/content_342199602820") without a harddrive that I want to use as a File and Print server along with other things. I'm pretty new to fooling around with hardware so I'll just come right out and ask it: 

What harddrives can I put in this thing? I'm talking size here. 500 GB? More? I found this [link]("http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1218119475009+28353475&threadId=1181258") but they don't discuss size.


Dang, hit enter when I was editing post in preview. Screwed up thread title :)

---

### Post by tamoneya on 2008-08-07
basically you need it to be an IDE drive.  Here is the only 500 GB ide drive I could find on newegg:[http://www.newegg.com/Product/Product.aspx?Item=N82E16822147008](http://www.newegg.com/Product/Product.aspx?Item=N82E16822147008)

As for the OS limitations ubuntu will be fine.  The mention about the problem with the bios: there is a pin you can set on the back of the harddrive that allows the drive to pretend to be smaller than it really is just while the bios is loading.  Then afterwards you get the full 500GB.

---

### Post by graabein on 2008-08-08
My colleague has the same machine and he got a 500 GB to run just fine. I'll go with that. 

But how much noise is 29 dBA? Is it tolerable? I'm not necessarily having the box in my living room anyway, but do you think busy disc activity will be annoying?

---

### Post by tamoneya on 2008-08-08
> **graabein said:**
> My colleague has the same machine and he got a 500 GB to run just fine. I'll go with that. 

But how much noise is 29 dBA? Is it tolerable? I'm not necessarily having the box in my living room anyway, but do you think busy disc activity will be annoying?

29 dBA isnt that bad.  It wont be a whisper but it also isnt a jet engine.

---

### Post by graabein on 2008-08-08
Thanks. I got it installed and have put Ubuntu 8.04 server edition on it. Installed File & Print, SSH, CUPS and one more I think. No X yet. Trying to get by without...

But how should I partition the 500 GB? Like this?:
[LIST]
[*]/
[*]swap
[*]home
[/LIST]
Where **home** is the storage I want available on my network. 

Where is the natural place to create the "root" directory for my share? Under *media*, *mnt* or *home*? Not under my default user I take it?

---

### Post by evets25 on 2008-08-08
> **graabein said:**
> My colleague has the same machine and he got a 500 GB to run just fine. I'll go with that. 

But how much noise is 29 dBA? Is it tolerable? I'm not necessarily having the box in my living room anyway, but do you think busy disc activity will be annoying?

I also do sound tech stuff, so I might be able to help you out a little bit here... I know that I do sound, I have a decibel meter that I use to keep an eye on how loud it's getting, and I try to keep it below 90dBA, or 85dBA, depending on the event and who the audience is. ;) So that's 90dBA for music, with like a full band, playing at a level that is approaching "too loud" for some. A rock concert might be louder, at like 95-100dBA.  Below 15-20 is like a whisper, So 29dBA is not very loud at all, but it's still noticable.

EDIT: Also, remember that the sound will get muffled be the case of the computer and whatnot, and some of it will get drowned out by other ambient noise in the room.

2nd EDIT: > **graabein said:**
> Thanks. I got it installed and have put Ubuntu 8.04 server edition on it. Installed File & Print, SSH, CUPS and one more I think. No X yet. Trying to get by without...

But how should I partition the 500 GB? Like this?:
[LIST]
[*]/
[*]swap
[*]home
[/LIST]
Where **home** is the storage I want available on my network. 

Where is the natural place to create the "root" directory for my share? Under *media*, *mnt* or *home*? Not under my default user I take it?

I just noticed this post, so I'll edit instead of double-posting...

I have a very similar setup with a 500Gb HD on my desktop, and the way I have it setup is that I have a partition for "/" (20Gb), a partition for swap (1 Gb), a (very small) partition for /boot (25 Mb), and the rest for my main storage partition that I put in ~/storage (that is, /home/username/storage). My reasoning for this is that I want root and /home all to be on the same partition, but my data to be seperate from them. That way, when I do a fresh install, I just copy over a few settings files and some of my .program folders in the home directory to "~/storage/backup" and the restore then on my clean install. This "~/storage" folder is shared so that I can access all my videos and music and documents from any computer on the network. 

Also, I recommend NOT naming your storage folder "home", since this is the name of the directory in the Linux filesystem where user accounts and settings are stored, and this will probably confuse both you and your computer. I call my folder where I store data and stuff "storage" which makes sense to me. You can call it whatever you want, but "home" might get confusing.

---

### Post by graabein on 2008-08-08
I'm not sure I got that... Can you type it out again a little bit clearer?

Partitions:
[LIST]
[*]/ 
[*]swap 
[*]boot
[*]storage
[/LIST]

Then make a directory on the root called **/storage** that you map up to the storage partition and share it with Samba?

I've been using GNU/Linux for quite some time but I'm not that used to setting up and partitioning systems.

I've seen both **/mnt/harddrive** and **/home/samba** on the net.

---

### Post by graabein on 2008-08-21
I went with 5 GB for **/** and **/home** and the rest for **/mnt/share1**. Swap is 1,5 GB.

Do I have to format my shared partition as NTFS? I can't find it in the partition part of the Ubuntu 8.04 server install (*use as*). Is FAT32 the same thing? I'm going to use the machine as a fileserver for my media, so I might have lots of small mp3's on it as well as large videos.

**Update:** Asked around on #ubuntu and no, I didn't have to use NTFS so I kept ext3.

What *mount options* do I want? Default suggestion is **relatime** which I figure is just fine.

---

