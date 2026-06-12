---
title: "Hardware for Ubuntu LTS based HTPC"
date: 2015-08-24
forum: Hardware
---

### Post by jason_gibson2 on 2015-08-24
I currently have an AMD 5350 Kabini APU with 8gb of ram, 120gb ssd for os / minecraft server, and 1tb spinner for main storage. Currently it is running Ubuntu Server 14.04 direct booting to Kodi. I have recently started having a fair bit of laggy response from Kodi, after researching I find that they don't support the fglrx driver. The radeon driver doesn't work for me at all, stutters endlessly. So my only option is to change hardware. This htpc also functions as my Minecraft server (5 people max), apt-cache proxy, transmission torrent box, file server & backups. Once I move into my new place in October I will be mirroring the server for further backups. As far as HTPC purposes I am limiting myself to dvd and bluray ripped movies as well as mp3 music that I have collected over the years. So it has no disc drive, just movies and music straight from the hard drive.

What hardware would accomplish this for me. I would like to keep it as simple as possible, the case I currently have is very small so no real room for a discrete gpu. I was looking at Intel i3 cpu with the hd4600 graphics. Would that be enough for my purposes? Or will I need to get a discrete gpu, bigger case and so forth? The reason I went with the Amd APU was to keep the power draw low with its 25w tdp. So the lower power draw the better as well. Motherboard suggestions would be appreciated as well, the case is mITX.

*EDIT* I am considering making this server / htpc hold a Mythtv backend and use Kodi as a pvr so that is also something to factor in.

---

### Post by Yellow Pasque on 2015-08-24
> The radeon driver doesn't work for me at all, stutters endlessly
Doing what? Video playback? Have you installed mesa-vdpau-drivers package for video decode acceleration?

---

### Post by jason_gibson2 on 2015-08-24
I'm an idiot. I kept trying to install the radeon driver, didn't realize the open source one was the ati driver. Server / htpc works great now... I fail.

---

