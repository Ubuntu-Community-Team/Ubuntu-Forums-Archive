---
title: "Freeze with TV card Hauppauge"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by kjbstar on 2005-12-11
Hello there,

first, please excuse me for my english skills !

Here is the problem:
on a first PC where my TV card WinTV Primio was installed before Ubuntu (Breezy), I've never had any problems: I install Ubuntu (dual boot w/ XP), I install tvtime, all works perfectly !

I decided to move my TV card from this PC to another one, where Ubuntu Hoary is already installed. And the headache begins...

With a "**lspci**", my card is correctly detected by the system.
I've read I had to install it manually loading modules, tell the type of card (3 for mine), etc...
But when I do a "dmesg | grep bttv " to get the framebuffer, I got plenty of " **bttv0: IRQ lockup, cleared int mask [bits: OFLOW PPERR]** " !
Worst: trying a "**scantv**", starting tvtime, or trying to load the card like this: "modprobe bttv card=3" result on a freeze of the system :/

May you help me ?
Thanks,
kjb

---

### Post by BoyOfDestiny on 2005-12-12
[QUOTE=kjbstar]Hello there,

first, please excuse me for my english skills !

Here is the problem:
on a first PC where my TV card WinTV Primio was installed before Ubuntu (Breezy), I've never had any problems: I install Ubuntu (dual boot w/ XP), I install tvtime, all works perfectly !

I decided to move my TV card from this PC to another one, where Ubuntu Hoary is already installed. And the headache begins...

With a "**lspci**", my card is correctly detected by the system.
I've read I had to install it manually loading modules, tell the type of card (3 for mine), etc...
But when I do a "dmesg | grep bttv " to get the framebuffer, I got plenty of " **bttv0: IRQ lockup, cleared int mask [bits: OFLOW PPERR]** " !
Worst: trying a "**scantv**", starting tvtime, or trying to load the card like this: "modprobe bttv card=3" result on a freeze of the system :/

May you help me ?
Thanks,
kjb[/QUOTE]

Hmm, it worked perfectly with Ubuntu Breezy. On the other machine (Ubuntu Hoary), you are having problems. Why not just upgrade from Hoary to Breezy?

---

### Post by kjbstar on 2005-12-18
Hello,

some news: I upgraded as you adviced me from Hoary to Breezy.
Now, it is a little better: I don't have any freezes anymore :)

But I have the same errors with a dmesg command. Sometimes, it shows me some "good lines" (pll ok, bttv0: registered device video0, etc...), but never a complete good dmesg.
With tvtime, I have a blue screen.
With xdtv, it's a black screen, and with the tvscan of xdtv, it find some channels, but always with a black screen, and I can see infinites "in/out errors".

I willl get crazy :/

---

