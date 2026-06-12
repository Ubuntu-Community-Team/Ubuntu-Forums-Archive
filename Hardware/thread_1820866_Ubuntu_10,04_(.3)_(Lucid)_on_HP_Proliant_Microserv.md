---
title: "Ubuntu 10,04 (.3) (Lucid) on HP Proliant Microserver"
date: 2011-08-08
forum: Hardware
---

### Post by purpleturtle on 2011-08-08
Has anyone had sucesss with 10.04.3 on an HP Proliant microserver?  The kernel version is current (2.6.32-33), and I believe the bios to be current.

I am experiencing frequent lock ups, particularly on the login screen if I leave it for ~10 mins without logging in. (It has also locked up when logged in when left unattended).

Even the live CD has locked up like this during the install (screen completely frozen, keyboard unresponsive, Alt+Sysreq+REISUB does nothing).

I've experimented with different display drivers, which made no difference.  I turned off all power save options, which made no difference either.

So, has anyone got 10.04 working reliably on the Proliant Microserver, or could I have a hardware issue perhaps?

TIA

---

### Post by purpleturtle on 2011-08-09
To answer my own question....

I tried lots of different live CDs today.

And despite memtest86+ successfully running all night, the problems I was having (freezing, kernel panics etc, mouse clicks not responding...) appear to be due to the non-ecc memory I installed (it was OCZ memory).

By messing around with bios settings and boot parameters I could generally coerce a particular version to work. But, as soon as I put the original ECC memory that came with the machine in, every version worked flawlessly with the normal default bios/boot params!

:confused:

---

