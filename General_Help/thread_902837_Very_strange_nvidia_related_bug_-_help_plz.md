---
title: "Very strange nvidia related bug - help plz"
date: 2008-08-27
forum: General Help
---

### Post by itemirus on 2008-08-27
I am running ubuntu hardy on amd 64 3200,2 Gb ddr ram, Asrock motherboard with integrated Nvidia 6100 card.

I was previously running this system with a pci express Sapphire GTO Ati card, and everything was fine.

I removed the card because the fan was very noisy, formatted and reinstalled ubuntu.

I have correctly downloaded and installed the latest nvidia drivers for the card and xorg.conf is configured ok, or so it seems.

Now to the bug.

Every 10 or 30 seconds [varies], the system seems to lock up completely as if there was 100% cpu use, but the mouse pointer moves flawlessy, yet i cant write, open menus, move windows, etc, everything else besides the pointer is standing still. Sometimes another strange thing happens: the screen locks and turns grey / i can still see the desktop but everything is locked up and in grey scale. After a few seconds it unlocks and everything is back to work.

I am quite sure this is related to the nvidia chipset but i dont want to reinstall the ati card because it makes so much noise and i have no way to slow down the fan [no  ati tools for linux].

Any clues? thanks

---

### Post by Comzee on 2008-08-27
Where did you get the nvidia drivers, from their site or did you use a program like envy. I've tried using nvidia's drivers right off their site and they didn't work so great.

---

### Post by rune0077 on 2008-08-27
> **itemirus said:**
> I am running ubuntu hardy on amd 64 3200,2 Gb ddr ram, Asrock motherboard with integrated Nvidia 6100 card.

I was previously running this system with a pci express Sapphire GTO Ati card, and everything was fine.

I removed the card because the fan was very noisy, formatted and reinstalled ubuntu.

I have correctly downloaded and installed the latest nvidia drivers for the card and xorg.conf is configured ok, or so it seems.

Now to the bug.

Every 10 or 30 seconds [varies], the system seems to lock up completely as if there was 100% cpu use, but the mouse pointer moves flawlessy, yet i cant write, open menus, move windows, etc, everything else besides the pointer is standing still. Sometimes another strange thing happens: the screen locks and turns grey / i can still see the desktop but everything is locked up and in grey scale. After a few seconds it unlocks and everything is back to work.

I am quite sure this is related to the nvidia chipset but i dont want to reinstall the ati card because it makes so much noise and i have no way to slow down the fan [no  ati tools for linux].

Any clues? thanks

About the turning grey part: if it's just the windows turning grey (and not the entire desktop), then that's normal Compiz behaviour. When a window stops responding, compiz will turn it grey to alert you to it. That typically means your CPU is doing something else, and once it's done with that, it returns attention to the window (and hence it stops being grey).

All in all, this doesn't sound very much like it's a driver problem, more something with the CPU. Try adding the monitor/sensor applet to your panel, so you can keep track on CPU-load (right click the panel, select "add to panel" and find the hardware sensors). Watch if they are doing something intensive when these things happens.

---

### Post by itemirus on 2008-08-27
> **Comzee said:**
> Where did you get the nvidia drivers, from their site or did you use a program like envy. I've tried using nvidia's drivers right off their site and they didn't work so great.

I downloaded the latest drivers from their site and installed from terminal after exiting X.

[QUOTE=Rune0077]About the turning grey part: if it's just the windows turning grey (and not the entire desktop), then that's normal Compiz behaviour. When a window stops responding, compiz will turn it grey to alert you to it. That typically means your CPU is doing something else, and once it's done with that, it returns attention to the window (and hence it stops being grey).

All in all, this doesn't sound very much like it's a driver problem, more something with the CPU. Try adding the monitor/sensor applet to your panel, so you can keep track on CPU-load (right click the panel, select "add to panel" and find the hardware sensors). Watch if they are doing something intensive when these things happens.[/QUOTE]

Thanks for clarifying over the grey thing / i guess it-s compiz then.
I guess it is a driver problem, because if i instruct X to switch to Vesa the problem is gone. I-ll try monitoring the cpu load.

---

### Post by itemirus on 2008-08-27
I-m watching the system monitor...it locks up as well and when it resumes working it plots a 100% cpu load during lock up time. Damn this is so annoying...Is there a log where i can check what process or service is the resource hog?
Thanks for any help / i am logging off now because i live in Europe and am going to sleep now....

---

### Post by rune0077 on 2008-08-27
You can use the normal system-monitor, or you can download htop (from the repo), which will give you a much better and more detailed readout. But if these locks up as well, that might not to much good.

Which Ubuntu are you using? In Gutsy I had high CPU-usage problems with Tracker, but they seem to have gone with Hardy. If you have Tracker running, try to turn it off and see if that makes a difference.

---

### Post by itemirus on 2008-08-28
I am running Ubuntu hardy 32bit
Htop shows that the process sucking up all of the cpu power is usr/bin/X

---

### Post by itemirus on 2008-08-28
Now i edited xorg.conf and using Vesa / everything works fine but my screen resolution is 800x600 now...

It is clear the problem is in the nvidia drivers / Is there another solution to get this geforce 6100 runnning without problems?

---

