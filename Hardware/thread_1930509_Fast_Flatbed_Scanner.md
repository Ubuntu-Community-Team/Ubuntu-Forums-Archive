---
title: "Fast Flatbed Scanner"
date: 2012-02-23
forum: Hardware
---

### Post by russell hedger on 2012-02-23
I am trying to put together an Ubuntu-based print-to-speech system with a flatbed scanner, OCR and TTS. This is to help someone with a visual impairment read letters etc.

One of the difficulties I am experiencing is getting a fast enough scanner to make the system practical to use. I need to scan at 600 dpi grey scale to get the best results with OCR, but on my current scanner (an Epson V330 Photo) this takes about 45 seconds for an A4 scan. Can anyone recommend a faster scanner that is compatible with Ubuntu? It has to be flatbed to cope with the variety of print media that need to be read, and preferably not hugely expensive. The Canoscan 9000F is pretty fast but there are no Linux drivers yet.

---

### Post by wolfen69 on 2012-02-23
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

But you're going to have to do some research as to find out which ones are fast.

---

### Post by russell hedger on 2012-02-24
wolfen69, thanks for the link.

Unfortunately, manufacturers publish scan speeds in different ways, such as lines per second - and this figure seems to vary depending on black & white, grey scale, colour. Hence it can be difficult to compare scan speeds for what I want to do: 600dpi grey scale. Sometimes the data just isn't there, which is why I was hoping someone might have experience in this area.

I have just noticed that the driver for canoscan 9000F has made it in the SANE cvs, so hopefully will be in the next release. This is the fastest flatbed I have found so far: at 600dpi it scans at 1.5 ms/line, giving less than 12s for an A4 sheet. At 300 dpi, it does 1.2 ms/line, giving around 4 s for an A4 sheet. A great improvement on the Epson photo scanners.

---

