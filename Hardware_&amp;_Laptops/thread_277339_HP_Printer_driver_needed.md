---
title: "HP Printer driver needed"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by indigoshift on 2006-10-14
Hello, all --

I finally got my wife switched over to Ubuntu, and she loves it.

However, she just bought an HP Photosmart C5100 Series printer...it's one of those multi-purpose things (scans, prints, copies, does photos, et cetera), and I'm having difficulty locating a decent driver.  While I've done all sorts of things with Ubuntu, this will be my first printer installation, and I'm a little lost here.

Not looking for anything fancy, just the ability to print documents in black and white (and possibly color).  The other things the 5100 can do (scanning, for instance) aren't really needed right now.  She just wants to print documents from her Ubuntu machine.

I realize this isn't a very common printer, which is probably why I'm having trouble finding the drivers.  Any help is appreciated.  Thanks!

---

### Post by meng on 2006-10-14
According to linuxprinting.org, this works "perfectly" with the hpijs driver, which you don't even need to download as it should already be available on the standard installation. Just go to Printer management and choose HP printer, if your particular Photosmart is not there look for PSC5000, or else PSC2500 (I can verify that this is among the multitude of printers that uses the hpijs driver).

---

### Post by indigoshift on 2006-10-14
It was indeed the PSC2500 driver.  Thanks!

It was so easy, my wife did it herself, which was very cool.  I'm usually tech support for the entire house, even for the smallest things.  But she was eager to do it herself, and it worked great.

Here's the step-by-step, just in case someone comes along later with the same question:

1.  Plug the printer into the computer.
2.  From the System menu, go to Administration, then Printing.
3.  Double-click "New Printer".
4.  It will already detect the printer (as "HP Photosmart C5100 Series"), so click "Forward".
5.  Select "PSC 2500" from the list on the next screen (it's waaay towards the bottom).  Click "Forward" again.
6.  Name the printer (if you wish) in the next screen.  Click "Apply".

And that's it.  Prints in b/w and color with no problems.

Thanks again for the help!

---

### Post by meng on 2006-10-14
Savor the taste of victory - now you just need to get your scanning working!

---

### Post by indigoshift on 2006-10-14
Indeed.  That's coming next, though.  It's the weekend, and I have hours of relaxing to do.  :-D

---

