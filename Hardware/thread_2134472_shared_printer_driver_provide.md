---
title: "shared printer driver provide"
date: 2013-04-11
forum: Hardware
---

### Post by creepwood on 2013-04-11
I have an ubuntu machine as a server (12.10 desktop). I have a shared printer through samba connected. It works.

What I wonder is, how can I make the ubuntu machine provide the right drivers depending on what OS uses the printer. For instance. A windows 7 machine wants to print for the first time, doesn't have the drivers installed for that printer. Instead of downloading the drivers for that printer from the manufacturers webpage.

I did some googling but didn't come up with the right search words.

---

### Post by conradin on 2013-04-11
generic postscript drivers. Does your printer have a network interface? is it connected?
what type of printer is this? 
samba isnt what I would try first for this type of operation.
is there support for windows7 from the manufacturer?

---

### Post by creepwood on 2013-04-11
Thanks for your reply.

The printer is working, I can already print from my windows machine. The ubuntu machine is sharing it through samba. I just want ubuntu to also driver host the as well :) It's HP P1005 driver connected with USB to ubuntu machine.

---

