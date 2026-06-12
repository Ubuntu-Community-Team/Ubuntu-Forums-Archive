---
title: "Ubuntu on a 300mhz 64mb computer"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by Breepee on 2005-12-09
I got this old box (Celeron 300mhz and 64MB PC66 memory and 220GB of diskspace with lot's of music on it in FLAC for the most part) which is to be a dedicated Rhythmbox playback machine. I only need to be able to access it's drives via samba and be able use Rhythmbox. That means I'll need gtk2, right?

Is there a version of Ubuntu that better suited for this? 4.10, 5.04 or just 5.10? I was thinking to install it as a server, and then try to get XFCE with Rhythmbox on. Little lighter than Gnome (I think?) but still suited for the job.

And ideas or comments?

---

### Post by John.Michael.Kane on 2005-12-09
Server install would seem the best way to go.you may not even have to install anything but the files needed to give your cilent machine access to the server, and files.

---

### Post by az on 2005-12-09
[QUOTE=Breepee] I only need to be able to access it's drives via samba and be able use Rhythmbox. That means I'll need gtk2, right?[/QUOTE]

What do you mean?  Do you want to run rhythmbox on another box and just access the drive?  No, you do not need gtk or even x.  You need to do a server install (as descrivbed) and install samba

sudo apt-get install samba

You need to edit the samba configuration by hand so that you can reach your computer via the network.

---

### Post by Breepee on 2005-12-09
I want to access the files though samba, primairily to update them. Then use the machine itself to playback the music back with Rhythmbox.

---

