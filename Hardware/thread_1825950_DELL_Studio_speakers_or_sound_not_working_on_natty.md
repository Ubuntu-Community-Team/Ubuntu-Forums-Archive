---
title: "DELL Studio speakers or sound not working on natty"
date: 2011-08-16
forum: Hardware
---

### Post by ndefontenay on 2011-08-16
Hi,

When I plug earphones, they don't work on my DELL Studio 17.

So I've used the 

sudo gedit /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=dell-m6

trick. This worked great in the past.

but with natty, something new happens. Without this line, I get microphone and computer speakers. When I try to get earphone working and apply these lines, then they work and the built in microphone stops working.

I'm not sure what to do anymore.

Nico

---

### Post by ndefontenay on 2011-08-17
Nobody had this problem?

:(

---

