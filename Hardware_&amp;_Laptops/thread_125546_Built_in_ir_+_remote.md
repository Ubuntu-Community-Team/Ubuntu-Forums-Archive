---
title: "Built in ir + remote"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by pelle.k on 2006-02-04
Hello. I've been struggeling to find out exactly how my Fujitsu-Siemens Amilo M3438G works, which has a built in ir reciever (dont ask me if it's SIR or not because i honestly don't know, the documetation is lacking such facts).
The remote control seems to be a eDio21 RC106, rebranded with fujitsu-siemens logo.

I've tried to google it, but there is no relevant information regarding the subject.
I find NO modules being loaded (lsmod | grep ir) (dmesg | grep ir) (cat /proc/bus/input/devices), though some buttons acctually work, and the rest of the buttons IS sending keycodes (I use xev to scan). The buttons that work gives the exact same output as the keyboard output, which has led me to belive the ir controller MAY be hardwired to the keyboard. If that is the case, i wont be able to change the keycodes to something else because i will be changing my keys on the keyboard as well...

Can somebody please give me some advice to track down what device is responsible for outputting the keycodes to X?

I'm not keen on trying out lirc, because it's a bitch to set up, and i don't even now what module i should be using.

---

### Post by pelle.k on 2006-02-05
Can someone please advice on how to (at least) make freevo/mplayer/xine react to the keycombinations which at the moment is not bound to any funtion in KDE, as i have noticed that actions are bound to the window with focus, and i will have freevo/mplayer/xine in fullscreen on my tv (screen1), while a normal KDE desktop on screen0.

---

