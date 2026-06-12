---
title: "Dual monitors, where to begin?"
date: 2011-12-31
forum: Hardware
---

### Post by Formerly on 2011-12-31
I'd like to configure my PC to run two monitors. I've never done this before so it took me a while to understand my computer only has one graphics card. After reading up apparently it's possible to hook a second graphics card instead of trashing the original card for one with a dual output.

After looking around I can't really find if this is possible for me in particular, though. "*Graphics* Gallium 0.4 on ATI RV370" tells me I have an ATI RV370. So then by the previous logic I would assume I can buy another ATI RV370 and hook it up.

Am I wrong, or am I right? And if I am right, how exactly would I hook up a second card?

---

### Post by tomski on 2011-12-31
many ati cards which use this core (ATI RV370) have 2 sockets 1 DVI & 1 VGA (google for differences) if this is the case all you may need is the correct cables/adapter to get the second connector active.

If your card only has one connector then you may need to look into getting a second card BUT this could pose you further problems in that your mobo may only support 1 GFX card at a time, Your mobo may only have 1 socket (PCIeX16) & numerous other issue which may hamper you.

but essentially once you have both monitors active i would install the proprietry drivers (via jockey or website) & then use the config tool provided by the drivers to get both monitors configured for use in xorg.

so to summerise

1) look at what you have & what it supports
2) either purchase a second cable/adapter or card if needed
3) connect both monitors & install relevant driver
4) configure xorg via driver config utility

---

### Post by tomtiger11 on 2011-12-31
> **tomski said:**
> many ati cards which use this core (ATI RV370) have 2 sockets 1 DVI & 1 VGA (google for differences) if this is the case all you may need is the correct cables/adapter to get the second connector active.
 
If your card only has one connector then you may need to look into getting a second card BUT this could pose you further problems in that your mobo may only support 1 GFX card at a time, Your mobo may only have 1 socket (PCIeX16) & numerous other issue which may hamper you.
 
but essentially once you have both monitors active i would install the proprietry drivers (via jockey or website) & then use the config tool provided by the drivers to get both monitors configured for use in xorg.
 
so to summerise
 
1) look at what you have & what it supports
2) either purchase a second cable/adapter or card if needed
3) connect both monitors & install relevant driver
4) configure xorg via driver config utility
 
Adding to that, you want to make sure you have a spare slot for your graphics card (obviously) and make sure that all of your cables and stuff work. Trust me, having a perfect graphics card but a broken cable is really annoying...

---

### Post by Formerly on 2012-01-01
> **tomski said:**
> many ati cards which use this core (ATI RV370) have 2 sockets 1 DVI & 1 VGA (google for differences) if this is the case all you may need is the correct cables/adapter to get the second connector active.

So this means I can use my unused DVI output as a working second VGA output just by use of an adapter?

---

### Post by gordintoronto on 2012-01-01
A much better solution would be a DVI cable and a monitor which supports DVI input. Most monitors built in the past four years support DVI.

---

### Post by Haneef Mubarak on 2012-01-01
But either way, if you're looking at an extended desktop (not mirroring), then you need drivers. If you have NVidia, I can give you instructions on getting the latest drivers.

---

### Post by tomski on 2012-01-02
> **Formerly said:**
> So this means I can use my unused DVI output as a working second VGA output just by use of an adapter?

yes exactly that but in terms of adapter i would recommend the 'adapter cable' essentially is it an adapter & cable combined into one & this will ensure that the card recognises the monitor, i suggest this because the last time i did this setup with ATI card i had issue's with the second monitor connected to the VGA port not being initialised by the card upon power up so i researched a lil bit & found that adapter cables resolved this issue but you have to fork out a couple of extra $$ or ££

good luck & don't forget to use propriety ATI drivers

---

### Post by Formerly on 2012-01-02
Alright, thanks everyone! I'm marking this one as solved

---

