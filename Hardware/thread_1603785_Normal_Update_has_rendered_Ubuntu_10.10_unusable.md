---
title: "Normal Update has rendered Ubuntu 10.10 unusable"
date: 2010-10-23
forum: Hardware
---

### Post by Buzzthebuzzsaw on 2010-10-23
Hi All,

I'm currently running Ubuntu 10.10 and it's been working perfectly since I upgraded from 10.04.

Everything was fine until yesterday when I booted my machine and the wireless networking was not working, the bluetooth is not working and an external display that was working fine at 640x480 (it's for sending the laptop display to a tv) is now an unsupported configuration aparently.

All of these have been working until yesterday.

I noticed an install of a linux image which I presume has caused the issue.  Does anyone have any ideas?

I'm currently using an older linux image but the display is not working on this either.

Any help would be greatly appreciated as in this state the latest linux image in Ubuntu is unusable.

---

### Post by Buzzthebuzzsaw on 2010-10-24
Ok it seems to be working again.

My laptop is a Dell Inspiron with an ATI Graphics card.
I had a poke around in the ATI Catalyst Control Centre and managed to get it working again.

I don't know why I had to do this now and not after the initial install.  I wonder was there a new release of the ATI Drivers?

Regardless it's working for the time being.
If anyone can shed light on what has updated or how I can figure out what recent updates have been applied it'd be great.

Synaptic has a history feature but the Updater appears not to have one, anyone know if/where a history of updates is?

---

### Post by cpmman on 2010-10-24
Try System - Administration - Log File Viewer - dpkg.log

---

