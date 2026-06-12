---
title: "Hot Swapable Ubuntu"
date: 2015-08-12
forum: Hardware
---

### Post by GrimTheReaper on 2015-08-12
If I have two computers, each with a hot swap bay, can I safely move ubuntu back and forth between them on an SSD? I have to use ubuntu for work and I don't really have a budget for my work computer, and so I'd rather build something that I can easily move than have to use a laptop. Also would ubuntu freak out if the Mobos and or GPUs were different and would I have to keep them the same?

---

### Post by TheFu on 2015-08-12
Hot swap or not?  It depends. Not all drive chips are the same.

When you move a Linux install between 2 computers, the GPU and NIC are the main things that cause issues. Sometimes having a different CPU "level" might matter too - it depends on the types of programs being run - for example, if you use a hypervisor and swap between AMD and Intel CPUs, that would be important. Swapping between a Core2Duo and a Core i7 might matter too - under specific situations.

So ... I would stick with the same family GPU. Definitely do not mix AMD and nvidia. You really want to pick GPUs that use the same drivers. nvidia definitely uses different drivers based on the GPU used.

OTOH, you'll never know the issues until you try.

I wouldn't do this.  It isn't like $40 for another HDD is THAT much of an investment. I just bought one myself a few weeks ago. Just don't get an SSD - those just aren't necessary.

---

### Post by Bucky Ball on 2015-08-12
What exactly do you need to do? I'm just wondering because what apps do you have to use on Ubuntu at work? Many are cross-platform and can be used on Windows. Open or Libre Office for instance, Firefox, ... or it more specific to your occupation? Just a thought ... :-k

And yea, this:

[QUOTE=TheFu]When you move a Linux install between 2 computers, the GPU and NIC are the main things that cause issues.[/QUOTE]

Apart from being aware of this, just plop it in the other machine, boot and and see how you go. You'll need to change the BIOS to boot from that drive and may have issues with boot, but as for hardware, as above.

---

### Post by GrimTheReaper on 2015-08-12
> **Bucky Ball said:**
> What exactly do you need to do? I'm just wondering because what apps do you have to use on Ubuntu at work? Many are cross-platform and can be used on Windows. Open or Libre Office for instance, Firefox, ... or it more specific to your occupation? Just a thought ... :-k


Atom, Git, Hexchat, Eclipse, Slack, and I have a bunch of environmental variables and settings that I can't really replicate on my home computer. I have to use Ubuntu for work (otherwise I'd use debian), and I don't want to use windows after they decided to sell their user's information.

---

