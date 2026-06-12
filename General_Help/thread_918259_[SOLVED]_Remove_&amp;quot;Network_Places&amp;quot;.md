---
title: "[SOLVED] Remove &amp;quot;Network Places&amp;quot; entry?"
date: 2008-09-12
forum: General Help
---

### Post by FrostDust on 2008-09-12
I tried visiting an FTP server through the "Connect to Server..." option on the "Places" menu. My problem is that the server is still listed under places, and I can't figure out how to remove it. The menu editor doesn't show the "Places" menu at all, and I didn't see anything in the "Network" window, besides my home network. Does anyone know how I can remove the FTP server from that list?

---

### Post by mb_webguy on 2008-09-12
Open Nautilus, right-click the entry in the Places sidebar, and select Unmount.

---

### Post by FrostDust on 2008-09-12
Thank you. I normally don't have the sidebar open, so I never would have checked there.

---

### Post by AggravatedGestalt on 2011-01-18
Sorry, but this is being *un*solved. How do we accomplish such a thing these days? Seems some developers are very interested in restricting freedom. The above information no longer applies. And pardon me folks, but what's with all the restrictions in an alleged opensource OS? No disabling gnome tooltip balloons, and no removing networks from places? This is flagrantly stupid. 

PS: I always enjoy reading the pedantic and ridiculous replies by Canonical borgs, so say your worst.

---

### Post by FrostDust on 2011-01-18
Using Nautilus 2.32.0, it is indeed possible to unmount (and mount) an FTP location, which is properly reflected in Gnome's Main Menu's Places listing. My issue was and remaines solved, and mb_webguy's advice is still applicable. I just tested it and it works as expected.

---

### Post by AggravatedGestalt on 2011-01-19
I see several networks listed, with such properties:
Type: unknown type (application/octet-stream)
Size: Unknown
Location: network:///
Accessed: unknown
Modified: unknown

I am unable to mount, delete, or do anything to them. Why are they there, and why can I not remove them? If they are part of "my" network, why is a connection of any kind made without my consent? I do not have filesharing enabled. They also linger even while the network is down.

---

### Post by beaufils on 2012-01-29
+1

This last behavior is still there under 11.10 and this very annoying once your laptop were present on on a large LAN with a lot of shares :-(

---

