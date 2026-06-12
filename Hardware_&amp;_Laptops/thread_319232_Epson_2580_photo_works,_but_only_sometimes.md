---
title: "Epson 2580 photo works, but only sometimes"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by HanZo on 2006-12-15
This is very strange. since breezy, my Epson Perfection 2580 photo scanner works out of the box with xsane. But it does so only when it feels like. It always works after a fresh install, for the rest, when I lauch Xsane sometimes it works, sometimes it will just say that no compatible scanner can be found. very strange.

has anybody an idea about what the possible cause could be? I don't know what I could try to do... so any hint would be highly appreciated!

---

### Post by HanZo on 2007-02-18
I'm really starting to loose my hope... don't get me wrong I'm not here to complain, just wanted to say, for anybody who's got the same problem I'm experiencing here, that I don't think it's worth spending all this time in trying to get someting to run that will never do... I've been looking hard for a solution but looks like there is none.
The best thing is probably to try another distro, or stick with bloody ol'windows and wait for better times to come.

---

### Post by HanZo on 2007-03-27
I"m loosing my hope but I won-t give up... after some playing around with the bios I finally found out that there was a setting that would interfere with the scanner... and that was the "enable legacy usb" setting. I've turned it off and it seemed to work fine... I was happy for a day or two, then installed Feisty (beta) and things began to get awkward again. The scanner now is found every time, and it will even move and do preview and scans but it takes ages, the scanner makes some strange noize and will not move back to its original position once a task hase been completed...
It"s not a problem with other usb devices because I"ve unplugged all of my hardware and the problem still persisted.
I was about to consider the idea of switching completely to ubuntu but if I can-t get these things to work... could please somebody help me? I have searched every forum, every site... can"t find anything...

and here come the specs:

**Mobo:** ASUS A8v Deluxe
**Processor:** AMD Athlon 64 3000+
Video: Sapphire Radeon 9600pro Agp
Audio: Terratek DMX 6fire
Other things connected: wacom intuos tablet, usb hub, 2 canon printers, usb card reader, external harddisk.

Right now running Ubuntu Feisty Beta "with all the updates"
Software used to scan: Xsane wit snapscan backend (as autodetected by ubuntu)
I have even linked the appropriate firmware for this scanner in the snapscan.conf file.

---

### Post by HanZo on 2007-10-02
I'm just replying to myself here... but who cares...
Gutsy seemed to put an end to all my troubles. Installed the beta and everything seems to be fine, working out of the box.

---

### Post by vgrisham on 2007-10-14
HanZo! Nice soliloquy! :popcorn:

[This]("http://download.tuxfamily.org/arakhne/pool/libsane-epson-perfection/") file seemed to help Gutsy pick up my 2580; it wouldn't work out of the box as it did for you. But then, you had crooned long and hard in this thread, so I suppose the gods of 7.10 intervened on your behalf.

After a year hiatus, my scanner finally works again! :guitar:

Thanks Gutsy!

---

### Post by HanZo on 2008-04-03
Hey thanks man! this seems to work indeed! great thing! I was already loosing hope somebody would ever answer me on this...

---

