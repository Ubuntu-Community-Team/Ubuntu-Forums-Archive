---
title: "Acer Extensa 76204021"
date: 2008-08-15
forum: Hardware
---

### Post by mazz72 on 2008-08-15
Hi all. I've checked around some threads and even checked out that Linux laptop testing site, but I can't find any info on this laptop. I want to put Hardy on it. Here are the specs...

Extensa 76204021

1.86GHz Intel Pentium dual-core T2390
17" diagonal WXGA+ TFT LCD
3GB DDR memory
160GB SATA hard drive
*** Acer InviLink 802.11b/g WiFi-certified wireless LAN ***
Intel Graphics Media Accelerator X3100

My main concerns are with the video and wireless, as they seem to be common problems people have with putting Ubuntu on a laptop. The video should be ok, I would think, being Intel; but I'm not familiar at all with Acer's InviLink. Anyone have any experience with this using Ubuntu, or think it could be a problem??

Thanks a lot. :)

---

### Post by mazz72 on 2008-08-15
hmmmm....looks like I may be on my own with this one. :(

Well, maybe I'll go ahead and give it a shot and post the outcome for anyone else who may be interested. :)

---

### Post by vocalstud69 on 2008-08-18
I just bought mine today, and I'm having a problem even detecting the wireless card with lspci, unless I'm missing something.  I'm thinking it didn't install right, and I can't even figure out who makes the Acer Invilink chipset.  I think it's Atheros, but I'm not sure, honestly.  Everything else works great, if only I could get that to work.

Edit:  The drivers were not loaded correctly, so I reformatted and it worked after updating and enabling the 'wl' option from the Restricted Drivers menu.  Note:  It is most likely a Broadcom Chip.  It'll say it on the bottom.  If it is a Broadcom chip, you'll need to install the b43-fwcutter package in Synpatic, and it'll do everything else for you.  lspci output shows--on my computer--that the Broadcom is a USB controller, and I'm wondering if that is why it didn't get installed right, because I had my flash drive hooked up to the computer.  I don't know if that's the case, but just to make sure I took out the flash drive when I reformatted.  

Everything else works great.  After enabling the ATI Radeon driver in the Restricted Hardware menu, Compiz-Fusion worked fine after restart.  It's so fast now it's obscene, and I love it, since I went from a 2ghz single core, 512MB 8lb laptop to a 5 lb dual core, 2gig laptop.  It's like going from rubbing alcohol to 300 year old, perfect wine.

Oh, and I didn't have any trouble with the headphone jack.  I haven't tested the tv out yet, since I don't have a s-video cord, nor the svga port to see if they work, but since the driver is from the manufacturer, I imagine that they would work.

---

