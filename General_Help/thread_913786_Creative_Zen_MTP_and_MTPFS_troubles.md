---
title: "Creative Zen: MTP and MTPFS troubles"
date: 2008-09-08
forum: General Help
---

### Post by lucasl on 2008-09-08
Hi,
I just got a Creative Zen 8gb and I love it! It is much better then the nano.
Anyway, one of the reasons I chose it was because it was MTP and I had read that it is well supported on Linux.

Much to my dismay, everything I've tried has failed. Banshee gave me an error about file descriptors or something and now crashes when transferring songs and there's no way I'm using Amarok (a personal hate). I thought MTPFS would be my best bet, but its really unstable. I somehow managed to copy a single file, but whenever I copy a folder of music I get all different errors. Sometimes I can't get into a folder with the message: "Sorry, couldn't display all the contents of "Music": Transport endpoint is not connected." There were empty folders I tried to delete but I either got a message about an endpoint again or a file doesn't exist message.

I might even have to change my _entire home partition_ to ext3 from xfs so I can use it in Windows and use the software that came with the player.

Is there any solution to these problems? I shall be eternally grateful. (I wonder how many times I've said that on these forums?) Thanks!

EDIT: The banshee error is LIBMTP_Send_Track_From_File_Descriptor failed.

---

### Post by justleen on 2008-09-08
i use this: [http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)
works great.

---

### Post by skalka on 2008-11-06
> **justleen said:**
> i use this: [http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)
works great.

Gnomad2 doesn't preserve tags.

---

### Post by bryncoles on 2008-11-06
maybe try kzenexplorer? its in the repo's and i use it... it works on a drag and drop interface, which i only mention cause it took me ages to work out!

---

### Post by Gertrude on 2009-01-20
> **bryncoles said:**
> maybe try kzenexplorer? its in the repo's and i use it... it works on a drag and drop interface, which i only mention cause it took me ages to work out!

Kzenexplorer worked a treat.
I am currently copying everything from my old Nomad Jukebox to the hard drive.  I forgot how big it was, physically I mean!

G

---

### Post by eckeroo on 2009-01-22
My MP3 player is the Creative Zen V 4GB (Video)

I bought it at a time when I was still using windows and the MTP worked fine.

Now I use Ubuntu, I can transfer music using Rhythmbox with the MTP plugin, but only if I connect my MP3 player via a USB1.1 socket and not a USB2.0 socket. The download rate is slow so you couldn't quickly upload songs to the player in the five minutes you have before you've got to leave for work.

I wish I bought a Sansa clip instead. :(

---

### Post by joanmunoz on 2009-01-27
Hi!

I've similar problems. Ubuntu 8.10 Intrepid doesn't recognize my Creative Zen Micro, wich works perfectly well under XP. I tried lot of things (that cause a major breakdown of my system...I'd to restore from my last backup!) I've installed kzenExplorer, Banshee, Gnomad2, lots of libraries...but nothing works. None of them recognize the player. The best I achieved is defining a partition of the internal hd of the player and mount it in Ubuntu, but with no access to the music again...

Please help!!

---

### Post by BDNiner on 2009-01-27
All I had to do to get my creative zen working under ubuntu is install mtp-tools from synaptic. And it works perfectly.

---

