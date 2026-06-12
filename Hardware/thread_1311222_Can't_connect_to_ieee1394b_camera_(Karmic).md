---
title: "Can't connect to ieee1394b camera (Karmic)"
date: 2009-11-02
forum: Hardware
---

### Post by essenv on 2009-11-02
Hi!

This is the first time I'm posting a question to ubuntuforums - my apologies if I picked a wrong category.

I'm having problems with an ieee1394b camera (Sony XCD-U100). The FireWire card, as well as the camera are detected (at least on some level), since* **lsmod | grep 1394*** gives:
[I]raw1394                29096  0 
video1394              18600  1 
ohci1394               33780  1 video1394
ieee1394              100896  3 raw1394,video1394,ohci1394[/I]

***lspci** *shows that the card is present:
*12:04.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)*

and

[I]**cat /var/log/messages | grep ieee**
Nov  2 16:50:45 nnn kernel: [   13.081697] ieee1394: raw1394: /dev/raw1394 device initialized[/I]

also raw1394 is present in /dev/ and I ran *chmod 666 /dev/raw1394*

I've installed Coriander and it also shows that the camera is detected - however I can't get any images.

In Kino, when I switch to Capture tab I get "No AV/C compliant cam connected or not switched on?"

testlibraw shows 1 connected device and agrees to talk with it
dvgrab tells me: "Error: no camera exists"

I don't think it's even necessary to say, but I'm not an expert on this field :), so *any* help would be great!

cheers,
Mathias

---

### Post by essenv on 2009-11-05
Bump

---

### Post by essenv on 2009-11-05
Problem solved. 

I switched the cable to the other 1394b connector (the camera has two) and got Coriander working. No idea why the other connector didn't work..

---

