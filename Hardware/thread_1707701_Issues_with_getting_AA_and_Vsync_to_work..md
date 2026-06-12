---
title: "Issues with getting AA and Vsync to work."
date: 2011-03-15
forum: Hardware
---

### Post by khaosdvorak on 2011-03-15
Hi everyone, I'm fairly new to Ubuntu and need some help.

Last night I got Fallout: New Vegas up and running fairly well with Wine 1.2.2 (stable) and am running it 25+ fps max settings. However, I cannot get Anti aliasing or v sync to work in game. I check V sync with no effect, and it blanks out the option to change AA in the launcher. 

I have tried to change AA to be force with Nvidia X server settings, and even after restart I still cannot enable AA or get V sync to work.

My hardware is as follows: 
Asus G51VX-RX05 Laptop
Intel Core 2 Duo 2.0 GHz
4 GB  DDR2 RAM
Nvidia Geforce GTX 260M 1GB

---

### Post by Artemis3 on 2011-03-16
Force Sync to VBlank in the opengl settings, and launch the game without closing nvidia settings (minimize).

Else launch the game passing the VSYNC variable, something like this:
In a terminal, cd into the game folder, then:

__GL_SYNC_TO_VBLANK=1 wine gamewhatever.exe

This works fullscreen only, not windowed.

---

