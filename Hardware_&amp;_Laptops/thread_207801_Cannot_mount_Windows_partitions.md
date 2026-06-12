---
title: "Cannot mount Windows partitions"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by newagelink on 2006-07-02
I receive the following error message when I attempt to navigate to /mnt/(my windows drives):
[img]http://www.danielbridges.info/files/img/linux/cannotmount.png[/img]
I don't know what could've gone wrong with the installation. I deleted the partitions I'd used for Mandrivalinux 2006, and, after failing to figure out how to designate two new ones for Ubuntu, I just left it unallocated, and selected the option "Use largest portion of free space," (or whatever it says)... the Mounting points that were configured after that were, I believe, the default, something like /dev/hda1 and /dev/hda2, or /media/hda1 and /media/hda2 or something ...

... now, mnt is showing up as empty, cdrom and cdrom0 are the only things under media, and they're not under dev ...

It's at computer:/// ... My C: drive is showing as "31.1 GB Volume" and my D drive (automatically created as a backup disc, from Windows) is "6.8 GB Volume". When I doubleclick either, I get the error shown above.

Any help would be greatly appreciated!

---

### Post by aysiu on 2006-07-02
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by newagelink on 2006-07-02
Ah, thank you!

Um, I have practically no prior experience with Linux (as if it wasn't obvious.) What are the chances of me messing up my Windows partition? I don't think it's very likely, if I understand mounting correctly -- it's kind of like plugging in a USB jumpdrive, and then "Safely Remove Hardware" (in Windows) before taking it back out again?

I guess I'm not really sure what mounting actually *does*. I'm going to keep reading the manuals, though, as well as checking other resources ...

Ugh. My sound decided to quit working -- it lists "Camera" as an option for Audio?? (I have a Logitech webcam plugged in.) :'(

---

### Post by aysiu on 2006-07-02
If it's NTFS and you mount it according to the instructions I linked to, you won't mess up your Windows partition.

If it's FAT32, you can accidentally delete files, just as you could in Windows.

---

### Post by newagelink on 2006-07-03
Ah! Yay, it's NTFS ...

Well, that's cool. If I read the instructions correctly, this'll allow me to write to it as well as read? (That would solve one of my remaining problems in my switch from Windows to Linux. The only others I have are 1) iTunes (or more specifically, my iPod) and 2) wireless signal? and 3) webcam.)

---

### Post by aysiu on 2006-07-03
No, FAT32 you can read/write
NTFS is read-only.

You can't have iTunes without Crossover Office, which costs money. You can, however, interact with your iPod using Banshee, AmaroK, and/or Gtkpod.

I don't know anything about wireless or webcams, unfortunately. Someone else here may.

---

### Post by EinA on 2006-07-03
Hi All, (my first post)
I have the same problem, with the same error message.
error: device /dev/hda9 is not removable
error: could not execute pmount

I had a look at the link to "Mounting Windows Partitions in Ubuntu"
which shows you how to edit the fstab file which I think requires rebooting
As I'm running from the Live CD. editing the fstab file would not work?

I tried unmouting - error message not mounted
tried mounting -  can't find /dev/hda9 in /etc/fstab or /etc/mtab

So how do you mount NTFS with a live CD?

Another thought, I would think that the majority of people trying the Live CD would be from a windows back ground and they would want to access their files from windows. (I wanted to see how videos played)
I do know for technical reasons that NTFS is read only.
So why not make NTFS mount automatically?

---

### Post by aysiu on 2006-07-03
I don't know why NTFS doesn't just mount automatically. This functionality has been available in Knoppix for a long time. Maybe Ubuntu will enable it with the next release--who knows?

In the meantime, you're right... with a live CD, you don't edit the /etc/fstab. Instead, you'd do this: ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda9 /windows -o nls=utf8,umask=0222
```

---

### Post by mllr on 2006-07-03
aysiu, its difficult to use iPod in linux? What software do you recommend? (Banshee, AmaroK, or Gtkpod)

---

### Post by aysiu on 2006-07-03
You know, I've used an iPod on Ubuntu only once or twice, so I'm probably not the best person to ask.

---

### Post by mllr on 2006-07-03
hmmm, and have somebody that i would ask? s;

thx

---

### Post by aysiu on 2006-07-03
Well, don't ask anyone in particular--just ask.

If someone sees, "Hey, aysiu, what do you think about this?" she may not answer because the question was not directed to her.

And it's a good idea to start a new thread for new questions. Otherwise, people will see "Cannot mount Windows partitions" and assume the thread is about mounting Windows, not using your iPod.

---

### Post by mllr on 2006-07-03
thx aysiu, im creating =)

---

### Post by ChiendeRue on 2006-07-04
You will love amaroK
All functionalities add / delete / recognises iPod no problem
It's far better than iTunes

I got on your thread because I can not mount my old linux partition.
Which commends should I use?

CDR

---

### Post by newagelink on 2006-07-04
Eesh, nested topics within a ... thread ... thing ...

(Yeah, so I should go to bed now.)

I tried using amaroK -- crap tried to synchronize my iPod, scaring me half to death thinking it had deleted 55 GB of music ... Granted, I should have never paid that absurd amount ...

I guess I'll be reading the amaroK user manual -- Help functions? I don't know -- before I try connecting it again. I wasn't too impressed with amaroK; it all seemed to be about playlist this and playlist that ... I was actually fine with iTunes' playlist-handling, once I got used to it.

And I guess I'll get back on-topic by saying that I'll be trying the commands tomorrow ... oh, shoot ... how do I set up my NTFS to read and write? I don't have to convert from NTFS to FAT32, do I? :( (What is the difference between the two, exactly?) Couldn't I lose data by converting ... (I guess I should stop being an idiot and back up my data.)

---

### Post by newagelink on 2006-07-07
> **ChiendeRue said:**
> You will love amaroK
All functionalities add / delete / recognises iPod no problem
It's far better than iTunesI'm reading through the manual now; no luck so far ... *heads over to Software Support and stuff*

Once I [get my iPod working to at least what it was with iTunes in Windows]("http://ubuntuforums.org/showthread.php?t=211197"), then I'll come back and fix -- remount? -- my Windows partitions ...

Thanks again for your rapid reply, aysiu!

---

### Post by newagelink on 2006-07-16
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)Thank you so much! It appears to have worked perfectly.

Now I just have to figure out how to make it writeable ... I hope I don't have to convert it to FAT32. :( (If I must, why?)

---

### Post by ORBiTrus on 2006-07-16
NTFS can be written to using Captive or, some new-fangled FUSE based design.  It hit the news hard recently.  Anywho, NTFS isn't all that hot.  A nice simple method which isn't unstable (I've had FAT lock up on me in the past, requiring a remount, and I don't trust any NTFS drivers) is to use a server.  Filesystem of UFS/JFS/XFS depending on OS and contents...  a 486 works well here.

Why you have to convert is the easy part though - because Microsoft Corp. has a patent on the NTFS filesystem (and FAT, though it's a little too distributed to enforce - like MP3s) and won't let anyone see the specs.  Therefore, short of reverse-engineering the filesystem, or using an emulated approach (Captive), no one can use it.  Go Software Patents (they really aren't that bad an idea, just in the age of intellectual property organizations, they show their faults)!

Also, I echo using Amarok as your iPod manager, it's quite mature there.  You might also like Quod Libet, my personal favourite GTK media player, but I don't have an iPod [iPod << competition], so I can't tell.  But there's probably some half-written, buggy Portable Media Device abstraction layer out there.

---

