---
title: "BIOS (and all other) displays are too big for screen"
date: 2010-11-19
forum: Hardware
---

### Post by Chocotacoi8 on 2010-11-19
I have a Dell Inspiron 8200 laptop. The video card is an NVIDIA GeForce2Go card. It's pretty old, but still works fine except for one unbelievably annoying problem. Basically, the computer thinks the laptop's physical screen is bigger than it actually is, which means that the display at all times (whether BIOS, XP splash screen, safe mode or desktop) extends too far by some amount (depending on the resolution size) off the edges of the screen to the right and to the bottom. So, for instance, the windows task bar can't be seen unless it's moved to the top of the screen. Similarly, the BIOS setup controls can't be seen because they're below the bottom edge of the screen.

I have tried everything I can think of from downloading new drivers (tho I don't think that would affect the BIOS anyway) to flashing the BIOS itself. Always the same display problem, right from the start when the computer is turned on.

The only thing that works (and the reason I'm posting in this forum) is if I boot into Ubuntu from a live CD. Then, magically, the display fits on the screen perfectly and everything can be seen, which is the only reason why I haven't stopped trying to find a solution. But this happens only when Ubuntu is running, from inside the Ubuntu OS. When I remove the live CD and restart, back to the same display problem right from the first BIOS loading screen.

So what is it about Ubuntu and a Live CD that makes everything work whereas the BIOS fails (and then of course Windows XP...but who's surprised there)?

Any ideas are welcome, I'm totally stumped!

---

### Post by amauk on 2010-11-19
Every computer component should have a unique identifier

In Linux, this is expressed as a vendorID, subvendorID, and a deviceID
(no idea how Windows does it)

The idea is that all hardware components in a system can be uniquely identified, so correct drivers can be loaded for the device (and where needed, firmware bugs in the hardware can be worked around in the OS - so called "quirks")

Chances are the laptop or graphics card manufacturer has altered the graphics chip, but failed to give it a unique ID, so some OS's may detect the component as something it's not, hence the wrong resolution.

The Linux kernel devs are very good at adding quirks to overcome hardware bugs

---

### Post by Chocotacoi8 on 2010-11-19
> **amauk said:**
> The Linux kernel devs are very good at adding quirks to overcome hardware bugs

So all I need is someone who is as smart as a Linux kernel dev to work their magic in windows....](*,)

But seriously, any suggestions? Is there any way to confirm a "quirk" is being used in Ubuntu, so I know that *this* is the issue?

---

### Post by amauk on 2010-11-19
Hmmm, sorry this is out of my depth

I have no idea if there's a way to determine whether a particular component has a kernel quirk associated with it

---

