---
title: "Epson V500 random behaviour on Ubuntu 14.04"
date: 2014-11-20
forum: Hardware
---

### Post by al.adab on 2014-11-20
hello,

A year later I've re-connected an Epson Perfection V500 Photo to my Asus UX301 - OS: Ubuntu 14.04 + related software: "Xsane", "Simple Scan", "ImageScan! for Linux" (drivers: *iscan-data_1.31.0-1_all.deb, iscan-plugin-gt-x770_2.1.2-1_amd64.deb, iscan_2.30.0-1~usb0.1.ltdl7_amd64.deb*, all downloaded from the Epson website). 

"ImageScan! for Linux 2.23.0" seems to work fine, except that starting the program is a total hit&miss. This is the pattern (have repeatedly tested it over the last 12 hours): 

- I switch on the Epson + connect it to the Asus via USB (the Epson's front green led is the only sign that that the scanner is on - i seem to recall that the Epson produced some noise upon being switched on, but I'm not entirely sure);
- if I try to launch "ImageScan! for Linux" from "Applications", nothing much happens: either the program doesn't respond or I get the message "could not send command to scanner";
- if I type *sudo iscan* or *iscan* on Terminal, the Epson initially produces that kind of noise (like it's calibrating itself) I'd expect to hear when I turn it on (see above). After that, nothing happens: the cursor on the terminal goes on blinking but "ImageScan! for Linux" doesn't start. 

The only thing that *almost* consistently seems to make the difference is if I do the following: 

a) I unplug the USB cable scanner<>pc (without turning off the scanner). At this stage the message "could not send command to scanner" pops up. I close the message;
b) I plug the USB cable scanner<>pc back in and I re-type *iscan* on Terminal. The "ImageScan! for Linux" windows appears and I can start using the Epson ("ImageScan! for Linux" seems to work all right, I haven't noticed anything wrong so far, the Epson does its job, in other words). 

Is there anything I can do to fix this? Btw, I tried two different (new) USB cables, so that's not the issue, I guess. Thank you!

---

### Post by Pilot6 on 2014-11-20
Turn off xhci in USB settings of bios.

---

### Post by al.adab on 2014-11-21
er...many thanks for your suggestion and please forgive my ignorance: how do i "turn off xhci in USB settings of bios"? i googled everywhere and found nothing...thanks!

---

### Post by al.adab on 2014-11-21
apologies (dumb questions): got it and it did the trick. Many thanks!

---

