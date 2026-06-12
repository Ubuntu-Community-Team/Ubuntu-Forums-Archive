---
title: "MSI Wind U100 Webcam"
date: 2009-07-01
forum: Hardware
---

### Post by SebastianGonz on 2009-07-01
[B]I guess if somebody can help me with msi wind u100 im new in ubuntu, and i installed Ubuntu Netbook Remix.. So.. I got a problem with my internal cam.. it don't recognize it.. when i use cheese it says ''No camera found'' what should i do?
is a hardware problem? or i need a driver only?

Please help
Sorry for bad English..
[/B]

---

### Post by SemenSemenych on 2009-07-04
Try to press Fn+F6? 
in Terminal (Alt-F2 -- gnome-terminal) 
lsusb 
before Fn+F6, and after it.

---

### Post by pblanton on 2009-09-18
Thanks! I had the exact same problem. Googling turned up this and it was the answer!

--
Phillip

---

### Post by Ubunthree on 2009-11-19
I am setting up an MSI Wind U100 also, dual-booting Netbook Remix with Windows XP. The Fn/F6 thing works under Windows, but doesn't seem to do anything under Ubuntu. Neither Cheese nor lsusb detects the cam, either before or after. Am I missing something, or is there a way to use the built-in cam with Ubuntu?

Thanks!

---

### Post by Ubunthree on 2009-11-21
Bumping this to say that I have run into too many annoyances with Remix, and have discarded it for the time being in favor of standard Jaunty, which seems to be working perfectly, except that it also has not detected the built-in cam. Fn/F6 has no effect that I can see under Ubuntu. Any suggestions would be appreciated. The cam is the only thing that I have found to be not working (so far!).

---

### Post by Argentino on 2010-05-06
Does anyone know if the built in webcam works with Lucid? Skype in Lucid?

---

### Post by Hendrixski on 2010-07-17
:-) Initially it didn't seem to work in Lucid, but then I ran lsusb and it seems to work just fine. Cheers!

---

