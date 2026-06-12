---
title: "Same problem...installed Ubuntu and lost all data."
date: 2008-09-12
forum: General Help
---

### Post by TriggerIsHappy on 2008-09-12
I saw the other post for this same problem and didn't want to intrude. I did read the request from cariboo907 and here are my results:

sudo fdisk -l  in Application/Accessories/Terminal equals the following:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x114e6452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Please help me. I lost some very precious data and need it back.

---

### Post by mikewhatever on 2008-09-12
It looks like you've done a clean installation of Ubuntu and there is nothing else on that HDD. Where was the data you lost? It's also not at all clear what other post you refer to.

---

### Post by Cresho on 2008-09-12
if you have a second drive, use partition doctor demo to tell you if you can actually recover the whole partition without looking for files.

there is a demo.   just dont use the drive with the lost partition.  [http://www.ptdd.com/](http://www.ptdd.com/)  it gets tricky in recovering lost partitions since it also looks for other lost partitions.

---

### Post by TriggerIsHappy on 2008-09-12
Mostly home movies and pictures. There were some word documents I needed for future reference. I was wanting to try out Linux and was told to boot from the Live CD and it wouldn't save anything to the HDD but apparently I was supposed to use the CD from Windows, this is what my research is showing me for that effect.

---

### Post by Kumagoro on 2008-09-12
Hold on now... the liveCD erased your data??
How did that happen! Did you click the install icon? Maybe your disk got corrupted?

---

### Post by TriggerIsHappy on 2008-09-12
The install option is what I was told to do. Then to follow the prompts accordingly. I was hesitant when it mentioned erasing all data but I was told everything could be restored. I guess I am screwed. I have no Vista Install CD and now my wife is pissed cause she doesn't like Ubuntu. Just call me an idiot.

---

### Post by Kumagoro on 2008-09-12
If you only wanted to check things out, you should've just played around, WITHOUT clicking the install icon :/

In the meantime... try to get to like Ubuntu, i know it sounds weird but really. OR dont use the PC and get the HDD to a professional data restore, really i dont know how to help you...

---

### Post by aysiu on 2008-09-12
Just follow this tutorial:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by bodhi.zazen on 2008-09-12
We are all sorry for your loss. You may be able to recover *some* data, there are tools such as photorec.

The key is to **STOP** RUNNING from the hard drive before other files are over written.

Run these tools from a live CD, preferably on an image of the HD.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

photorec is in the repos and can be installed on the live CD.

---

### Post by aysiu on 2008-09-12
I'm also a big fan of Photorec.

The link I posted earlier outlines step by step how to use it off the live Ubuntu CD.

---

### Post by bodhi.zazen on 2008-09-12
As always, ... Nice link aysiu  !!!!!!!!!

/me adds to bookmarks

It so happened you posted while I was typing ;)

---

### Post by TriggerIsHappy on 2008-09-12
I am going to try the photorec but I have figured out my first mistake. I downloaded the text version and not the live cd. I am downloading the live CD now to try the photorec. will update when completed

---

