---
title: "Logitech wireless / multimedia keys"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by disector88 on 2006-08-07
Hi,

I am having trouble with my multimedia keys on my Logitech EX110 wireless keyboard. The problem is that the "next" and "play" button are recognized as the same key (in the "Keyboard Shortcuts" console). i.e. If I assign "play" to perform an action, I can't assign another action to the "next" button since ubuntu says that that key is already assigned. 

I installed another package, but it brought its own (ugly) interface of green text and green bars. Is there a way to have dapper / gnome to natively recognize the keys without having to install something (I think I tried hotkeys) on top?

---

### Post by disector88 on 2006-08-10
Is there something wrong with the way the keyboard is configured ? 
Does anyone know how to bind all the keys?

---

### Post by disector88 on 2006-08-23
Hi,

I figured out that my symkeys set up was a little messed up. This was corrected by reading several guides/howtos. Also, I figured out that metacity handles the keyboard shortcuts by default and was messing up the volume keys. However, metacity is not really configurable, and it was changing the volume on the wrong channel in alsamixer. Alternatives were in order.

I first tried hotkeys, that worked for the play/stop/next/prev keys, but not volume & mute.
Then installed keytouch, which is really great and supports multimedia keys on several keyboard models. It did not work with the volume keys out of the box, but is easy to reconfigure. I used custom commands to make it talk to amixer. 

The 'mute' key however doesn't work. I have the dreaded ca0106 chip on my Creative Sound Blaster Audigy SE card. The channel I output on is 'Analog Front'. This is what I get when trying to issue the 'mute' command:

$ amixer -sset 'Analog Front' toggle
amixer: Unknown playback setup 'toggle'

Any ideas?

---

