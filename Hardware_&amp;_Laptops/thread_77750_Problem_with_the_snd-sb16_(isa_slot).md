---
title: "Problem with the snd-sb16 (isa slot)"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by served on 2005-10-17
I have a problem!!
I installed ubuntu 5.04 and soundcard doesnt work :( when i add snd-sb16 in the sudo gedit /etc/modules list.
Then i upgraded it to ubuntu 5.10 but the problem remaines :S
What could i do to solve it?
With ubuntu 4.10 it worked and it worked fine!
I just had to add "snd-sb16" in the .../modules list and then restart and ready but now I cant see that its working.

Second problem is with my video i have Nriva TNT 64, 32 mb. My screen resolution is 1024x786 and only 60hz and i cant change it. What should i do?(it should be 80hz or 100hz)

---

### Post by theking2 on 2006-05-01
that's funny having the same problem. I did work this morning but after a reboot the card could not be located. As far as I remember (from the win95 time of this card) I had to specify two dma addresses and an interrupt. But how to do so in ubuntu puzzles me.

---

### Post by theking2 on 2006-05-02
I found what might have caused the problem in my case. I've recently added a USB card which was recognized without a problem. When I shutdown, remove it, and reboot: presto the SB16 card is backup again. 

After adding snd-sb in /etc/modules with sudo gedit /etc/modules I even have the wonderfull startup tune back!

There must be some conflict between the two cards. Is there a way of finding out DMA IRQ or whatever can cause the conflict? I have not found anything about this in the Device Manager.

---

