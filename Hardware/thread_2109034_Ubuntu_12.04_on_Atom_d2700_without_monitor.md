---
title: "Ubuntu 12.04 on Atom d2700 without monitor"
date: 2013-01-26
forum: Hardware
---

### Post by madman11 on 2013-01-26
Hello everybody,

i'm running an Intel Atom d2700dc which functions as a fileserver.

Since i updated my Ubuntu it stopped starting headless, which is essential for me because i don't have the possibility to attach a monitor at all times.

First of all i tried many distributions with a 3.* kernel. None of them want to boot headless.
The last one i was able to start headless was a Debian squeeze with 2.6.* kernel. But i don't want to stick with it because i want some functions which came with 3.*.
What is worrying me the most is, that even Ubuntu Server won't start headless unless i deactivate my graphic chip in bios.
I also looked for bios options to disable error messages when no monitor is connected. But i didnt't find anything.

So the last weeks i was searching for solutions and found threads about using vesa driver + xorg.conf or dummy driver + xorg.conf + nomodeset in grub. (Like [here]("http://ubuntuforums.org/showthread.php?t=1832456").
 
I tried so much but it is never starting headless (it stops in a state where i can't ping it or do anything else with the system)

I also found a solution with a dummy plug for VGA, but my Board only has HDMI and DVI-D (no analog pins ...)

Are there any solutions i didn't think about? (Maybe another way to simulate a monitor)

It would be awesome if somebody has hints for me.
Tell me if more information are needed.

---

### Post by ahallubuntu on 2013-01-26
A server edition should certainly start headless.  I have one Ubuntu 12.04 server that starts headless and I didn't do anything to enable it.  Perhaps it's a limitation of your BIOS.

---

### Post by madman11 on 2013-01-26
Yeah, i would assume it's something about the board itself.
But i can't get in my head why i can boot a Debian Squeeze without any troubles.

---

