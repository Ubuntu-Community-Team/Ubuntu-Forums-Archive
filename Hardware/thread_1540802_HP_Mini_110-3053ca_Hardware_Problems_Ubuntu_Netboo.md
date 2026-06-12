---
title: "HP Mini 110-3053ca Hardware Problems Ubuntu Netbook Edition"
date: 2010-07-28
forum: Hardware
---

### Post by jamesdjadams on 2010-07-28
Hello,

After installing Ubuntu 10.04 netbook edition on my HP Mini 110-3053ca netbook, I have no wifi and no sound. I have found a few posts on how to get these to work but none worked for me! I'm new to Ubuntu and like it so far but need these components operating. 

Is there going to be a fix? If so, when? Is there an easy way to get these things working on my netbook?

Thanks!

---

### Post by mikewhatever on 2010-07-28
The wifi issue is likely the lack of a driver. Hookup an ethernet cable, then open System->Admin->Hardware Drivers.
As for the sound, open Sound Preferences and make sure it's not muted.

---

### Post by jamesdjadams on 2010-07-28
Okay, I was able to get the wifi up and running but still no sound... :(

---

### Post by mikewhatever on 2010-07-28
Here is what google found:
> Actually I solved it, but thanks for your reply! For those who care this is what I did:
I added:
options snd-hda-intel model=ref

To:
/etc/modprobe.d/alsa-base.conf
[http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/](http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/)

In a Terminal window, run **gksudo gedit /etc/modprobe.d/alsa-base.conf**,
add **options snd-hda-intel model=ref** to the end of the file,
save and exit.
Sound should hopefully work after a reboot.

---

