---
title: "[SOLVED] Snap shot?"
date: 2008-08-21
forum: General Help
---

### Post by Yezinki on 2008-08-21
Hi there,

How can one take a COMPLETE snap shot/ image of the Ubuntu & Windows OS separately?

Just like using Norton Ghost & Acronis True Image for windows..........not HOT IMAGING but Cold imaging .........as in windows booting in DOS from a boot able CD.........creation/ restoring an image at a specified location.

I have heard that it is possible to take a complete snapshot of both Ubuntu & Windows...........while remaining in Ubuntu environment,coz its much faster?

Hoping like always to hear from you smart people!

---

### Post by forger on 2008-08-21
I think partimage might be what you're looking for:
[http://packages.ubuntu.com/hardy/partimage](http://packages.ubuntu.com/hardy/partimage)
[http://packages.ubuntu.com/hardy/partimage-server](http://packages.ubuntu.com/hardy/partimage-server)

> **Yezinki said:**
> Hi there,
I have heard that it is possible to take a complete snapshot of both Ubuntu & Windows...........while remaining in Ubuntu environment,coz its much faster?


Although it might be possible to take a snapshot of a linux environment while it's working, it's much *safer* and *error-free* to just do it by booting from a live cd.
On the other hand, the application might just be that good to work within a working linux environment :)

---

### Post by forger on 2008-08-21
I also found:
[Mondo]("http://packages.ubuntu.com/hardy/mondo")
(I am just trying to backup a mounted partition, works fine so far)
the command to backup is: sudo mondoarchive

[afbackup-client]("http://packages.ubuntu.com/hardy/afbackup-client") (and [server]("http://packages.ubuntu.com/hardy/afbackup"))

---

### Post by Yezinki on 2008-08-21
Thanks,

1. Does ([http://packages.ubuntu.com/hardy/partimage](http://packages.ubuntu.com/hardy/partimage)) it take a Complete image of Ubuntu?

2. Can it placed on some drive  partition & be restored?

3. Can it be burnt on a optical   media?

4. Hypothetically if one restores it, is it as good as the original........100% accurate?

Regards!

---

### Post by forger on 2008-08-21
You'll need to try it, mondo has a lot of options to backup to optical media and/or hard drives

---

### Post by quibbler on 2008-08-21
Have a look here:

[http://quickstart.phpbb.net/index.php?sid=dac309d51d44da24def951d63e972c55](http://quickstart.phpbb.net/index.php?sid=dac309d51d44da24def951d63e972c55)

regards quibbler

---

### Post by Yezinki on 2008-08-21
thanks!

---

### Post by prshah on 2008-08-21
> **Yezinki said:**
> 
How can one take a COMPLETE snap shot/ image of the Ubuntu & Windows OS separately?

As suggested, partimage will do the job for both Windows and Ubuntu. But specifically for ubuntu, there is a much better option; it's called remastersys.

It will take a complete backup of your Ubuntu installation, and you can even make a live CD out of your (customised) installation, so that if anything happens to your Ubuntu installation, you can boot off the live CD into the familiar setup you've made, rather than the "basic" setup of the original live CD.

---

### Post by Yezinki on 2008-08-21
> **prshah said:**
> As suggested, partimage will do the job for both Windows and Ubuntu. But specifically for ubuntu, there is a much better option; it's called remastersys.

It will take a complete backup of your Ubuntu installation, and you can even make a live CD out of your (customised) installation, so that if anything happens to your Ubuntu installation, you can boot off the live CD into the familiar setup you've made, rather than the "basic" setup of the original live CD.

Thanks prshah,

Where have you been lol.........missed you lol.

I have Ubuntu, Kubuntu, MythBuntu & Xbuntu all running but I like Kubuntu 4 session the most.

Kindly have a look at my post Packages.........where are the live CDs saved?

Where can I install/download remastersys?

Regards!

---

### Post by forger on 2008-08-21
> **Yezinki said:**
> 
Where can I install/download remastersys?


[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by Yezinki on 2008-08-21
Thanks forger

---

### Post by prshah on 2008-08-21
> **Yezinki said:**
> 
Kindly have a look at my post Packages.........where are the live CDs saved?
Where can I install/download remastersys?


Read it, didn't understand it, left it. :) ;)
[Remastersys is here.]("http://www.remastersys.klikit-linux.com/")

---

### Post by qstraza on 2008-08-21
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
this is what i use

---

### Post by Yezinki on 2008-08-21
Which takes a more accurate image & restores exactly?

Out of the 2........remastersys or the other?

Regards!

---

### Post by Yezinki on 2008-08-21
> **prshah said:**
> Read it, didn't understand it, left it. :) ;)
[Remastersys is here.]("http://www.remastersys.klikit-linux.com/")

Extracting Live CDs?

Regards!

---

### Post by Yezinki on 2008-08-21
> **prshah said:**
> Read it, didn't understand it, left it. :) ;)
[Remastersys is here.]("http://www.remastersys.klikit-linux.com/")

hi prshah,

Could you kindly care to see the post...........([http://ubuntuforums.org/showthread.php?t=896402](http://ubuntuforums.org/showthread.php?t=896402)) Live CD/DVD.

Thanks!

---

### Post by qstraza on 2008-08-21
We use G4U in our faculty, we have dual boot of winxp and ubuntu gutsy, we use image the entiry HDD and copy it on ftp server... Its cool if you have to put a new PC in a classroom.

G4U uses well know command 'dd', look around on google ;)

---

### Post by Yezinki on 2008-08-21
Thanks,

Where is the link to download Ubuntu gutsy.......is it different from hardy Heron 8.04?

Regards!

---

### Post by qstraza on 2008-08-21
> **Yezinki said:**
> Thanks,

Where is the link to download Ubuntu gutsy.......is it different from hardy Heron 8.04?

Regards!
Who are you talking to? If answer is me, G4U is a liveCD and dd comand is installed my default on gutsy and heron.

---

### Post by Yezinki on 2008-08-21
> **qstraza said:**
> Who are you talking to? If answer is me, G4U is a liveCD and dd comand is installed my default on gutsy and heron.


Yes I am talking too you.

Where do I get G4U?

Whats the command line?

How do you merge G4U && Ubuntu Hardy Heron?

Regards!

---

### Post by qstraza on 2008-08-21
> **Yezinki said:**
> Yes I am talking too you.

Where do I get G4U?

Whats the command line?

How do you merge G4U && Ubuntu Hardy Heron?

Regards!
You are kiding right?

Just to make it clear, you want to make full snap shot of your windows partition and a full snap shot of ubuntu partition?

If this is the case, then justfuckingoogleit.com for g4u or better yet, let me do it for you, for hit gives you this link [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
there you can download the g4u. 
[http://www.feyrer.de/g4u/g4u-2.3.iso](http://www.feyrer.de/g4u/g4u-2.3.iso) burn this file and than boot that cd, make sure to read the instruction before, how to backup the partition and not the whole hdd.
[http://www.feyrer.de/g4u/#using](http://www.feyrer.de/g4u/#using) this is a howto, read first and do it cerfuly, than if you have questions, ask.

---

### Post by prshah on 2008-08-21
> **Yezinki said:**
> 
Out of the 2... remastersys or the other?


Both should work equally well, but remastersys offers the additional functionality of creating a live CD from your customized installation.

> **Yezinki said:**
> Extracting Live CDs?


> **Yezinki said:**
> 
Could you kindly care to see the post.. Live CD/DVD.


I don't think you are getting the concept of a live CD.

A live CD is a CD which, when booted from, will run the operating system and give all functionality, as though the operating system is installed, but without the need for installation.

This is useful for when you want to try out the operating system, but do not want to take the time to install it, or the inherent risks to your existing data during installation.

As a contrast, the "alternate" CD can be booted from, but you cannot use the operating system until you "install" it to your hard drive.

Considering that the concept of a live CD is not clear to you right now, maybe you should forget about remastersys temporarily, until you have used Ubuntu/Linux for a while. Any of the other backup solutions mentioned here will also do the job for you; you can also see [this thread]("http://ubuntuforums.org/showthread.php?t=874643") for more methods and details on how to backup an entire HDD. (The thread starts slightly off-topic, but after 10-12 posts, there are a lot of ideas on how to create a exact HDD backup, one of which is "dd").

---

### Post by Yezinki on 2008-08-21
thanks prshah,

For the detailed clarification!

---

### Post by Yezinki on 2008-08-21
> **qstraza said:**
> You are kiding right?

Just to make it clear, you want to make full snap shot of your windows partition and a full snap shot of ubuntu partition?

If this is the case, then justfuckingoogleit.com for g4u or better yet, let me do it for you, for hit gives you this link [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
there you can download the g4u. 
[http://www.feyrer.de/g4u/g4u-2.3.iso](http://www.feyrer.de/g4u/g4u-2.3.iso) burn this file and than boot that cd, make sure to read the instruction before, how to backup the partition and not the whole hdd.
[http://www.feyrer.de/g4u/#using](http://www.feyrer.de/g4u/#using) this is a howto, read first and do it cerfuly, than if you have questions, ask.


Hi there,

Exactly I was yanking yourballs..........

Regards!

---

### Post by Yezinki on 2008-08-21
Thanks prshah,

You are so conceise,elaborate, in depth, to the point in all your replies.

Simply GENIUS!!

---

