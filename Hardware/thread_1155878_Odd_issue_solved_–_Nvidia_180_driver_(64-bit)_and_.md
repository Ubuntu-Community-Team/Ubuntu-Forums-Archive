---
title: "Odd issue solved – Nvidia 180 driver (64-bit) and GeForce 8400GS"
date: 2009-05-11
forum: Hardware
---

### Post by coffeecat on 2009-05-11
I've managed to solve this, but I'm posting in case it's useful to someone or someone has a better idea, or has any comments.

 Two machines both with AMD 64 X2 processors. Machine 1 running 64-bit Jaunty, machine 2 32-bit Jaunty. Identical Nvidia GeForce 8400GS cards fitted the other day in both, replacing 6200 and 7200 cards.

 I then noticed on machine 1 that the mouse cursor would 'catch' or hesitate. Also, a hesitation every so often when typing. If I held a key down in Open Office or the terminal, I would get a rapidly expanding line of characters, but with a pause regularly about every second. Ditto when scrolling through text using the arrow keys. Video playback also affected.

 Long story short – it took me a long time to track this one down – disabling the 180 nvidia driver and activating the 173 one in System > Administration > Hardware Drivers solves the issue. Now I have smooth cursor and keyboard control again. The question is: why is the nvidia driver causing a regular hiccup regularly every second? It's like a clock ticking, which I suppose it is, but what's going on?

 In brief:
 
Jaunty 32-bit + GeForce 8400GS + nvidia 180 driver – no problem.
 Jaunty 64-bit + GeForce 8400GS + nvidia 180 driver – PROBLEM.
 Jaunty 64-bit + GeForce 8400GS + nvidia 173 driver – no problem.

---

### Post by coffeecat on 2009-05-19
The plot thickens. I think I'm talking to myself but I'll post this because it might come up in a search for someone with the same problem.

The reason the 32-bit 180 driver worked fine on the other machine was not because it was 32-bit, but because it was on the other machine. Explanation - I installed 32-bit Jaunty on another partition on the machine running 64-bit Jaunty and got exactly the same issue with the 180 nvidia driver. So it's not the 64-bit version of the driver that's the problem - it's something to do with the particular machine. It's put into focus a whole load of odd things happening with this machine, and I believe it's down to some conflict somewhere between the onboard nvidia chipset, the nvidia PCIe card, xorg and the proprietary nvidia driver.

I've posted some of the other problems I've had [here]("http://ubuntuforums.org/showthread.php?t=1163870"), but for the record, the motherboard on the affected machine is an Abit AN-M2 with the nvidia GeForce 7025/nForce 630a chipset.

Of course, it could be a BIOS issue, but there's only been one BIOS revision after mine and the two fixed issues (according to the documentation) are quite specific and unrelated to my problems. So I'll never know if this is a BIOS issue since the board is now obsolete and Abit have withdrawn from the motherboard market.

---

