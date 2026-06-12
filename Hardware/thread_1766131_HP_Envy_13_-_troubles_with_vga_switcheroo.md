---
title: "HP Envy 13 - troubles with vga_switcheroo"
date: 2011-05-24
forum: Hardware
---

### Post by ilembitov on 2011-05-24
Hi, all.

I have installed Ubuntu 11.04 on HP Envy 13. This laptop has two GPUs - Intel GMA4500MHD and ATI Radeon HD 4330, so I need some kind of switching.

I have followed this guide: [http://linuxenvy.blogspot.com/search?updated-max=2011-01-17T15%3A26%3A00-08%3A00&max-results=7](http://linuxenvy.blogspot.com/search?updated-max=2011-01-17T15%3A26%3A00-08%3A00&max-results=7)

However, when I run the switch_between_cards script and choose either integrated or dedicated GPU and the reboot (using the shutdown script), the machine simply won't boot. I mean, I get a black screen straight after GRUB, and the disk i/o stops shortly after.

Then, I have to force reboot (using the laptop's power button) a couple of times until I get to boot into my system. However, as soon as I run switch_between_cards again, I see that both GPUs are still running.

What do I do?

P.S.: is my card still supported by the recent Catalyst driver? Last I've tried installing it, the control center said it can't find my ATI card. But I couldn't find any mention of my card being deprecated on ATI site.

---

