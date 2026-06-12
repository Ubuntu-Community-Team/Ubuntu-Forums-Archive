---
title: "Using a server as a desktop?"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by CARGANZAR on 2009-09-27
Hi

I'm wanting to use a server as a desktop machine and am getting the impression that the server I am intending to use is too powerfull, but the ubuntu server addition has no GUI and I'm just attempting to switch over from MS can anyone advise?
The system I am intending to use is a HP DL585 Specs listed below.
 [http://www.pcauthority.com.au/Review/84798,hp-proliant-dl585-g2.aspx](http://www.pcauthority.com.au/Review/84798,hp-proliant-dl585-g2.aspx)

2x AMD Opteron 2.2GHz 64 Bit  1MB cache CPU`s fitted,

16GB Memory,

HP Smart Array 5i Raid Controller with 64MB Cache,

3x HP 72.8GB Ultra SCSI 320 Hot Plug HDD`s

Integrated Lights Out Controller,

2x Hot Plug Redundant Psu`s,

2x HP NC 7782 1000tx network Ports,

2x USB Ports,

CD Rom Drive,

Floppy Drive,

Plus all standard Ports


Cheers

---

### Post by steev182 on 2009-09-27
You can put any OS on a server.

If you use ubuntu server, you just need to do 'sudo apt-get install ubuntu-desktop' and you'll have a server working as a desktop.

The DLs are rackmount, so that may be an issue, and you get a huge gust of fans spinning up for the first 1-2 minutes, but the fans slow down. It will be a lot louder than most desktops, but I have a Dell PowerEdge SC440 running as a home server/desktop and I had to get a graphics card for it and a soundcard (I had a Griffin iMic USB, so that was ok). It's not too loud now, but that's probably from being acclimatized to it.

It's not too powerful, just too large and unwieldy for a home environment in rackmount form.

---

### Post by CARGANZAR on 2009-09-27
> **steev182 said:**
> You can put any OS on a server.

If you use ubuntu server, you just need to do 'sudo apt-get install ubuntu-desktop' and you'll have a server working as a desktop.

The DLs are rackmount, so that may be an issue, and you get a huge gust of fans spinning up for the first 1-2 minutes, but the fans slow down. It will be a lot louder than most desktops, but I have a Dell PowerEdge SC440 running as a home server/desktop and I had to get a graphics card for it and a soundcard (I had a Griffin iMic USB, so that was ok). It's not too loud now, but that's probably from being acclimatized to it.

It's not too powerful, just too large and unwieldy for a home environment in rackmount form.

So do I need to install the server version then install desktop version on top? Sorry total newb to linux. :)

---

### Post by steev182 on 2009-09-27
You can get away with just putting the desktop version on, then you won't be greeted straight away with a command line when you first install it.

It'll be a nicer way of easing yourself into Linux!

---

### Post by CARGANZAR on 2009-09-27
Thanks for the help :guitar:

---

### Post by stlsaint on 2009-09-27
with 16gb ram and a server processor you need to go with 64bit!

---

