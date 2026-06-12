---
title: "PS/2 keyboard w/USB adapter perpetually resets"
date: 2013-04-19
forum: Hardware
---

### Post by kipnflip on 2013-04-19
I'm having a keyboard problem, and have googled until my eyes were numb trying to find precisely this problem, or something close to it. My apologies if this has been asked and answered elsewhere.

I got a new computer, Dell 8500, last month (March 2013), and installed a Lubuntu 12.10 dual boot with Windows 8. So far so good. The new computer came with wireless keyboard and mouse, which use a single USB dongle. The mouse was jittery at first, but that was solved by using a different USB port for the dongle, and that's probably not related to the current issue.

I gave the wireless keyboard the "old college try," but after a month, just didn't like it. I like my old, large, "clicky key" keyboard (Dell SK-8110) with big meaty keys. It's PS/2, while the new computer has only USB. No problem - I got a Belkin PS/2 to USB Y-adapter, and connected the keyboard to the purple part. (I still use the wireless mouse.)

I've used two keyboard modifications for years: "xset r rate 250 30" to give a delay/repeat that's to my liking, and a trusty old 9-line xmodmap script that turns CapsLock into Ctrl, and both Ctrls (left and right) into CapsLock. That's the way I like it.

Everything works perfectly - for a while. Then, out of nowhere, but typically after the keyboard has been idle for a short while (maybe 30 seconds or a minute), the Num/Caps/Scroll Lock lights blink, and the keyboard essentially resets - losing the xset and xmodmap settings. Occasionally, the lights blink but my mods stick; usually, though, the keyboard resets. Also, sometimes, the keyboard just locks up, and I need to unplug/replug the USB connector. The mods are lost, in any event. I can run xset and xmodmap again, and get my mods back, but it's intolerable for this to happen perpetually while I'm trying to work.

I tried each mod individually, without the other. Same problem. I also tried a command "setxkbmap -option ctrl:swapcaps" that I found somewhere, in place of xmodmap. I like it less - it only turns left Ctrl, not both, into CapsLock. No matter; the problem remains. I even wondered if the wireless keyboard, sitting nearby, might somehow be pinging the computer once in a while, confusing it. So I turned it off, removed the battery, and even put it in another room! No difference; same problem.

Am I expecting too much for a modern computer to accept an 8-year-old keyboard with an adapter, and a couple of simple modifications? What gets me is that everything WORKS - for a while! It's as if something - the OS, perhaps, or the computer hardware, or even something in the adapter or the keyboard itself - is triggering a reset occasionally, instead of just leaving things alone.

---

