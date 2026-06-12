---
title: "resume from suspend kills wireless"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by h2gofast on 2006-05-31
running panasonic cf-71 p3 600, netgear pcmcia wireless card.
boots up and connects to network just fine.  
after resuming from suspend, no connection.  If I pop the card out, the laptop locks up.
If I pop the card out before suspending, it locks up when I put it back in.

After bootup but before suspend I can pop the card out and in without a hitch.
Any suggestions are welcome.
cheers, 
h2.

---

### Post by perce on 2006-05-31
Have you checked if the modules for the card are removed when you remove the card? if this does not happen, have you tried removing the modules manually with
modprobe -r?

---

### Post by h2gofast on 2006-05-31
thanks for the reply
```
lsmod | grep orinoco
orinoco_cs             17928  1
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
pcmcia                 40508  2 hostap_cs,orinoco_cs

```

after ejecting the card....

```
[4300212.993000] pccard: card ejected from slot 0
root@z1900:/home/h2# lsmod | grep orinoco
orinoco_cs             17928  0
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
pcmcia                 40508  2 hostap_cs,orinoco_cs

root@z1900:/home/h2# modprobe -r orinoco
FATAL: Module orinoco is in use.

same with modprobe -r hermes


```

not sure what I need to do next.... 
cheers h2

---

### Post by perce on 2006-06-01
[QUOTE=h2gofast]
after ejecting the card....

```
[4300212.993000] pccard: card ejected from slot 0
root@z1900:/home/h2# lsmod | grep orinoco
orinoco_cs             17928  0
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
pcmcia                 40508  2 hostap_cs,orinoco_cs

root@z1900:/home/h2# modprobe -r orinoco
FATAL: Module orinoco is in use.

same with modprobe -r hermes


```

not sure what I need to do next.... 
cheers h2[/QUOTE]

Try, in the order, 
modprobe -r orinoco_cs
modprobe -r orinoco
modprobe -r hermes

and then try to suspend

---

### Post by h2gofast on 2006-06-01
```
root@z1900:/home/h2# modprobe -r orinoco_cs
FATAL: Module orinoco_cs is in use.


pccard: card ejected from slot 0
root@z1900:/home/h2# modprobe -r orinoco_cs
root@z1900:/home/h2# modprobe -r orinoco
root@z1900:/home/h2# modprobe -r hermes


```
after suspend I tried to pop the card back in and it locked up, i.e. screen froze and no key or touchpad response.  

I should add that hibernate seems to work.  

Anyway thanks for the suggestion.

---

### Post by joske on 2006-06-02
Do you use NetworkManager? It's a known issue. Just disable/enable networking in the applet. 

See malone: #40125

---

### Post by h2gofast on 2006-06-02
thanks, but is there a way to configure it to do this automagically when I want to suspend.  
Pulling up another gui, typing in my password, disabling networking, hitting suspend, and then pulling up the gui when I resume is a lot.  
I don't mind the exercise, but I'll probably stick to hibernate for now.  Coming back from hibernate takes longer, but requires less interaction.

Is anyone else having trouble with suspend hanging the laptop over a network connection?

---

### Post by anllogui on 2006-06-02
Yes, I have had this problem in ubuntu for a long. 
I have a conceptronic card. I found the solution, but I forgot it, sorry. It was  modifying the script that is executed when the system is suspending, inserting the lines "modprobe -r", and reloading these modules when the system comes up. I cannot find it anymore.

---

### Post by Jope on 2007-04-23
I started experiencing the same problem once I upgraded from 6.10 to 7.04 .. I even used the graphical updater, because it was supposed to not break things.

Oh well, after lamenting about it for a while and basically shelving the laptop for a few days because of this annoyance, I decided to finally fix the problem. :-D

I checked the suspend / resume scripts and what order they did things.. In /etc/acpi/suspend.d, there's the script that pulls down the interfaces. The first thing it does is "eject" the pc card, then it goes on to kill dhcp clients and then it pulls the actual network interfaces down.

Ok, I started to play around with the order of disabling the wireless interface in the shell, trying out different combinations of stuff, like just taking the card out without ifdowning first, and so on.

When the card gets ejected, the pcmcia utilities should take down the interface and everything's ok, but it seems something has broken there during the upgrade. Now if the card is just removed, everything hangs when the pcmcia scripts try to bring up the interface again.

I couldn't be bothered to figure out how the pcmcia stuff works (what scripts are called, etc) so I just moved the pccardctl eject line to be the last thing that the 55-down-interfaces.sh script runs. Thus the interface gets taken down cleanly and only then the card is stopped, avoiding the hang when it is reinserted and trying to ifup the interface that's already "up" in some limbo state.

Now my machine hibernates nicely and wireless is available after hibernation.

Maybe one day I'm sufficiently bored to check out the pcmcia side of things, but I'm running Ubuntu for the sole reason that after a day of looking at solaris and hp-ux, I couldn't care less for tweaking things that should just work. ;-)

---

