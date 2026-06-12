---
title: "kernel panic - not syncing"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by blunt on 2005-05-09
hey. 
im sorry if this is the wrong place to post this thread, but i think that the problem i have is related with my modem and i dont know where else i could post this.

i cant really explain my problem cos i cant see the whole message, so thats the first thing that id like to ask about; **where can i see the output of the boot process of ubuntu?** this kernel panic happens shortly after loading the network interfaces, right after loading the package pppoe i believe. the only "readable" text i can put here in the meanwhile is this:

"<0> Kernel panic - not syncing: fatal exception in interrupt"   ](*,) 

please tell me how can i see the message to post it here so maybe someone can help me.

dont know if this matters, but here it goes: i have a P4 2.4, motherboard asus p4s8x-x, wireless mouse and keyboard via usb, speedtouch 330 adsl modem (grey), geforcefx 5200 and a sound blaster live LS among other stuff, but these are the ones that i believe that may be related to this problem, especially the modem.. but as i said before, i have to get the output of the buffer before. 

thank you in advance

---

### Post by blunt on 2005-05-11
No one?

---

### Post by Kurse on 2005-05-11
This is like saying "I was driving down the road, and my car just stopped! Whats wrong!? How can i fix it?" 

People cant help if ya dont give them enough info to help troubleshoot.

---

### Post by blunt on 2005-05-11
[QUOTE=blunt] i cant really explain my problem cos i cant see the whole message, so thats the first thing that id like to ask about; **where can i see the output of the boot process of ubuntu?** (....) please tell me how can i see the message to post it here so maybe someone can help me. [/QUOTE]


i know that.. but i have to know how to get the problem message to put it here...
can you help out pls?

---

### Post by alastair on 2005-05-11
You could try stopping at GRUB (ESC) and doing a "recovery" option boot.

Logs are under : 

/var/log

i.e. syslog, dmesg etc.

You could try disabling the (supposed) problem device i.e.. do not startup PPP (pppoe?).

Or try a boot with "acpi=off" or/and "noapic" (perhaps) i.e.

stop at boot (ESC)
select kernel - and "e" to edit
edit kernel line - "e" - add "acpi=off noapic" at end.
boot - "b"

---

