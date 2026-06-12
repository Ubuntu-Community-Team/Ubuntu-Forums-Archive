---
title: "Questions about building a server for 12 small clients"
date: 2013-10-25
forum: Hardware
---

### Post by anthony.honciano on 2013-10-25
So I've never used ubuntu, but I'm looking to set up an ubuntu server for small low end pc clients that are only going to stream mp4 files. When building a server, I plan to put one together with enough resources, but I'm not 100% about how many nic interfaces I need.

These mp4's are roughly about 2-5MB in size, and these clients will be connected via LAN. ANd I was planning on connecting a router to the server, and the server will then provide the content to these 12 clients. Should I have two NIC cards? or just one going into a simple router?

Thank you and sorry about such a noob question (we all start from somewhere).

---

### Post by Samuel_Peters on 2013-10-25
From my opinion it doesn't really matter but just try it out with one NIC card first and then two.

---

### Post by anthony.honciano on 2013-10-25
Thanks, Samuel. And just to be clear, I'm going to run the Ubuntu Server, not the desktop. Plus any recommendations on a router?

---

### Post by skimtneer on 2013-10-25
Hi Anthony,

It's not the size of the files that you'll be serving, but how many of them you'll be serving at the same time, and what their bitrate is.  But even then, serving 12 copies at the same time of a 3 Mbps bitrate mp4, that's still only 36 megabits per second which is well within the range of a single NIC.  You'd probably be fine with any of the 16-port routers out there.

---

### Post by The Cog on 2013-10-25
If you are not familiar with Ubuntu, I suggest that you install a desktop version rather than Ubuntu server. The main difference between desktop and server is that server has no GUI - command line only, which you may find slows you down a bit. I would suggest Xubuntu rather than Ubuntu, it will probably feel more familiar than Ubuntu.

I agree 1 NIC will probably be enough.

---

