---
title: "Need MythTV system advice"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by skattman83 on 2006-07-16
I want to build a MythTV box, and I have an old 800mhz celeron pc laying around.  If I used a Hauppauge 150 tuner card and an nvidia geforce fx5500(or 5200) card, would this system be able to handle being a pvr?

---

### Post by ORBiTrus on 2006-07-16
Yes.  The PVR-150 is supposed to work now, but if you're a stickler for stability use a PVR-250.

Like, really... 800MHz?  My old 300 can play DVD's, and my 450 can handle Xvid, and a PVR-150 is a hardware encoder, so it won't even use the CPU.  Now, if that were a BTTV card, I'd use a 1.2GHz system as the minimum.  But it's IVTV.  The real requirement in a PVR is the hard drive, but then we can now get vertical and boogie, so space is no longer a luxury few can afford.

P.S. Fedora makes a nice Mythbox.  Ubuntu's OK, but too much junk unless you do a server install.  Fedora has even more junk, but at least it's "able to be disabled".  *grin*  Breaking legs is fun... */grin*

P.P.S. For reference, my Mythbox is a P3-500 w/ 512MB ECC RAM (gotta love Dell motherboards), a 80GB and 200GB hdd, a PVR-250, and GeforceMX (the original) video card.  Sadly, I only get 3 stations, but I'm gonna see if someone out here (in the boonies) will let be set up a relay station to connect bounce an 802 signal to the nearest cable recipient.  Problem is getting to talk to them w/out some hick shoving a shotgun in your face...

---

### Post by skattman83 on 2006-07-17
What is the difference between a BTTV and a IVTV?

---

### Post by ORBiTrus on 2006-07-17
Kinda like a motorbike (IVTV) to a bicycle (BTTV).  Your CPU is the rider.

BTTV cards just receive the signal, and send it to the cpu, whereupon the CPU encodes it.  These are nice if you have a 3GHz or so computer which can encode about 2-2.5 MPEG-4 (DIVX) streams in real-time.

IVTV cards receive and encode to MPEG-2 (DVD) streams, which can avoid the CPU entirely if you have DMA turned on your harddrive. (If not, your CPU will interupt every time you need a disk write and will be responsible for caching the information in RAM and moving to Hard Drive as needed.  DMA means the CPU initializes it, then the card, RAM, and Hard Drive all chat to one another without help.)

So the limiting factor in how many BTTV cards can encode, or how many channels can be recorded/watched at once is the CPU.  Whereas the limiting factor if the IVTV cards is the bandwidth between PCI and Hard Drive (usually, what, about 66-100 MHz clock these days?  'Eh, I'm not a computer architect).  You might be able to have 4 shows recording/watching, while playing a high-intensity game with IVTV, or just 2 shows recording, and maybe use that SNES in the basement with BTTV.

Of course, if your question is actually about the physical difference rather than the difference to the user, I might as well ask you to explain  what the difference is between AMD and Intel, in terms of individual transistors.  Because, either way, they are all just black-box chips.

---

### Post by skattman83 on 2006-07-17
Thanks for the explanation, so the Hauppauge series cards are IVTV then, right?

---

### Post by skattman83 on 2006-07-22
I need a recommendation.  Will a 64 bit interface video card be able to play back dvds and mpeg2 without any lag?

---

### Post by herrdoktor330 on 2006-07-22
I too am interested in building a MythTV box. I've been reading over the Wiki and I don't really understand the full extent of it's potential. Maybe you guys could help me out on this one:

I have a ULI Socket 939 Mobo and a MayFlash Super JoyBox (for attaching PS2 contolers). I plan on slapping an Athlon X2 processor into (3800+ most likely) and I intend on buying 2 GB of RAM, 2x250GB SATA 3.0GB drives, and either 2x Hauppage 250 or 1x Hauppage 550 PVR cards. I'll be using a Chaintech 128mb NVIDIA 6200 PCI Express x16 Video with S-Video TV out and the integrated HD Audio of the motherboard. And of course, I'll be adding in a DVD burner for copying/ripping DVD movies.

What I would like the box the box to do is record 2 programs at once, be able to play emulated games with the frontends provided, and samba serve both the ROM collections I have and the digital media saved on the box over my lan to the other PCs in the house. I would like it to be able to serve all of these functions at one time. 

Based on what I want to build, would I be able to meet those goals? I understand that it probably won't be able to encode a DVD to Xvid or anything like that while DVRing... and most likely I'll be doing exclusive Mpeg2 encoding for the sake of processor overhead. But will it be able to DVR while serving files and playing emulated games and doing basic file serving? Will my planned hardware purchase be enough to meet all these goals? Will SATA 3GB give me enough hard drive bandwidth? What about getting super joybox controllers to work on a MythTV box? Is that an option? Also, do you get higher video quality from having 2 Hauppage 250 cards rather than a single dual tuner?

Any input would be helpful.

---

