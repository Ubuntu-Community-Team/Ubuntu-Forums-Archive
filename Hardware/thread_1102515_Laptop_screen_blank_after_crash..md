---
title: "Laptop screen blank after crash."
date: 2009-03-21
forum: Hardware
---

### Post by killpotts on 2009-03-21
Hey everyone, I have a big problem and I am hoping for some possible solution. 

I was playing Guild wars for a while and all of the sudden the screen freaked out on me. It did something that resembled what an old regular Nintendo would look like when it crashed - gray and colored lines across the screen. Nothing would respond, so I had to hard reset IE push the power button.  

Now, My screen will not turn on when I boot up. No bios, no nothing. I can tell that the CPU itself is booting up, but the screen remains off until it boots up to Ubuntu. When it boots to ubuntu I can hear the drumroll music it makes at startup, and the screen "sort of" turns on. What I mean by sort of turning on is that the screen lights up and shows it has power to it, but still remains black/blank as opposed to off/dead. 

FYI I know this is likely a dead graphics card. Problem is if it is a dead graphics card I am basically screwed as this particular make/model of graphics card has it built into the motherboard making it cost too much to replace, and the laptop is out of warranty. So I am looking to see if anyone knows anything that may be a possible alternative solution ( if there is one ).

My specs relevant to this issue are:

-Gateway model M680
[http://forum.notebookreview.com/showthread.php?t=18208](http://forum.notebookreview.com/showthread.php?t=18208)
-256Mb Nvidia Go 6800 graphics card
-Ubuntu 8.10
-120 GB IDE hd

---

### Post by robojiannis on 2009-03-21
I have exactly the same problem, after forgetting to disable my external monitor.

Now I can work only with an external monitor connected to the laptop. If you find any solution I would highly appreciate it!

---

### Post by killpotts on 2009-03-21
Your just gave me an idea since I never tried an external monitor before. It would be a lot better then nothing ! So I did and managed to get it so my bios shows booting on my external monitor...but it still goes back to black/blank as soon as ubuntu loads and the monitor said "Video mode not supported". I suspected that this is because I have my resolution set to 1680x1050 and the monitor I plugged it into only supports 4:3 ( which explains why it displays my bios a bit weird, with skipped lines and such ) So I went to the grub menu during bootup and tried to use xrandr to change my resolution, but it wouldn't let me.


See, I wouldn't mind having to use an external monitor as long as it works. This laptop got pretty beat up during college so I never move it from its location and basically use it as a desktop already. Any ideas as to how to just get my desktop back would be great.

---

### Post by killpotts on 2009-03-21
I just tried booting from the live CD, and it looked really quite bizarre. It does not show the "Ubuntu" Graphic and instead the live CD displays as a blue dos-looking menu. I selected to boot from CD without changes and it got to the desktop ( The live CD desktop ) but looks really weird. I can move my mouse around, and the default background shows with a few graphical bugs, but none of the toolbars come up and my keyboard becomes unresponsive. So I basically can't do anything in it.

---

### Post by killpotts on 2009-03-22
Just tried Aircan cleaning with little results, here are some pictures from the external monitor:

Here is the bios screen: Note the letters randomly spaced incorrectly and random anomalies like "Securioo" instead of "Security"

[img]http://img238.imageshack.us/img238/2751/1000302.jpg[/img]

Here is What booting from the ubuntu live CD looks like. Note random anomalies:

[img]http://img511.imageshack.us/img511/8338/1000299.jpg[/img]

Grub Recovery menu:

[img]http://img410.imageshack.us/img410/3661/1000306.jpg[/img]

Xrandr error ( note the anomalous "r" :

[img]http://img21.imageshack.us/img21/600/1000305y.jpg[/img]

Loading with random strikes through letters. Some letters randomly missing:

[img]http://img242.imageshack.us/img242/6847/1000304.jpg[/img]

More Grub Recovery menu

[img]http://img217.imageshack.us/img217/3608/1000303.jpg[/img]



And the screen still goes blank when I attempt to boot. 

So, is this something that is possible to fix ? :P

---

### Post by robojiannis on 2009-03-23
I contacted my laptop manufacturer. They are 100% certain that it is a hardware problem. 
I even implied that I might have changed the default installation (OS, Software, etc) and they said it certainly is not a software problem.

So that's that. Hope you're still in warranty :)

---

