---
title: "Distorted JPEG images on USB CF card reader w/large cards"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by jabezmcc1 on 2008-01-19
I am having trouble with a usb compact flash reader (Delkin eFilm Reader 2, part no. DDREADER-2).  

My system is Xunbuntu 7.10 (gutsy), kernel 2.6.22-14-generic, installed on a Dell Inspiron laptop with 196 Mb.

The problem is this:  the reader results in distorted images when used with a large 512 Mb CF card (Pny THNCF512MMG).  The distortion consists of wide horizontal bands of incorrect color in JPEG files.  The images have the same problem when viewed in either GQView or Gimp.  Gimp gives a “Premature end of JPEG file” message but displays the image anyway.  If the images are copied to the hard drive, the same problem exists.  The problem occurs independent of image resolution or file size, and all JPEG images on the CF card have the problem.  When converted to BMP (using another computer), the images appear to work, but GIF and PNG formats also have errors.  Interestingly, I see the exact same problem on another Xubuntu 7.10 system (Compaq Presario AMD K-6, 320Mb RAM)

The kicker is, the compact flash reader appears to work fine with smaller CF cards.  If I use another computer to copy the exact same images to a smaller, 32 Mb CF card, they have no problems being read by the Delkin eFilm Reader 2 on the Xubuntu system.  Needless to say, images on both CF cards work fine in other computers.   

This appears to be some sort of bug in the driver for the CF card reader, maybe the usb driver?  Problems with Xorg settings or other display issues are ruled out by the fact that everything works fine with the 32 Mb CF card.  If it is a bug, I would be happy to help try things to diagnose it.

---

### Post by jabezmcc1 on 2008-01-20
After posting over on the bug report page, it looks like this is a bug.

BUT the good new is I found a workaround.  The key is to FIRST plug the CF card into the card reader, THEN plug the reader into the usb port.  That appears to work! 

Thought I'd post this just in case anyone finds the same issue...

---

