---
title: "Dual monitors from 2 graphics cards?"
date: 2008-10-15
forum: General Help
---

### Post by MunkyJunky on 2008-10-15
I'd like to have dual monitors on my PC, just wondering if it's possible to do. I have an Nvidia GeForce 6600 LE, with dual output (VGA & DVI), and my motherboard has onboard graphics (VGA).

I have a 19" VGA monitor, and a 15" HDTV with VGA input, and a spare VGA cable. Basically, can I have dual monitors, one output off my Geforce card, and one from the motherboards onboard graphics card? And if so, how would I go about setting it up?

---

### Post by howefield on 2008-10-15
> **MunkyJunky said:**
> I'd like to have dual monitors on my PC, just wondering if it's possible to do. I have an Nvidia GeForce 6600 LE, with dual output (VGA & DVI), and my motherboard has onboard graphics (VGA).

I have a 19" VGA monitor, and a 15" HDTV with VGA input, and a spare VGA cable. Basically, can I have dual monitors, one output off my Geforce card, and one from the motherboards onboard graphics card? And if so, how would I go about setting it up?

You probably can but you can also run dual monitors from the one card, (your Nvidia)

Install nvidia-settings and configure from there.

---

### Post by MunkyJunky on 2008-10-15
I know I can run 2 monitors off the Nvidia, but that has one VGA output, and one DVI output. I'm just trying to save a bit of money and not need to have to buy a converter. 

Is it possible through the motherboard & Nvidia? Or will I HAVE to buy an adapter? I don't care if getting it to work through 2 is tricky, I'm very comfortable with terminal.

---

### Post by overdrank on 2008-10-15
> **MunkyJunky said:**
> I know I can run 2 monitors off the Nvidia, but that has one VGA output, and one DVI output. I'm just trying to save a bit of money and not need to have to buy a converter. 

Is it possible through the motherboard & Nvidia? Or will I HAVE to buy an adapter? I don't care if getting it to work through 2 is tricky, I'm very comfortable with terminal.

Hi and you can try and use the command with the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and setup both graphics there. I tried it once with intel and nvidia and almost had it working but moved on to other things :)
The adapter you are speaking of is not expensive at all maybe $2.

---

### Post by MunkyJunky on 2008-10-15
Well i Live in a big city where everything is overpriced. It would cost me around £7, and I'm a university student now and need that £7 to eat. I'll have a  go with the command, cheers.

---

