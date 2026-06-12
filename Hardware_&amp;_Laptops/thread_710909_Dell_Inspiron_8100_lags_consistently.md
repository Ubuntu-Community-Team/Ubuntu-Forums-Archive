---
title: "Dell Inspiron 8100 lags consistently"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by heroes_on_a_half_shell on 2008-02-29
this seems to be a fairly common problem on dell inspirons. and yes, i really have looked around and didn't find anything on the forums or elsewhere that i could actually understand and could fix my current issue.  mine is an 8100 with a 1Ghz P3 - 512mb ram - new hd - nvidia geforce2go. right after install, the laptop would lag anytime a load was placed on the processor. i noticed this due to the fact that audio playback would skip every time a new song was queued or a even just clicking a link in a browser. so, i disabled powernowd and installed cpufreq to get back my cpu scaling. using a desklet to keep an eye on the scaling - it seems to be working fine and without lagging due to load.

which is exactly my new problem. since i got rid of the load induced lag, i now notice a tick in the mouse every 5 secs. i whipped out the watch on this one - and its almost exactly 5 sec intervals. it does this with the touchpad, with an external usb mouse, and even the crappy little mouse button in the middle of the keyboard. it does it with apps running (100% cpu usage), and without apps running (1-2% cpu usage). it's always there, and it's very consistent. however, it mainly seems to effect the mouse. apps don't seem to slow down at all, and even audio playback is fine. however, the tick is also noticeable in 3d rendering situations such as playing tremulous or watching that uber cool screensaver with the random engine configurations running cycles. ok, so maybe it's not just the mouse.

well, thats all the info i've got. if you want to help me and need anything else, please let me know how to get it, cuz i'm still a wee bit new here.

thanks in advance for any help-- these forums have been awesome

---

### Post by heroes_on_a_half_shell on 2008-03-11
well, this thread got a lot of views but no replies so i had to figure it out for myself

problem = gkrellm

i was using gkrellm to monitor my temps and fan speeds.  it was always running so the tick was always there.  i discovered this after i installed fluxbox, kde, and xfce4 to rule out desktop environments as the problem.  anyone thinking about multiple desktop sessions should do it - it's interesting.

however, if someone reads this and knows the answer to my new problem i would greatly appreciate them saving me the research.

now that i stopped using gkrellm, i am using i8kmon to control my fan speeds w/ a gnome applet to monitor the temps and fan status.  however, i have these 3 shiny new desktop environments and i just don't know how to install i8kmon as a daemon for them.  in gnome i used the preferences -> sys admin -> sessions menu to create a start up command.  what i want to do now is the same for kde, fluxbox, and xfce4. 

if you know the process (or the locale of a how to) for installing daemons in these three off the top of your head, plz let me know.  also,  it would be great to know if there is some way to use a gnome applet in other environments.

thanks

---

