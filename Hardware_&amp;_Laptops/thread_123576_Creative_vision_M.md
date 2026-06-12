---
title: "Creative vision M"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by Oz_hack on 2006-01-30
Hello just got the new Creative vision M, did have a ipod but that annoyed me,

Anyway i have having problems with it, when i plug it in, my computer mounts it( i checked in dmesg) but doesn't put a icon on the desktop. And i can't access it. 


I installed gnomad 2, which was a deb file, but it couldn't find it (sync) 

I read in one forum that these devices work on MTP ( they seem to have there fingers in every cake) 

Has anybody got one of these working on ubuntu yet, or got MTP working.
Or by any chance is there a way of getting access through wine.

 Its such a brill little thing ( about the same size as a ipod) I don't wish to go back to gates machines

Thanks in advance to any help  

andrew

---

### Post by Oz_hack on 2006-02-01
Well no replys 

Have done a bit of digging (well i emailed creative and asked) 

At the moment there is no drivers built for it on linux  but (

From creative  ( email they sent me)

  "I was doing some digging.... It looks like gphoto2  MIGHT be able to access MTP 
devices. It seems that gPhoto2 has BASIC MTP support. But may be a question of adding the correct configuration in Gphoto2 before files can be viewed.
Looks like the iRiver  has been added as an example."

Hope this helps someone out there, at the moment the only way i have is through samba 


PS linux is the best

---

### Post by Oz_hack on 2006-02-01
Just got another email from creative ( talk about good customer support)

have a look at this link they got  a iRiver T30 working which uses MTP

[http://bys.cauterized.net/?cat=15](http://bys.cauterized.net/?cat=15) 


thanks

---

### Post by Oz_hack on 2006-04-25
Well after months of playing i never got it to work, good on creative for there support thought got a few more emails from them with ideas etc 

So i ended up selling it and buying a USB disc one just plugs in comes up as a hard drive alot easier

---

### Post by ShiftyPowers on 2006-04-28
I unfortunately still have my creative zen m (couldn't commute without it).  What I end up doing is just using my windows laptop to transfer the videos from the network onto the player.  A pain in the a ss but at least it'll hold me over until MTP support is onstream in linux.

---

### Post by drobvice on 2006-05-05
Just wanted to say thanks for keeping this thread updated.  I was thinking of maybe getting this player and now I think I'll wait.

---

### Post by imaiden22 on 2006-08-10
its been a long time since the last post on this thread and I think there have been MANY advancements in the MTP problem...as I remember from some digging of my own, the problem shoudl be solved in the latest build of gnomad and the libs that are available...correct me if i'm wrong folks. I'm actually looking to buy a Vision M and im hoping this isn't a problem anymore so i can enjoy and not have to worry about getting rid of windows for good and feel safe with my music on linux

---

### Post by jshayden on 2006-08-21
[http://blogs.ign.com/namlas/2006/07/12/24727/](http://blogs.ign.com/namlas/2006/07/12/24727/)

Good to know.  I'll be buying one soon.

Josh

---

### Post by Haegin on 2006-10-26
If you compile gnomad2 from source and also compile the libraries libnjb and libmtp then you can use mtp devices under gnomad2 so the vision:m works fine.

---

### Post by romana on 2006-10-30
> **Oz_hack said:**
> Hello just got the new Creative vision M, did have a ipod but that annoyed me,

Anyway i have having problems with it, when i plug it in, my computer mounts it( i checked in dmesg) but doesn't put a icon on the desktop. And i can't access it. 


I installed gnomad 2, which was a deb file, but it couldn't find it (sync) 

I read in one forum that these devices work on MTP ( they seem to have there fingers in every cake) 

Has anybody got one of these working on ubuntu yet, or got MTP working.
Or by any chance is there a way of getting access through wine.

 Its such a brill little thing ( about the same size as a ipod) I don't wish to go back to gates machines

Thanks in advance to any help  

andrew

Theres a nice [howto]("http://ubuntuforums.org/showthread.php?t=199250") on these forums.

---

