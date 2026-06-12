---
title: "Laptop Speakers and headphones problem"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by fwallace99 on 2007-05-27
Hi all. I am running Ubuntu Dapper Drake 6.06 LTS. I have a Toshiba Satellite A135-S2276.

I've installed the ALSA drivers and libraries and utilities, and edited my /etc/modprobe.d/alsa-base file to get the line added at the bottom:

options snd-hda-intel model=3stack

OK, well and good. However, I still can't turn off the Laptop speakers while keeping my headphones sound. Since this is a laptop, you can see why I want this feature. A bit embarrassing to say the least if my sound is blasting out.

[Interesting the volume hardware control at the front works with the ALSA Mixer, nice touch.]

I am told this is a known issue, searching through the forum suggests no one has an answer.

All I need is any work-around to allow me to mute speakers while keeping headphones. So far mute speakers does not do anything (they keep playing). Any help would be greatly appreciated.

Thanks.

---

### Post by Ken_Lewis81 on 2007-05-27
I think that ALSA is ignoring the switch in your headphones port to switch off your speakers (the one that does 'plug headphones in, speakers turn off').  Have you filed a bug with the ALSA bug-tracker about this?  They will need hardware details but should be able to fix the issue.

Take care.
Ken.

---

### Post by fwallace99 on 2007-05-28
Hi Ken, no I have not filed a bug report with the ALSA folks. I will do so and if there's a bug fix I'll post it here.

Thanks.

---

### Post by kekc on 2007-06-07
Fixed in 1.0.14 AFAIK

---

