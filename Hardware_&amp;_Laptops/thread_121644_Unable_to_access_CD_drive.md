---
title: "Unable to access CD drive"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by zanzibar_jones on 2006-01-25
Hello there,

I've been attempting to run breezy on an Acer Travelmate for a month now but would still count myself as almost completely clueless. Today I was working on getting audio cds to play and in so doing have managed to create a far worse problem for myself. After browsing on the forums I thought I'd found a potential solution to the audio cd issue and put the following command into terminal and then restarted:

sudo usermod -G audio username

and then the cd icon vanished. When I tried to open the cd file through 'computer' I get the error message "could not execute pmount". Frankly I haven't the faintest idea what I've done but if someone could help me put it right I'd be incredibly grateful. I can live without playing music on the laptop but being able to read and write to the cd drive is kind of essential.

Thanks in advance,
Alex

---

### Post by hillbilly on 2006-01-25
try running > $/> sudo mount -t auto /dev/cdrom /mnt/cdrom
NOTE: if you dont have /mnt/cdrom directory, create it.  
now if you navigate to /mnt/cdrom you should be able to access your cdrom. 

But I do not know what caused the removal of your cdrom icon e.t.c

EDIT: i had used option -p earlier, which is wrong !

---

