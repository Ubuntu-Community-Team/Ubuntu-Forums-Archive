---
title: "IBM port replicator problems"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by banditti on 2005-06-02
If I put my laptop in my port replicator, I get no video.  Thoughts?

T40P

---

### Post by alastair on 2005-06-02
No video where? the laptop screen or external monitor?

Maybe a BIOS setting to choose the display (and it defaults to the "wrong" one?)

---

### Post by Arthemys on 2005-06-02
In your BIOS, there should be a few options regarding video. My guess is that when it detects your port replicator or docking station, it sees the DVI port or something similar and switches over. Did you try the FN key and F7 (the key combo on my R51) for cycling displays?

---

### Post by banditti on 2005-06-03
A little more information might help.  One, I recently switched to Ubuntu from XP as my primary OS.  Before the switch, I would put it in the port replicator and it worked.  What I mean to say is it might not be a bios deal.

With that said, it goes in the port replicator closed and outputs via DVI to an external flat screen.

---

### Post by Arthemys on 2005-06-03
Yes but Windows has a way of overriding whatever the BIOS says, as there are drivers talking to the video card. It's possible.

---

### Post by gotmonkey on 2005-06-05
Hey Guys, 
do you have to add the monitor that is attached to the port replicator? I have a Viewsonic VP201B with native 1600x1200 resolution.

---

### Post by Vorian on 2005-06-27
What kind of monitor do you have?

---

### Post by aerials on 2005-07-09
[QUOTE=banditti]With that said, it goes in the port replicator closed and outputs via DVI to an external flat screen.[/QUOTE]

As far as I know, now one got that DVI port (neither on MiniDock nor PortReplicator II) to work with Linux yet. I've been able to connect my LCD to the dock via VGA, but the quality of the VGA signal is a shame, no way to work with that blurry image under UXGA resolution.

So I'm looking for a way to tell the (radeon) driver to use the DVI instead of the VGA port.

---

