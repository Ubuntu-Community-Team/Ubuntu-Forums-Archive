---
title: "Neoware &quot;CA2&quot; thin client; how to change PXE boot options (hotkeys)"
date: 2009-11-28
forum: Hardware
---

### Post by youbuntu on 2009-11-28
My friend has four Neoware "CA2" thin clients, which we are setting up an LTSP with. We couldn't figure out how to make the CA2 PXE boot (boot from ethernet) and tried repeatedly to do so, to no avail, even resorting to removing the casing to see if there were jumpers to do it.

After some clever Googling skills :) I found the information - so here it is, shared for others:

Start the Neoware CA2 and Hit [SHIFT] [F10] repeatedly during and after the turquoise splash screen at start-up until a dark blue screen shows. Set 2nd entry on screen to INT 19 - Boot from network 1st. Save & exit.

---

