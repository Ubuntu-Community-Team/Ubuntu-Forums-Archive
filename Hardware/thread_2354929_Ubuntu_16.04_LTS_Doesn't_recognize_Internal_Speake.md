---
title: "Ubuntu 16.04 LTS Doesn't recognize Internal Speakers, microphones, or headphone jack"
date: 2017-03-07
forum: Hardware
---

### Post by patrickhuie19 on 2017-03-07
[http://www.alsa-project.org/db/?f=2e5b257a5fefe59a59228b29d26e7200d1eb5d5e](http://www.alsa-project.org/db/?f=2e5b257a5fefe59a59228b29d26e7200d1eb5d5e)

My laptop is unable to recognize or find any output or input devices that I believe connect directly to computer hardware (?). However, USB bluethood headphones work. 

The problem is confounded by the fact that when I dual boot into Windows, windows is also unable to find any internal input our output devices.

This problem started after I suspended Ubuntu (like the log out, suspend, shut down menu) a couple days ago.

---

### Post by Autodave on 2017-03-07
That sounds to me like your sound card called it quits. And in a laptop, that is usually the mother board.  If you are not ready to ditch the laptop, you may want to look into getting a USB sound card.  

I am *assuming* that your USB ports are still working. If you know anyone that has a USB sound card, you might want to ask them if you could try it before you buy one.

---

### Post by Autodave on 2017-03-07
I just checked online: the good news is that the USB sound cards are very small and inexpensive.

---

### Post by patrickhuie19 on 2017-03-08
Thanks for the suggestion! 

I'll try to see if I can do that :)

So is it just a weird coincidence that this happened when I pressed suspend? Another more intriguing note - this has happened before (when i pressed suspend), but after monkeying around with windows audio settings, it fixed itself when I booted into Ubuntu.

---

### Post by Autodave on 2017-03-09
Try one other thing before you order that USB card: power down machine, remove battery, wait 10 minutes. Put battery back in and see if sound now works.

---

