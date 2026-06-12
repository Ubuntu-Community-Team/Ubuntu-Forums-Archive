---
title: "[SOLVED] Installing 7.10 has bricked my ps3..please help"
date: 2008-09-17
forum: General Help
---

### Post by jonnywombat on 2008-09-17
Ok I followed a tutorial of how to install Ubuntu 7.10 (the ps3 spesific version) onto my ps3..

All seemed to go ok, right up until the ps3 spat out the ubuntu cd and propmted me to press enter to continue..


I did so but ps3 did nothing.. left it for 1 hour, no change so pulled the plug.

Now the PS3 will boot into ubuntu just fine, but will not shut down properly, it starts the process, I get various lines of text and the screen goes blank... but no power down.. I have to pull the plug.

Also I cannot boot to ps3... press tab when kboot loads, select old, but just get an error...

Please help.. if only to restore my ps3 as a ps3..not to bother about having ubuntu installed at the moment:(

---

### Post by -Zeus- on 2008-09-17
i don't think you'll find help on that here, although you're welcome to ask.  You might want to ask on a ubuntu ps3 specific forum?

---

### Post by jonnywombat on 2008-09-17
Solved... it myself anyway..

---

### Post by -Zeus- on 2008-09-17
could you mark it solved and report how you fixed it?

---

### Post by Jose Catre-Vandis on 2008-09-17
Advice from LinuxFormat magazine:

To return to the original OS (PS3)

Turn off PS3
Then turn it back on, but hold down the power on button (the one with the red light) for @ 5 seconds until you hear a beep.
This will reset the PS3 and start the XMB

---

### Post by jonnywombat on 2008-09-17
> **-Zeus- said:**
> could you mark it solved 

Had done this as soon as it was

> **-Zeus- said:**
> report on how you fixed it

See above

---

### Post by jonian_g on 2008-09-17
You can also boot back to the ps3 by typing on the kboot prompt:
```
boot-game-os
```
and it will make ps3 the default.
Or while you are inside ubuntu open a terminal and type:
```
sudo boot-game-os
```
Or create a launcher on the desktop or panel with the above code.

After ps3 firmware upgrade at v2.0 and above compatibility is broken for kernels earlier than 2.6.23. Ubuntu 7.10 uses kernel 2.6.22, so compatibility is broken (doesn't shutdown properly, no working wireless). When ubuntu hangs on shutdown don't pull the plug just keep the power button pressed until it beeps twice.

My advise is to wait for Ubuntu 8.10 final version(30 Oct 2008 ) as it will use kernel 2.6.25 and it will be available for ps3 and it will work properly.

---

