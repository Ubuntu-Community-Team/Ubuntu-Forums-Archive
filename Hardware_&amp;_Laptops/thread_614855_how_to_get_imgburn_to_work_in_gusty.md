---
title: "how to get imgburn to work in gusty ?"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by kraymore on 2007-11-16
how do you get imgburn to work in gutsy ?  i read one post that said that it required wine 0.9.33 to work but not the latest version.  i really need to get this application running to burn .dvd files.  

thank you

---

### Post by taurus on 2007-11-16
You mean you need to burn .img to a DVD?  Well, k3b can handle that just fine.

---

### Post by kraymore on 2007-11-16
no i'm afraid that i've stumbled upon a .dvd file that references a .iso file with a "break" in the writing of the image and i've been told that imgburn will burn the .dvd file without having to go with a commercial program (that might not work with ubuntu at all).  i had to tear down a ubuntu box here at home just to install windows, and steal my fathers writer to write an image, but i'd sure love to return his writer and setup the linux box again.  

so -- yes i need to burn a .dvd file which references a .iso file.  the .dvd file only says this:

LayerBreak=1913760
image.iso

so it points to an iso with a layer break.  i've read posts about growisofs working but i could never get it to successfully burn so i turned to try imgburn on ubuntu.  

thank you

desperately need to burn this iso properly

---

### Post by jespdj on 2007-11-17
It sounds like this ISO image is meant for a dual-layer DVD. The layer break indicates where the DVD goes from the first to the second layer.

Are you using a dual-layer DVD disc? Do you have a DVD writer that can write dual-layer DVDs?

---

### Post by kraymore on 2007-11-17
yes i have a dual layer disc and its a dual layer burner.  is growisofs the only thing that will burn isos with layer break ?  

i dont know what my error means.

---

