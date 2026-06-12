---
title: "WiFi active LED"
date: 2008-05-27
forum: Hardware
---

### Post by gdbtx on 2008-05-27
OK, so I'm trying to be perfect - sue me.

On Hardy with a Compaq F700/F750 I have everything working except the LED indicator for the Atheros AR242x WiFi card. The card is fully functional AFA connectivity. The card is controlled by a sliding switch and should show blue when active/connected but never changes from orange, i.e. shows inactive even though fully functional. 

Any known fixes or ideas for solving this?

---

### Post by amingv on 2008-05-27
I've never seen one of the default drivers work the LEDs right (since they're made to be as generic as possible; I would assume), so you could use ndiswrapper or find your way around at driver level, though I don't see how this is a big deal if it works fine.

---

### Post by steveneddy on 2008-05-27
With the Intel WiFi driver one would install hardy backports to correct the issue.

---

