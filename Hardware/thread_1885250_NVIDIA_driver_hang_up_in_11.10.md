---
title: "NVIDIA driver hang up in 11.10"
date: 2011-11-22
forum: Hardware
---

### Post by rfbeck on 2011-11-22
When I try to install the latest NVIDIA driver in Ocelot, I get the following error:

mkdir: cannot create directory '/tmp/selfgz493': read-only file system

I have never gotten such an error before, and I have done this a lot. Any help would help.
______
Robert

---

### Post by rfbeck on 2011-11-24
Any help out there folks? Even a nibble?
______
Robert

---

### Post by Crempel on 2011-11-24
> **rfbeck said:**
> Any help out there folks? Even a nibble?
______
Robert

Very interesting - I also installed the "current" NVIDIA driver (after installing Oneiric 173 was loaded) and Gnome-shell, which I use, just froze. I did not get any error messages, it just did not react anymore. I repeated this a few times, also under Unity, but the result was always the same. I got a 7200GS, maybe Oneiric does not like it? With the older 173 driver everything works well.

---

### Post by rfbeck on 2012-01-22
Hi out there. I'm still looking for an answer to my question, posted at the top. I remember fixing it one time by changing runlevels. Is there another way?

______
Robert

---

### Post by pbrane on 2012-01-22
Have you tried using this PPA? It works for me just fine on 11.10.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by rfbeck on 2012-01-23
Thanks for that pbrane. I have done it and I think it will make my future NVIDIA drivers less of pain. In the meantime, I have finally solved thus far my installation issue. I installed the drivers using one less command. I used "sh" instead of sh ./etc. The NVIDIA driver installed like a charm. Don't know why it made the difference.
Thanks for the help. 
______
Robert

---

