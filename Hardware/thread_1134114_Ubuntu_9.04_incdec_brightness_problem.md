---
title: "Ubuntu 9.04 inc/dec brightness problem"
date: 2009-04-23
forum: Hardware
---

### Post by iulian on 2009-04-23
Hi,

I've upgraded today from 8.10 to 9.04 and I cannot increase screen brightness. Whenever I press ENTER, PAGE UP, PAGE DOWN, ARROW L, R, UP, DOWN, DEL screen brightness decreases. This happens every time I press the above mentioned keys, even if I'm in an editor.

It's very frustrating. Is there a way to make ubuntu not to listen those keys for those to inc/dec brightness.

I'm using an HP-Compaq 6730s laptop with ATI Radeon Mobile 3430.

If you have any idea please let me know.

---

### Post by iulian on 2009-04-23
If I run xev and try to check the key events raised by the key combination Fn+F7 (decrease brightness) and Fn+F8 (increase brightness) no event is raised. Just like these keys are not recognized. Any way to map these keys?

---

### Post by iulian on 2009-04-23
Seems like a System > Administration > System Testing has partially solved the problem: Fn+F8/F7 key combinations are not working but arrows, PG UP/DOWN and other keys that were wrong mapped are working now.

---

### Post by taiang on 2009-04-26
Hi there. I've been having the same sort of problem with laptop keyboard special keys not functioning properly (i.e. volume not increasing/decreasing, brightness keys not working, etc. etc.) I had similar issues on notebook of a few different manufacturers, running different distros, including Ubuntu 9.04 Jaunty and Fedora 10. Seems like our dev guys are having such a hard time keeping up with all those models and version numbers. oh well, if only we had more open standards, things would be simpler, and we'd be  bunch of happy users by now. Ok, on to the solution:

For the more technical-oriented, [_this page here_]("https://wiki.ubuntu.com/Hotkeys/Architecture") might point you in the right way, if you care to read it through attentively.

Here's a quick outline of what worked for me on Jaunty 9.04, based on the info from the URL above: 

WARNING: Potential for system damage may exist! Proceed with caution! *Backup any files before altering them!!*

> Under the folder **/usr/share/hal/fdi/information** there should be some folders, namely **10freedesktop/** and **20thirdparty/**, which contain several .fdi files inside them. These files are XML mappings having to do with your hardware and how it interacts with other stuff in your computer (e.g., the X server).

> looking at the **10freedesktop/** folder, you should see a lot of files named like *30-keymap-<manufacturer_name>.fdi* and *30-keymap-module-<manufacturer>.fdi*. These are important for us, for they define the mappings from hexadecimal kernel keycodes (like [*0x9c]*) into X server actions (like *0x86AudioRaiseVolume*).
 
> Based on that knowledge, we must accomplish two simple steps now: 1. discover the hexadecimal code for the keypress we are attempting to fix, and 2. Find the action inside the file which we were expecting to happen for that specific key combination, and alter its keycode.

> The first step can be handled by entering the command **sudo showkey -s,** and then typing the desired key combination and marking down the hexadecimal keycode that appears. Luckily, there will be a single one. If not, try to note which one varies when you press the immediately adjacent special keys, and mark that number down.

> Now we must find the X.org action which we want to fix inside the .fdi file (the file of the appropriate manufacturer for your notebook, in my case, 30-keymap-hp.fdi). The actions have pretty obvious names, so if you're trying to fix volume functions, a simple search for 'volume' inside the file should set you up. Once you find the correct action, alter its keycode mapping (e.g., the number before the action's name in "e068:brightnessup", for example) to the one we found earlier. Voila! 

From here I did a reboot to get everything working again, but I'm sure this isn't necessary, I just don't know exactly how to reload all the necessary modules and services.

Please, comment on the solution, and point out any technical mistakes/imprecisions, and other flaws that probably exist, as I'm just a helpless user trying to get things working for me. And sorry about the lengthy explanation, I feel this might be overly complicated for some (me included) so I tried to be as detailed as possible.

happy hacking,
taiang

---

