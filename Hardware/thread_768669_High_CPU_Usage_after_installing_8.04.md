---
title: "High CPU Usage after installing 8.04"
date: 2008-04-26
forum: Hardware
---

### Post by urutoraman on 2008-04-26
I have a HP ZD7000 laptop with Intel Pentium 4 CPU, Nvidia GeForce Go 5600 and a Broadcom Wireless network card.

On Ubuntu 7.10 (Gutsy) everything was working perfectly fine: wireless, nvidia, compiz, etc.

I wanted to try the new Heron (8.04) so I proceeded to erase the partition where I had Gutsy installed to do a FULL clean install.

The installation went really smooth, but slower than Gutsy. Everything worked like a charm.  Even wireless worked without any trouble (had to connect to wired network and get the b43-fwcutter).

Proceeded to install the restricted Nvidia drivers and Compiz Manager. Worked like a charm too!!

Here comes the trouble, for some reason on Hardy the CPU usage is Extremely High when the machine is IDLE.  I got PowerTop and it always list at the top b43legacy and nvidia as the top processes that wake up the CPU.  On Windows XP the ACPI Temperature reports only 40C but with the newly installed Hardy Heron it goes all the way up to 65C+ depending on what I'm running.  The CPU fan blows really hard when running 8.04 (It was cool and quite on Gutsy 7.10).

Now I'm afraid to use my Linux partition because I can fry the CPU or motherboard.

Is anybody experiencing the same High CPU Issues?  Is there a way to solve this?

:confused:

---

### Post by phoenix5002 on 2008-04-26
I experienced the same problem as you after installing Hardy.
However, luckily, mine only happened once.  I ran an application and it crashed, a few seconds after it crashed I experienced the exact same problem as you, CPU was running at 100% but when I checked which application was using cpu all of them looked normal nothing was using more that 15% cpu so I didn't know where it was coming from and it just stayed at 100%.  I couldn't even turn my laptop off had to press the power button.

hopefully that could help you somehow, maybe an application running at startup crashes for you and your experiencing the same thing as me.  Maybe someone else here can tell you how to monitor for that sort of thing.
NOTE: restarting X did not solve the problem for me, it was still at 100% CPU.  I will test this again later for you to confirm if it was the application crash or something else.

---

### Post by la3875 on 2008-04-26
I noted the same issue on my laptop. Hardy was using 15% of CPU and memory just idling. In addition it broke wireless and I was unable to resolve. Being impatient, I'm back to gutsy until Hardy is more stable. 

Congratulations on the desktop effects. I couldn't get them enabled no matter what I tried. Again... Gutsy is good right out of the box for me.

---

### Post by Matthew T. on 2008-04-26
I'm having a similar issue since I installed 8.04 last night. My machine has an AMD Athalon 64x2 4200 Plus processor with 2 gigs of RAM. CPU 1 is barely active while CPU 2 hovers around 40% usage while the machine is idling. The gnome system monitor has 5% CPU usage. No other process is actively running.

After turning off tracker, the tracker applet, disabling the nvidia drivers, and uninstalling compiz, I found out it's the gnome system monitor. It's using a lot more than 5-11% it thinks it is, as per the top command.

---

### Post by urutoraman on 2008-04-28
Found the solution. I am a happy camper now
Just followed the instructions in this link :KS [http://howtoforge.com/cpu_frequency_scaling_ubuntu]("http://howtoforge.com/cpu_frequency_scaling_ubuntu")

---

### Post by Alessandro Allegri on 2008-05-04
Well, it's not working for me.
Zd7000, P4 3.4GHz, Nvidia GeForce something.
Upgraded from Gutsy to Hardy (Hasty?) a week ago. Everything was working ok until...
Last night I passed to battery power for a while, and in 10 mins Hardy sucked my (already oldish) battery out in Joule effect.
Plugged in power supply again, but the heating wouldn't go off (around 60°C, while Gutsy would dwell in the 40's).
So I looked for a solution: uninstalled powernowd, installed cpufrequtils, modprobed p4_something (as in the link above), added the same module to the modules file, chose a governor (ondemand).
Heating still on, no sign of improving.
I read that the video drivers might be the cause, so I downloaded envyng, uninstalled the former drivers and installed the new ones. Now I am in the fantastic predicament of having Hardy unpredictably cut off my pc (no switching off procedure, just plain and brutal cut off) at leisure. Uninstalled nvidia through envyng, same thing.
Bonus: heating still on.
Now it's either I find a quick and steady solution, or I'll have to say goodbye to Hardy and find a way back to old faithful Gutsy... 
Any ideas?
Thanks,
A.

---

