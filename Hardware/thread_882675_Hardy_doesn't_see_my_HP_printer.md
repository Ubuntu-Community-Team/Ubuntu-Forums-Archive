---
title: "Hardy doesn't see my HP printer"
date: 2008-08-07
forum: Hardware
---

### Post by RgnKjnVA on 2008-08-07
Something happened and suddenly Ubuntu doesn't see my HP Photosmart D5160. It's configured in CUPS with the correct driver, listed as 'accepting jobs, idle, published' and my lsusb results (below) show that the printer is in fact connected. However, I never see the printer icon in the upper panel like in the past when it's connected. My apps reflect this as well, not showing the HP printer as an option. If I try to print a test page I'm prompted for my login/pwd but nothing happens once entered. I've re-logging in and rebooting to no avail. WTH?! This is incredibly frustrating considering I didn't DO anything to make this happen >=o( Any help would be appreciated.


> lsusb
Bus 002 Device 010: ID 03f0:c402 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 035: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 004: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 003: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 001 Device 001: ID 0000:0000

---

### Post by ihatetryingtopickaloginna on 2008-08-07
Same thing happened to my Epson printer. It was working fine, and then it wasn't. Ubuntu saw the printer, but it wouldn't print. So I ran this program, gnome-cups-manager and it fixed the problem. Try it and see if it helps. You may have to install it first if it isn't installed already. It wasn't on mine.

---

### Post by silvanus2005 on 2008-08-07
You should install HPLIP using Synaptic, and your printer will work , I think.

---

### Post by RgnKjnVA on 2008-08-07
Thanks for the suggestions. HPLIP was already running. That cups manager appears to just be a UI for what you can already do from [http://localhost:631](http://localhost:631) unless I'm missing something.

I eventually removed all printers configured and started over with a clean CUPS slate. Appears to be working now "...but for how long?" is the question.

---

### Post by ihatetryingtopickaloginna on 2008-08-07
> **RgnKjnVA said:**
> That cups manager appears to just be a UI for what you can already do from [http://localhost:631](http://localhost:631) unless I'm missing something.

Hmm, didn't know about the cups url. Interesting. I wonder what else can be done this way.

---

