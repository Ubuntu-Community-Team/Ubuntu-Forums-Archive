---
title: "My 1st hw problem [AUDIO]"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by bufa on 2005-02-20
Well... everything is going well, but I can't hear anything from my pc... :(

I have a Sound Blaster Live Mp3+ and it seems to be "detected", but it doesn't work... any idea?... :-?

---

### Post by bufa on 2005-02-20
[QUOTE=bufa]Well... everything is going well, but I can't hear anything from my pc... :(

I have a Sound Blaster Live Mp3+ and it seems to be "detected", but it doesn't work... any idea?... :-?[/QUOTE]
 no ideas? :(:( snif

---

### Post by nikopol on 2005-02-21
I'll need more details to help you here but in the meanwhile try this...

A) is there another soundcard integrated to your motherboard that is being detected instead? You may want to disable that soundcard to avoid it being detected
B) on the sound icon, (top right of the screen), right click and open it. Go to File> Change Device and check that your device is the one selected. Then check that the volume levels are set correctly.
C) Another thing you could try is in the console type ```
sudo alsamixer
``` - then see if the levels are not Muted.

---

### Post by bufa on 2005-02-21
[QUOTE=nikopol]I'll need more details to help you here but in the meanwhile try this...

A) is there another soundcard integrated to your motherboard that is being detected instead? You may want to disable that soundcard to avoid it being detected
B) on the sound icon, (top right of the screen), right click and open it. Go to File> Change Device and check that your device is the one selected. Then check that the volume levels are set correctly.
C) Another thing you could try is in the console type ```
sudo alsamixer
``` - then see if the levels are not Muted.[/QUOTE]
 the problem is the next:
I've got 2 sound boards 1 "on board" and the other (sblive) in the PCI slot.

OK, Linux Takes the "onboard" as a default... so if I plug the speakers on the onboard, it works... wrongly, but it does...

I want to select the PCI as a default!!!!!!! please!

---

### Post by nikopol on 2005-02-22
[QUOTE=bufa]the problem is the next:
I've got 2 sound boards 1 "on board" and the other (sblive) in the PCI slot.

OK, Linux Takes the "onboard" as a default... so if I plug the speakers on the onboard, it works... wrongly, but it does...

I want to select the PCI as a default!!!!!!! please![/QUOTE]
 You will have to check your BIOS to see if you can disable the soundcard which would mean that Linux wouldn't detect it at all (I think)...

---

