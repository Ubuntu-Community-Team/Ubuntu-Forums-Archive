---
title: "HP Envy HD4000/7670m graphics issues (13.04)"
date: 2013-04-27
forum: Hardware
---

### Post by idrum4316 on 2013-04-27
I have an HP laptop with hybrid graphics that I can't seem to get working right. If anyone can help me out, I'd appreciate it.

Here are the specs:
HP Envy 6t-1100
CPU - i5 3317u with Intel HD 4000 integrated graphics
GPU - AMD Radeon HD 7670m (2GB)
OS - Ubuntu 13.04 64 bit

Here's what I've tried:
1.) Using open source drivers installed by default. The battery life is about 2 hours (I got at least 6 with Windows), the temperature would get up to 200 degrees at idle, and I couldn't activate the 7670m even though it was powered. I was able to get about 3 hours of life and lower temperatures if I ran "[COLOR=#333333][FONT=UbuntuMono]echo OFF > /sys/kernel/debug/vgaswitcheroo/switch[/FONT][/COLOR]", but that kind of defeats the purpose of buying a laptop with discrete graphics, right?

2.) Using the fglrx drivers available in the Ubuntu Software Center. When I log in, I get a wallpaper and nothing else. If I use crtl+alt+t I can get a terminal and launch the software center to reinstall the open source drivers, but I don't get Unity back. Still just a wallpaper and nothing else.

If any other information would be helpful, let me know and I'll post it. I had these same issues on 12.10, and I was hoping 13.04 would solve them, but I guess not.

Update: I tried to follow the guide here [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) and when I got to the step where you run "aticonfig --initial -f", the output I got was "aticonfig: No supported adapters detected."

---

### Post by d!ck-t on 2013-04-27
Hybrid graphics in Linux are difficult. For Nvidia, you need to use Bumblebee to switch off or use the dedicated card. There might be something similar for AMD hybrid graphics.

---

### Post by idrum4316 on 2013-04-28
[FONT=arial]I think AMD's Catalyst is the equivalent to Bumblebee. I just tried the latest stable version (13.4) from the AMD site, and it appeared to build and install fine, but that seems to have made things worse. The desktop manager didn't want to start. It wanted me to start in low graphics mode or something and then gave me a shell interface. I'd really like to get this working. I installed openbox hoping at least I'd have something, but that didn't really do anything... [/FONT][FONT=arial]I'll re-install Ubuntu and start over.[/FONT][FONT=arial]

Update: I re-installed and as root, I ran ```
service lightdm stop
``` and then ```
[COLOR=#333333]echo DIS > /sys/kernel/debug/vgaswitcheroo/switch[/COLOR]
``` and I got a black screen, using the default open source driver. Does that mean the open source drive doesn't work at all?
[/FONT]

---

### Post by v00d0 on 2013-06-03
I'm also interested in to solve this. I have the exactly same situation and i did the same things. 
- I installed amd catalyast then everything in the UI disapperead; 
- I've a supernova instead of a PC, around 70 degree in IDLE, i uninstalled Unity and installed Gnome ( same thing, it's always a supernova).
- I tried do turn off ati card from bios, but advance features are locked in EFI Bios so i can't get it off. 


I subscribe to this hoping someone have a solution.

---

### Post by Mark Phelps on 2013-06-03
Hybrid and Switchable graphics are flavors of the same serious problem in Linux.  The PC vendors with these devices include drivers special-made for these devices; downloading drivers from Intel or AMD sited generally do not work.  Further reading: [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics")

---

