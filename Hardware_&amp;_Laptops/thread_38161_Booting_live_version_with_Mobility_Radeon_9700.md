---
title: "Booting live version with Mobility Radeon 9700"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by zdlugasz on 2005-05-30
Hi
I am completely new to Ubuntu and with small exp with Linux as well.
To be short: I downloaded and burned "live" version of 5.04 (in fact Kubuntu DVD) to test how does it looks like, do I like it. I tried it at my laptop : Acer Extensa 2902LMi with ATI Mobility Radeon 9700 and 15.0" SXGA+  display (standard resolution is 1400x1050) and during booting I am getting blank display. Later I tried it to run at desktop PC and was working. 
What I have seen, at my laptop even boot manager screen (where I choose to run live version or to install) did not show this bluish graphic in the background. And during loading consecutive modules (I got Yenta and USB ok) the last line was sth. like : Starting system log daemon"
If I guess correctly the next in queue should be frame buffer, graphical environment or whatever.
During booting with vga=771 laptop hung at the beginning, almost right after I pressed Enter.

Can you propose solution how can I test it on my laptop?

THX


EDIT: I went 1 step ahead - those noapic nolapic options caused that it hung. With vga=771 only I could choose language and it started to detect hardware/install modules (e.g. Floppy, which I do not have). However, sth. like 10 or 20 seconds later I am still getting completely blank screen and no response.
I had to use power button and then my display "awakened" in text mode and I got messages  :mad:  that Ubuntu comes with NO WARRANTY, linux switched to runlevel 0, sent TERM, KILL, stopped K display manager, daemons and shut everything down.

---

