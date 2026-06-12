---
title: "need help Installing LOTRO"
date: 2008-08-11
forum: General Help
---

### Post by zaptear on 2008-08-11
i'm useing this guide to do it and here is ware i'm running in to a problem

LINUX
[edit] Getting that patch

(Not needed anymore. However, you'll need at least an up-to-date installer which you can grab off the trial download on the LOTRO homepage - Don't use the original install CD)
[edit] Installing Wine

1. Install Wine (follow the instructions on their webpage if you run into problems).
2. Edit the Wine registry and set the proper amount of video memory: HKEY_CURRENT_USER/Software/Wine/Direct3D/VideoMemorySize = < amount of video memory ie 256 > (LOTRO works fine for me without this step though)
3. Use the Wine config util and set the Windows version to Windows 2000.
[edit] Installing LOTRO

[COLOR="Red"]1. Use the fakeNET11.reg file (you can import it with Wine's Registry Editor).[/COLOR]
2. Install LOTRO. DO NOT USE THE DVD FOR THIS! Install a downloaded trial version.
3. Decide whether you'd like a nice graphical launcher (GUI) or a text-mode command line launcher. The GUI launcher is highly recommended.
GUI launcher:
1. Install Mono if you'd like the GUI launcher. If not, skip to setp 5.
2. Install the GUI launcher, following the instructions here.
3. Launch the GUI launcher and go to Tools->Options and make sure the Game Directory is properly set.
Typically, this is ~/.wine/drive_c/Program Files/Turbine/The Lord of the Rings Online.
Command line launcher:
1. If you'd rather prefer a command line launcher get it here.

step on that i highlighted in red i just dont understand what i  need to do here

---

### Post by zaptear on 2008-08-13
i'm useing ubuntu ver 8.04 and i have been trying to get LOTRO to install and run for 4 days now i have installed LOTROlinux buy adding deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) hardy main to muy repository list and updateded i have wine 1.0 installd and the lotro game as well

No i can't seem to find LOTROlinux files on my system. so i can start the game i dont know if i have missed a step or something i have been reading 
[http://lorebook.lotro.com/wiki/LOTRO...x_and_Mac_OS/X](http://lorebook.lotro.com/wiki/LOTRO...x_and_Mac_OS/X)
and
[http://www.lotrolinux.com/](http://www.lotrolinux.com/)

any help i would love thanks

---

### Post by zaptear on 2008-08-13
Bump

---

