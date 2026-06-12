---
title: "[SOLVED] Help with audio"
date: 2008-10-15
forum: General Help
---

### Post by EvanRogers on 2008-10-15
OK, so yesterday i thought i would compile a new kernel because i heard that it could speed up your system. I folowed this guide: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Now i can't change the voume control, there is a red x over the volume control and when i click on it i get this error:

No volume control GStreamer plugins and/or devices found.

And when i try to listen to music on rythmbox it just skips the song and puts a red - sign next to the song.

I have installed all the gstreamer apps i am pretty sure. Any help would be great. 

(noob here:lolflag:)

---

### Post by forger on 2008-10-15
follow this golden rule: if it works, don't try to break it :) you probably need to compile restricted drivers for the kernel you've built.. but..

why don't you use your old working kernel?

---

### Post by EvanRogers on 2008-10-15
How do you do that?

---

### Post by Yellow Pasque on 2008-10-15
From that thread..
> Q. My High Definition sound (Azalia) does not work with the new kernel!:

A. This took me a long time to figure out because I didn't have sound either. You have to enable the Intel HD module in Advanced Linux Sound Architecture, even if it isn't Intel.
I guess he/she's referring to compiling the ALSA module directly into the kernel. You can also use this script to build ALSA modules: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

And, of course, you can try OSS4 if that doesn't work out.

---

### Post by forger on 2008-10-15
> **EvanRogers said:**
> How do you do that?
Uh ok, follow this golden rule too: Don't try something you don't know how to undo :)
No offense, just suggesting things that you should keep in mind before tampering with the system

Reboot and keep pressing the "esc" key every second or so until grub (boot menu loader) shows a selection of kernels.
You use the one you were using before.. for hardy, that should be: 
2.6.24.19.x up to 2.6.24.21.x

Select it with the up/down arrow keypads, and press enter.
Make sure you remove the custom kernel using Synaptic package manager

---

### Post by EvanRogers on 2008-10-15
ha sorry, but that golden rule is impossible for me. i like to experiment, well i got it working just switched kernels then deleted the other ones. thanks guys

---

### Post by forger on 2008-10-15
> **EvanRogers said:**
> ha sorry, but that golden rule is impossible for me. i like to experiment, well i got it working just switched kernels then deleted the other ones. thanks guys

Welcome to hardcore linux then :guitar:
Just make sure you backup your critical data before doing any sudo rm -rf commands :P

---

