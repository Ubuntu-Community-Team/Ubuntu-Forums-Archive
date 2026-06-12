---
title: "Jaunty Dial-up problem..."
date: 2009-08-21
forum: Hardware
---

### Post by Gizenshya on 2009-08-21
In Jaunty, I'm trying to connect my mom's comp to the internet... but the modem doesn't show up.  The comp is an HP a6433w, and the modem is connexant (sp?).  In windows it shows up as a "PCI soft data fax modem with SmartCP", nanufacturer CXT (which apparently means connexant).

I've googled till my face turned blue, and the only lead that I've found was from years ago about a site called "linuxant.com."  The problem?  They want to limit the hardware that ***I*** own to a trickle, and hold it ransom unless I pay *them* to use **my** hardware.  I'll keep it clean, but you can probably guess what I suggest they do with their drivers...

But that info is years old.  I haven't checked the exact model of my modem yet (lspci will work maybe?), but I'll post it asap.  I'm just praying that there is some new info/options available since 2007.

This is the only thing keeping this computer attached to windows... and it's a biggie :'(

If I find no luck herem I'll try swapping a modem from another computer.  All of the modems work with windows, and all are untried with linux.

let me know if you need any more info.

thanks in advance

[off topic] HP is clueless.  Completely clueless.  They said that they aren't trained for linux issues.  Honest, and what I expected... so I started asking about windows and reformatting.  After a LONG conversation about downloading a windows disk from the HP website (in vain) I was finally transferred to someone who informed me that there never was such an option. >.<  [/off topic]

---

### Post by Gizenshya on 2009-08-21
command outputs...

lspci: Conexant Systems, Inc. HSF 56k Data/Fax Modem

uname -m: i686

uname -r: 2.6.28-11-generic

I got that info and went to the linuxant site and downloaded the driver with that info.  I'll reboot in ubuntu and try it.

PS: just noticed... there are no i686 drivers.  I don't know what will happen when I try to install the i386 drivers (probably nothing).  I might have to dig up a 8.10 i386 disk...  stay tuned

---

### Post by jefelex on 2010-01-06
I'm having an awful time trying to figure out what is wrong in my jaunty setup - I have a conexant modem in my Compaq laptop - it worked fine with 8.10 (after a bunch of tweaks), but I am basically unable to get it to stay trained with 9.04!  I have not tried to renice the process yet - that may help, I'll try that tomorrow, but it is frustrating to say the least!  I'm wondering if anyone else has come up against this problem, and had any solutions!! :-)

TIA

John

---

