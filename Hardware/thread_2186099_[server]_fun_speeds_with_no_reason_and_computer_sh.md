---
title: "[server] fun speeds with no reason and computer shuts down blinking"
date: 2013-11-05
forum: Hardware
---

### Post by sowdust on 2013-11-05
Hi everyone,

I have a simple Ubuntu server on a Dell desktop serving only the basic services (web server,mail,ftp,ssh etc). Always up to date.
I've been experiencing two problems that I think could be linked:

First of all, sometimes the fan goes off speeding crazily with apparently no reason. If i check with htop, I see the CPU is used at 0% by all processes. Maybe some processes could be hidden?

Second, at very irregular intervals, the computer just turns off (doesn't shut down properly) and the front led start blinking orange. The strange thing is that the BIOS is set to restore the state of the system in case of power fault (ie. it turns automatically back on if the power goes out).

What could be causing this? I've been thinking for a long time of a security problem ([thread here]("http://ubuntuforums.org/showthread.php?t=2095018")) but couldn't find anything so far, so I'm thinking it could be a hardware problem or something to do with the power supply (the electricity infrastructure in my house is very old and sucks)

I'd appreciate any suggestion or comment.

thanks!


[edit] Just now, the computer went off. I had htop open on a terminal, so I'm attaching its screenshot. That --purge --config=/etc/denyhosts.conf looks suspicious to me.

And the led on the lan cable attachment keeps going on and off as if it were still exchanging info. the system seems completely off though!

---

### Post by Skaperen on 2013-11-05
My first suspicion would be the power supply.  They are the most common hardware failure point.

---

### Post by sowdust on 2013-11-05
thanks, Skaperen. now that I think of it though, the problem occured also in my old house, where the electric system was new.
So I'm thinking, maybe an internal power supply problem? also, could that be connected to the speeding fan?

---

### Post by varunendra on 2013-11-06
CPU fan going crazy and system shutting down for no reason sounds like a CPU overheating problem to me.

Usually happens in old desktops whose heatsink compound (the paste between the CPU and heatsink) has dried up (possibly creating air-gaps) or the heatsink is clogged with dust. But can also happen in new machines in case the heatsink has not been properly seated or is otherwise unable to dissipate the heat off the CPU.

If you are comfortable with doing this, I'd suggest to pull out the heatsink and replace its stock heatsink compound with a good quality one, then reseat it properly and see if it helps. Of course you can try "lmsensors" or a similar tool to verify the heat levels beforehand if you are sure your CPU area has the required sensors to report that.

As for blinking LED on the ethernet port, which one is blinking? Usually there are two LEDs, one remains steady (indicating the connection is established) and the other one blinks when there is traffic activity. If there is just one LED, you'll have to make sure which state means what. It could be just a "No or Faulty connection" indication.

---

### Post by sowdust on 2013-11-08
thank you varuendra. I have now put the case in a fresher place and it hasn't shown problems so far. If it happens again I'll just give him some of that toothpaste : )

---

### Post by varunendra on 2013-11-08
> **sowdust said:**
> thank you varuendra. I have now put the case in a fresher place and it hasn't shown problems so far. If it happens again **[COLOR="#FF0000"]I'll just give him some of that toothpaste[/COLOR]** : )

LOL !! :P

I remember having read a post somewhere where a user did just that (used toothpaste instead of heatsink compound, simply because he didn't know the difference). Fortunately, his CPU was under warranty, which soon came in handy. ;)

---

