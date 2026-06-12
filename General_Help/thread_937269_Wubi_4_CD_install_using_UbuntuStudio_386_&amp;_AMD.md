---
title: "Wubi 4 CD install using UbuntuStudio 386 &amp; AMD64"
date: 2008-10-03
forum: General Help
---

### Post by DaTzr on 2008-10-03
[SIZE="2"]I'm interested in going for Ubuntu but am preferring the Studio version so I have a few questions and am looking for experienced/knowledgeable advice. My scenario is this: I'd like to make a (1) DVD to boot/install with but I'd like to be able to use it with my 2 different machines (1 is an AMD Athlon2000 and the other is a AMD64 5000+ Dual Core) but also, I want to help my son who is Iraq where downloads REALLY suk be able to use a copy of this same DVD. Now that I've heard about 'Wubi', it seems like it may be a little less treacherous to try this different OS (currently we run either XP, OS/2 Warp 4 or Vista Ultimate according to the machine). Now, I had already D/L'd the 2 diff studio iso packages (no sign of 'Desktop' & I have 'Alternate' versions but am I correct in that Wubi will not work with those as they are not 'Desktop' iso? Hope also in responding you also see that I want to know if I can have different Studio iso's with Wubi on 1 DVD and  -if-  so do I place Wubi 1 time on the DVD with the other versions alongside and it will allow me to chose?
:confused:

Cheers & Thanks[/SIZE]

---

### Post by Orlsend on 2008-10-04
I am not sure that it will work with the dvd iso, But I know UNetbootin does installs anything to partition.

---

### Post by ago on 2008-10-06
> **DaTzr said:**
> [SIZE="2"]I'm interested in going for Ubuntu but am preferring the Studio version so I have a few questions and am looking for experienced/knowledgeable advice. My scenario is this: I'd like to make a (1) DVD to boot/install with but I'd like to be able to use it with my 2 different machines (1 is an AMD Athlon2000 and the other is a AMD64 5000+ Dual Core) but also, I want to help my son who is Iraq where downloads REALLY suk be able to use a copy of this same DVD. Now that I've heard about 'Wubi', it seems like it may be a little less treacherous to try this different OS (currently we run either XP, OS/2 Warp 4 or Vista Ultimate according to the machine). Now, I had already D/L'd the 2 diff studio iso packages (no sign of 'Desktop' & I have 'Alternate' versions but am I correct in that Wubi will not work with those as they are not 'Desktop' iso? Hope also in responding you also see that I want to know if I can have different Studio iso's with Wubi on 1 DVD and  -if-  so do I place Wubi 1 time on the DVD with the other versions alongside and it will allow me to chose?
:confused:

Cheers & Thanks[/SIZE]

Do not do a single DVD.
Provide the Ubuntu Live CD (8.10), and any separate CD or DVD. Install Ubuntu via Wubi using the Ubuntu Live CD, then boot into Ubuntu and from there you can add other CD / DVDs as software sources in the admin menu. Then you can use applications>add/remove to install any package therein even without internet connection.

---

