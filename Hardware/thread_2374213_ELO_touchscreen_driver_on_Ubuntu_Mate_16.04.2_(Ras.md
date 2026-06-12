---
title: "ELO touchscreen driver on Ubuntu Mate 16.04.2 (RaspberryPi)"
date: 2017-10-13
forum: Hardware
---

### Post by buddyrail on 2017-10-13
I've got an ELO touchscreen that I've got communicating fine with a laptop running Ubuntu Mate, but can't I replicate it on a raspberry pi 2.

The touchscreen input is attached through a USB to DB9 converter. If I listen to ttyUSB0 I can see the touchscreen inputs coming through, but it's not included in the xinput --list.
If I try sudo inputattach --elotouch /dev/ttyUSB0 it will hang for a while and then tell me it can't set the line discipline.
It looks like the elo module doesn't work the same on the pi version of Mate, but since I've been using Ubuntu for about three days now I'm not sure how to troubleshoot it further.

Is there something I'm missing to get the serial input added to the xinput list?

Thanks.

---

