---
title: "Modem picks up but won't dial number"
date: 2005-01-10
forum: Hardware &amp; Laptops
---

### Post by J.K. on 2005-01-10
Hi
When I request the system to dial up, Using 'pon' in the terminal, I can hear the moden pick up(dial tone) but then it puts down without dialing.
When I tested it in W.....W.......Wi...., another operating sytem, it did the same thing, but I solved this by putting an 'x' in : modems->properties->connections->advanced->extra settings. How can I solve in Ubuntu?
Thanks

---

### Post by Danilo on 2005-01-10
Use "sudo pppconfig", go to "Change connection", select your connection, go to "Advanced options", change "Modem init" field from "ATZ" to something like "ATZX3" or simply "ATX3".

---

### Post by J.K. on 2005-01-10
Thanks Danilo, thats exactly what I was looking for.
Its working fine now. This post is proof.

---

