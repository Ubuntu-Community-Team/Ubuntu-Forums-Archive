---
title: "Suspend Option, Hibernation, and Laptop Lid"
date: 2009-11-13
forum: Hardware
---

### Post by Exüberance on 2009-11-13
I'm running Ubuntu 9.1, and I'm having a lot of trouble with standby/suspend and hibernation. There are 3 cases where different things happen:

1) Suspend by closing the laptop lid:
Laptop appears to go into standby fine. The light on the back of the laptop turns off, and the logs on the computer report that the standby was successfull. When I wake the computer, I have a black screen with a cursor. If I hit Ctrl+Alt+F1, to get to the full-screen terminal, I get an infinite loop of error reporting, and am unable to enter any commands. I have to hold down the power button to shut down.

2) Suspend by using the suspend option on the GUI
Laptop turns screen off... and back on... and off again... and back on... then goes off and stays off. The light on the back of the laptop is still on and stays on forever, however. When I wake the computer, it starts on the full screen terminal. Pressing Alt+F7 to get back to normal turns the monitor off and nothing except a hard restart will get it back on.

3) Hibernation
It kind of sort of half-almost works...ish. I select hibernation from the GUI. It goes to full-screen terminal, displays some errors, then the monitor turns off, but ALL lights are still on (including the light on the power button). I have to hold down the power button to turn off. When I restart it says "waking computer", and goes to a black screen with only a cursor (like when I resume from suspend), but when I hit Ctrl+Alt+F1, there's no error. Hitting Alt+F7 to go back, brings up a menu that normally appears when you lock the computer. Logging back it, the computer returns to it's previous state, but is slower and uses double the memory, with half of it in swap. (I assume it copies the memory to swap, gets it back, but then forgets to free that memory). Restarting normally returns the computer to normal.

This is [s]kind of[/s] really annoying since when I used Windows *shiver* standby worked and I used it all the time when moving between classes.  At least Ubuntu can actually start up in a decent time without hanging forever like some operating systems do *cough*Vista*cough*, but it's still longer than standby and it means I can't resume where I left off. 

If it's relevant, my computer is a HP Pavilion dv7 Notebook PC and my graphics card is GeForce 9200M GS

---

### Post by Exüberance on 2009-11-13
bump

---

### Post by elsealio on 2009-11-13
Have you installed the nVidia drivers?

I had the opposite problem, where I could suspend/hibernate fine, but could not resume my session. Once i installed the gpu driver (version 185) from System > Administration > Hardware Drivers it worked fine.

---

### Post by Exüberance on 2009-11-14
Yes, I have installed the latest Nvidia drivers. I had to when I first booted Linux because the display was spazing out, but the update fixed that. I haven't check to see if I can still use standby on Vista or not, but I imagine that it will still be fine.

---

