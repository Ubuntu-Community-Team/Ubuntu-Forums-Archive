---
title: "Epson printer: wireless connection missing filter, wired connection not recognized"
date: 2016-09-28
forum: Hardware
---

### Post by Transcix on 2016-09-28
Hello and thanks very much for any assistance.

I've had for a long time an Epson Stylus NX515 printer that's worked fine with Ubuntu, with me being automatically prompted to download the appropriate driver. Recently I upgraded to Ubuntu 16.04 and the printer continued working for a while, but then experienced I think one or two errors which I forget about but I corrected them, however now another, different error has arisen and I can't figure it out on my own.

The printer was connected wirelessly and all of a sudden print jobs would not go through, with an error message indicating a configuration problem due to a missing filter. Using the troubleshoot feature found that a certain cups filter could not be found. I tried downloading all cups filters from various sources, restarting cups and restarting the printer but this didn't work.

I decided it would be quicker to switch to a wired connection, so I deleted my printer from the printers program (in system settings) to start fresh, disabled the wireless networking on my printer's end (as the printer manual indicates), and proceeded to install the USB chord, but nothing happened when the chord was plugged in. I turned the printer's wireless networking back on but now the printer isn't recognized wirelessly or via USB; I can enter a device URI or search for a printer network host but I don't know what these things mean.

So basically I can't find any signals of my printer on my computer. At this point an hour of effort has left me worse off than where I was before and I'm not sure how to proceed further, so any help is greatly appreciated!

---

### Post by SeijiSensei on 2016-09-28
Try connecting the printer to your router with an Ethernet cable.  My Brother is wired to the network and visible from every machine in my home including Ubuntu PCs, Windows PCs, and smartphones.  Use a static IP address if you have that option.

---

### Post by Transcix on 2016-10-01
Thanks SeijiSensei, but that didn't work. I finally installed cups again and it worked, I can't really explain it, I just got lucky!

---

