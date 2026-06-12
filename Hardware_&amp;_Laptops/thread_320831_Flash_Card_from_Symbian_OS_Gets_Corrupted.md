---
title: "Flash Card from Symbian OS Gets Corrupted"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by Who on 2006-12-18
The flashcard from my Sony Ericsson M600i is very confusing for my Ubuntu (Edgy) system.

Basically, I can't write to it without corrupting the card - the volume automounts (as vfat) but after a little bit of writing everything related to the device stops (I.E the gnoime copying dialogue stops moving - the window still redraws though. Nautilus doesn't crash)! Often after trying to unmount the device and putting it back into the phone the data written is corrupt - the cool kind - where there are files and folders of negative size and with random filenames! (fixed by dropping the folder using fsck)

Does anyone know how can I solve this? It seems that if the format of the card means it can't be written to then it _really_ shouldn't be written to! 

The dmesg output from when I mount the device is in dmesg.txt

I am reluctant to break it again and take the logs of that because it can take a little while to clean, but if it is necessary then I will...

I don't think this is a hardware problem because my Dad's Windows PC seems fine with the card, as does the phone. I am using the card in the same flashcard reader on both PCs.

I remember having a VERY similar probelm with PSION cards a while back, Psions ran the forerunner to Symbian so that may be a clue for someone :)

If not then can I have some advice on posting a good bug report? I don't know what to include

Looking forward to any help

Who

---

### Post by Who on 2007-04-24
Looking at it again I think it is because Psion uses FAT12 but it is mounted as fat16. Does that sound feasible? How do I make ubuntu treat it right?

---

