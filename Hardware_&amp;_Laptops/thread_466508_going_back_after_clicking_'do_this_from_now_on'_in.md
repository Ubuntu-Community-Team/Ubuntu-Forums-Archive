---
title: "going back after clicking 'do this from now on' in Kubuntu"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by donnellymp on 2007-06-06
Hi. I use Kubuntu, and I have a Sansa m240 mp3 player that, when I first plug it in, Kubuntu recognizes first as a camera and then as a regular USB drive. Today I stupidly got the camera dialog box and checked that spot where you say 'do this from now on.' Now, whenever I plug in the Sansa m240, it gets recognized as a camera, and I can't access any of the files I had saved on it. How can I reverse the 'do this from now on' action and get Kubuntu to recognize it as a USB drive?

---

### Post by pbw on 2007-06-07
You can change that in kcontrol.. Also, you should be able to still access your files anyways. Just open it/go to the path in konqueror.

ie. enter /media/whatever in konq.

---

### Post by donnellymp on 2007-06-07
Thanks for your reply. I tried /media/Sansa m240 in Konqueror, and the files do display, but they're locked, and when I click on them, I get an error saying that 'the resource does not exist anymore.' Also tried it as root, to no avail. Seems like the Sansa m240 is being mounted as a camera and not a USB device, so there's no mount point. How specifically would I chane this in KControl: I saw where I can change file associations, but nothing specific to my problem. But I may be missing something.

---

### Post by pbw on 2007-06-07
I was assuming it'd be under peripherals -> camera or whatever (i don't have one, so i'm not sure on this and could be wrong).

Anyways, take a peek at ~/.kde/share/config/medianotifierrc That should be the file you need to alter, or even just delete.

Lemme know if that helps.

-- pbw

---

