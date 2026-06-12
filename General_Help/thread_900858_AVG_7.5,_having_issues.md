---
title: "AVG 7.5, having issues"
date: 2008-08-25
forum: General Help
---

### Post by ShinHadoken on 2008-08-25
Ok, I installed the latest version, got all the latest updates. I've even reinstalled this a couple of times. Here's the problem. I tell it to scan, and I give it the path "/", which is the entire file system. In all four tests I've ever attempted (even after reinstalling) somewhere between 5900-6100 files, it quits and throws up the error:
 
/ Cannot open; not checked! Resource temporarily unavailable.
 
I have ran them all with gksudo.
Is this a problem with AVG, or can I correct it by omitting a directory, or changing a setting?
 
Thanks a lot,
 
SH

---

### Post by oldmanteabags on 2008-08-25
if your running a program as a user, then you not have permission to see certain directories and files. 

scan home, this should work. you might want to read up on running avg as root.

clamav is an excellent linux anti-virus software

---

### Post by ShinHadoken on 2008-08-26
Sorry, forgot to mention previously that I've been using gksudo to use it as root.
 
(I use clamav as well, I just want to have a few options going for me.)

---

### Post by ShinHadoken on 2008-08-26
Bump, please.

---

### Post by SammerHammer on 2008-08-26
AVG-AV is not a Linux app, so I don't think it knows how to scan Linux filesystems properly.

Anyways, there is no virus for ubuntu, so why scan?

---

### Post by Super TWiT on 2008-08-26
AVG does have a Linux version.  However to my knowledge it is meant scan for windows viruses on a Linux machine to avoid cross contamination between Linux and a windows machine you may be sharing files with.  Windows viruses are pretty pointless on Linux.  The only way a Windows virus could EVER do anything is if you ran the file in wine or cedega, however, currently even the worst these can do is freeze your computer, that is until you kill wine.  That is one of the joys of Linux is that you don't have to worry about viruses.  The main protection is that you are only supper user when you have to be and not all the time.  That and why get Linux when there are so many windows machines that aren't protected out there!

---

### Post by ShinHadoken on 2008-08-26
Ok, I'm giving up on AVG actually, because here's what I am trying to accomplish. I have friends who may possibly convert to Ubuntu from Windows. These guys are used to how Windows works. The fundamental differences I got across, but they can't get over the fact that there's no GUI security software. Now, I explain to each of them that Linux has no viruses, but if I can get them a GUI virus scanner, they'll have it if they want it. ClamTK solved my problem. Thanks a lot guys!
 
SH

---

