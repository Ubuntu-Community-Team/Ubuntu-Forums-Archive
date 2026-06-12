---
title: "Annoying sound when moving mouse"
date: 2009-04-23
forum: Hardware
---

### Post by riwa on 2009-04-23
When i move my mouse a squealing sound comes out of the headphones. Its constant. When I move the mouse its always there. When I dont, its silenced. Very annoying.

Any ideas?

---

### Post by ddrichardson on 2009-04-23
USB, PS2 or wireless mouse?

---

### Post by wandering_not_lost on 2009-06-08
I get the same thing, mouse move = odd noise, thought it was just me. 
USB mouse btw.

---

### Post by ddrichardson on 2009-06-09
Is the USB controller on the main board or in a slot? Same for the soundcard. USB transmits power to the mouse and interference is easily picked up in unshielded soundcards.

---

### Post by Brausen on 2009-06-15
> **ddrichardson said:**
> Is the USB controller on the main board or in a slot? Same for the soundcard. USB transmits power to the mouse and interference is easily picked up in unshielded soundcards.
The only way out is to shift the USB mouse?
Is there another solution?

---

### Post by ddrichardson on 2009-06-15
Shield the sound card.  A surprisingly common issue is simply not screwing the card into the chassis (where the back plate touches the case).

---

### Post by Arcturus691 on 2009-08-12
I think this might be a bug.  This problem started right after the last updates.  I also just noticed that on my system if you press and hold the arrow key on the keyboard you get the same noise. The sound happens even if the sound is muted via software.  Any one know how to check which updates were applied on the last update?(Nevermind: synaptic->file->history)

I have attached updates done on my system before sound issue.

I noticed some header updates maybe these are the culprit?

---

### Post by Arcturus691 on 2009-08-21
Just for the record,
Annoying sound disappeared for me with latest updates, specifically:

linux-image-generic (2.6.28.14.19) to 2.6.28.15.20

Volume control for keyboard is still busted probably separate issue.
See Thread: [1249336]("http://ubuntuforums.org/showthread.php?t=1249336") for volume control fix

---

