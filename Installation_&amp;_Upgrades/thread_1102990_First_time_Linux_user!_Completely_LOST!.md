---
title: "First time Linux user! Completely LOST!"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by adadk on 2009-03-22
I've used Windows all my life. This is completely new territory to me. Heck, I don't even know DOS!
I bought a server for my gaming clan to collocate in a datacentre so I can stop forking over cash to GameServers. GS uses Linux on its servers however I'm unsure which version they use. To get my feet wet so to speak, I downloaded and installed Ubuntu 8.10 Server Edition. I assumed that it would have some sort of desktop. If it does, I do not see it. And being an absolute Linux virgin, I have no idea on how to get there.
All I see is some sort of login screen. 

adekuyper@adadk:~$

I downloaded the PDF version of the Ubuntu Pocket Guide but even that shows Ubuntu being setup with a GUI in place.
Please, what do I do next?

---

### Post by sookun on 2009-03-22
hmmmm server edition?

type startx to see what hap

---

### Post by adadk on 2009-03-22
Apparently xinit wasnt installed, so it prompted me to do so. As a result:

[img]http://www.f-thirteen.net/adam/server/U810SE_1.jpg[/img]

---

### Post by LiamWilson on 2009-03-22
simple. Type sudo apt-get install ubuntu-desktop

---

### Post by Calmor on 2009-03-22
Server edition does not come with a GUI desktop standard, as it's geared more towards corporate, headless servers that don't need such a desktop.

If you want the standard GUI desktop installed on top of Ubuntu Server edition, run the following:

```
sudo apt-get install ubuntu-desktop
```

You could replace ubuntu-desktop with kubuntu-desktop if you prefer KDE to Gnome, or xubuntu-desktop if you want XFCE (lighter-weight, possibly better for your purposes)

---

### Post by adadk on 2009-03-22
Thanks Liam! Is there a site that would list all these sorts of things? I mean, I've found sites that list boot commands and the likes, but they all seem to be aimed at users with basic knowledge of Linux. I have zero.

---

