---
title: "TI internal card reader issue"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by mshale on 2007-04-08
Hey guys and gals.  

I just got a micro SD card for my cell phone.  It came with an adapter that converts it to a regular SD size.  I read some HOWTOs and got it working.  Now that I have rebooted my laptop, it all went away (no auto mount when i insert the card, can't even do the howtos again)  I followed the howtos to the T, even added the code to the modules like it told me to make it where i didn't have to mount it every time i rebooted.  Now i get nothing, and when in insert the card, the indicator light that shows me that the card is being read is blinking in this fashion:  .- .- .- if you can read Morse Code.  Any suggestions??

---

### Post by rwb on 2007-04-09
Hi I have a similar issue but using Fiesty 7.04 Beta

the Ti internal reader on my HP nc6120 was fine and auto mounted with the 2.6.20-12 kernel but now with the updated 2.6.20-14 kernel i get this.........

Apr  9 15:54:58 rwb-laptop kernel: [  190.920000] tifm_7xx1: sd card detected in socket 3
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000] mmcblk0: mmc3:aaaa SD01G 992000KiB 
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000]  mmcblk0: p1
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 4 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.112000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 13 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.116000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 9 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983609
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983610
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983611
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983612
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983613
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983614
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983615
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983616

Like wise I think that the two problems are related
anybody got any Ideas apart from reverting bak to 2.6.20-12?:confused:

---

### Post by mshale on 2007-04-09
> **rwb said:**
> 
the Ti internal reader on my HP nc6120 was fine and auto mounted with the 2.6.20-12 kernel but now with the updated 2.6.20-14 kernel i get this.........

```
Apr  9 15:54:58 rwb-laptop kernel: [  190.920000] tifm_7xx1: sd card detected in socket 3
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000] mmcblk0: mmc3:aaaa SD01G 992000KiB 
Apr  9 15:54:58 rwb-laptop kernel: [  191.104000]  mmcblk0: p1
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983936
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 1983984
Apr  9 15:54:59 rwb-laptop kernel: [  192.108000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 4 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.112000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 13 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.116000] end_request: I/O error, dev mmcblk0, sector 0
Apr  9 15:54:59 rwb-laptop last message repeated 9 times
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983609
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983610
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983611
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983612
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983613
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983614
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983615
Apr  9 15:54:59 rwb-laptop kernel: [  192.124000] end_request: I/O error, dev mmcblk0, sector 1983616

```

Like wise I think that the two problems are related
anybody got any Ideas apart from reverting bak to 2.6.20-12?:confused:

I'm using Feisty 7.04 as well, btw.

Now that I think back, it did start doing this after i did an update, which probably DL a new kernel for me too... How did you run that diagnostic?  I would like to check and see if I get the same errors.  I personally wouldn't mind reverting back to the older kernelk, I didn't have any problems with it.  I looked in the kernels folder, and i have 4 folders. two that have the kernel number 2.6.20-12  and two with the newer number.  to revert back to the older one, would i just remove the newer folders?

---

### Post by macogw on 2007-04-23
[http://geocities.com/dollzrgr8/tifm_install.tar.gz](http://geocities.com/dollzrgr8/tifm_install.tar.gz)
Download
untar
cd to directory
sudo chmod +x install.sh
./install.sh

That should make it work on Feisty

---

### Post by clueless dave on 2007-05-06
I am using a TI card reader in a System76 laptop with SD cards used in a Palm T/X and a Canon digital camera. I had no problem under Edgy with cards that I had cleaned and reformatted in the Palm. However, after the upgrade to Feisty things stopped working. Syslogs showed that the system recognized that a card had been inserted, but wouldn't automount it.

It turned out that brand new "unformatted" cards automounted. After digging around to see how I could reformat the card in Linux and having no luck with the commands to do so, I decided to try reformatting the cards in my digital camera. Bingo! The cards automount, no problem transferring audio files, and I'm good to go.

I know this isn't a purist solution, but is a no-hassle workaround that might be useful to someone with an otherwise recognized device and access to a digital camera. I can only conclude that Feisty is fussier with regard to the file formats on the SD card.

Sorry for the cross-post, but thought it might be useful if someone didn't happen to look in the USB/mmc thread.

---

