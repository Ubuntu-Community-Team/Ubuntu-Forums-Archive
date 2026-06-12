---
title: "How to mount Windows XP shared directory"
date: 2004-12-10
forum: Hardware &amp; Laptops
---

### Post by therascalking on 2004-12-10
Hi all,

I am wracking my brain trying to get this .. hopefully simple .. thing working.

Here's what I have for a setup and what I hope to accomplish.

PC1: running Windows XP Professional, shares drive called mp3, on workgroup HOME

PC2: running Ubuntu Linux also on workgroup home

What I want to do is mount the mp3 share from my Windows box and have it readable from the Ubuntu box. I wish to do this so I can do nightly rsyncs of my music collection

Things I know:
Samba is installed
Windows box can see Ubuntu box
Ubuntu box can see Windows box

But for the life of me I cannot figure out how to mount the Windows share so it is viewable by Ubuntu. Any thoughts? Ideas?

Any help would be MUCH appreciated!

---

### Post by therascalking on 2004-12-11
I found the problem .. I had to add the smbfs package:

apt-get install smbfs

Once I added that I could mount the Windows XP drive with no problemo!

---

