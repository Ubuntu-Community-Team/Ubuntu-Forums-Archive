---
title: "serious mouse lag"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by BillyBeag on 2008-02-05
Hi I have just installed 7.10 from SUSE 10.2, the system is a bit wierd, it is a P3 450Mhz with 512mb ram and 60 gb HDD.. in a pizza box.
I have a MS "wheel mouse optical USB and PS/2 compatible" with just your normal amount of buttons.
Previously, on SUSe I had no problems with this mouse or the system, which I use for a LAMP and SAMBA server. It is a bit slow, but I have had it running all sorts of stuff since 1999....

After the Ubuntu install however I am getting very heavy mouse lag on the desktop, when the system starts at logon I have a whizzy little pointer that is a joy to aim with, then when the taskbar at the top loads it's icons, suddently my wee arrow goes very very slowly, even jumping from one position to then next as if the system or display is not catching up.
 I have changed to Xubuntu from Gnome, I have tried a few changes to the xorg.conf, I have tried using the generic open source drivers for the Nvidia Gforce 4 ti4200 agp card, which I actually swapped into from a previous GF  MX440, to see if it would help.
Now I don't actually think it is the mouse, though I am no expert, I tried the 7 button intellimouse version to see if that would help too, I am more inclined to think there is something eating the resources that is slowing the display down, though dragging seems to be smooth enough.

I don't know what else to try, I am tempted to access it from the LAN but I like to see the desktop when I fiddle with stuff, the alternative is also to go back to SUSE but I WANT Ubuntu. :)
quite a dilemma  eh?

---

### Post by Yellow Pasque on 2008-02-05
If you can, click System -> Administration -> System Monitor. Look around there and see what process is eating your CPU (asuuming there is one).

---

### Post by BillyBeag on 2008-02-05
Hmm 
I have had a pretty good look around in there, I have ended a few processes i know I don't need like bluetooth and cron, really I cannot see anything that is using more than the actual system monitor itself, which is at 14% ..
This is a minimal; installation, I only really want it to run the LAMP, Samba & VSFTP servers, but I would still like to use the GUI too.

I think I might try the 6.06 server package if I can't get over this.

Oh and BTW I installed this using Unetbootin perhaps there were options for the Kernel it didn't configure right... Maybe a reinstall with a different kernel config..
As usual I seem to need to get deeper into Linux technical issues than I have height... :shock:

---

