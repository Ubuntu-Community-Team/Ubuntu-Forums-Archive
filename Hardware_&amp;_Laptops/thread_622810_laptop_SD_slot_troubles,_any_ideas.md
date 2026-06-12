---
title: "laptop SD slot troubles, any ideas?"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Scarath on 2007-11-25
Hi

I have a problem with a Samsung r40, this laptop has got an SD slot on the front of it. 

As im sure you have guessed it does not work/register when you put an SD card into it.

Has anyone else had this problem with SD memory slots in laptops?

Is there a solution? (I have googled the problem but couldnt find anything) 

I know some flash-digital music players need a bit of code written to the root file to make linux see them/use them, could this help? (e.g. is there a bit of code you could stick on the SD card that would make linux see it/run it)

Or could it be that gutsy just doesnt support the on-board SD (this may be, when the card is plugged in there is no new device in the media folder).

Thanks in advance

---

### Post by blurryone on 2007-11-26
G'day Scarath,

I too have been having this problem but have a Ricoh multi card reader and am trying to get it to read an xD card.

When i insert the card it does not mount

Have also checked google - but nothing out there i could see...

Hopefully somebody has a fix for this and it will work for both of us..

Good luck

Blurry

---

### Post by Lutin on 2007-11-26
Hello

Just wondering whether either of you guys has a Texas Instruments controller for your SD cards? These seem to be fairly common - I have one on my Acer Aspire 7003. I had to do a fix in /etc/modules under Fiesty (at work so don't have my laptop with me and cannot check what the mods were), but this was not necessary with my recent upgrade to Gutsy.

If you search on the TI controller you might find something.

Hope this is some use - I can check when I get home if it would help.

regards

---

### Post by blurryone on 2007-11-26
Lutin,

Have been doing some more searching and found out that apparently gutsy does solve my problem but only for SD cards - from what i have read xD cards are still not working. which is kinda stink. I can see the device and everything.....

FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

unfortunately it still does not mount when i use an xD card.. i will test tomorrow with an SD card and let you know

Sure if you could try an xD card (if you have one) and let me know but so far as i can tell there is a issue surrounding the use of xD not SD (SD was fixed with gutsy)

Cheers mate & Peace

Blurry

---

### Post by nowhere.elysium on 2007-11-26
There was the same problem with the inspiron 6000 when it came out: a kernel hack solved it, until it was introduced in the mainstream. I think you also had to make a mountpoint for mmcblk0.
Basically, it's because Ricoh are tight-fisted with their schematics.
Try searching around for pages on how to get the inspiron 6000 working - there's some good information in them, and they may well sort your problem out.

---

### Post by blurryone on 2007-11-28
thanks nowhere... to bad for me i'm still a complete noob with linux so i will just have to wait till i have learned a bit more..

---

### Post by Scarath on 2007-12-07
Weird think happened, I tried some other SD cards in the lappy and they mounted ?!?!

The one that didnt mount was a 32mb Pretec SD card

The ones that worked were - 2 GB kingston SD card
                                              - 2 GB kingston Micro SD card (plugged in using a micro SD adapter)

Maybe Kingston works while other (cheapo brands) do not. I got the 32mb along with my digital camera and so I expect it will be bottom of the barrel quality. 

Maybe its a size thing. Who knows.

---

### Post by victorgreen on 2007-12-07
The SD reader in Thinkpads, at least T61/X61's works out of box in gutsy

---

