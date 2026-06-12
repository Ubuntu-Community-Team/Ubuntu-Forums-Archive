---
title: "plants vs zombies in wine input not supported"
date: 2009-05-13
forum: Hardware
---

### Post by rmvalentine on 2009-05-13
when running plants vs zombies in wine my monitor displays a box that says "input not supported." behind this box the game is displayed perfectly. the box moves around, so the game is playable, but it's very distracting. any ideas?

oh, my monitor is an acer 17." model number al1716

---

### Post by coolen on 2009-05-16
I just ran into the same problem.

The resolution of the game is too low. You can try enabling 3D acceleration in the options menu, but I just got a black screen. If so, kill it and it should come back next time without it.

---

### Post by coolen on 2009-05-16
Alternatively, windowed mode seems to work just fine.

---

### Post by rmvalentine on 2009-05-16
i could not find a way to get it to work in full screen. instead i just had wine emulate a virtual desktop at 800x600 and ran it in a window. this isn't ideal but it's better than the bouncing input not supported box.

---

### Post by coolen on 2009-05-16
Did disabling fullscreen in-game have any effect? Worked perfectly for me.

Also, on a slightly happier note, when I played it on Windows, it took ages to load. I'd go watch a YouTube video or two waiting to start the game.

Under Wine, I'm playing within ten seconds. Linux gaming ++.

---

### Post by darkwalt on 2009-05-19
hey guys, I was having trouble with this in wine as well.  When I boot the game, it immediately starts in fullscreen mode, with only half of the game displaying on my monitor.  Any suggestions?

---

### Post by Bad_Byte on 2009-05-26
@darkwalt Go to run command or console window and type winecfg [enter] this will should bring up wine configuration, go to the applications tab and then click on "add appliaction" now find your PlantVsZombies.exe once that is done head over to the graphics tab, there under graphic settings you will find "emulate a virtual desktop" enable it and set a size you like, click on "OK" at the bottom. Now PvZ should work just fine, it did for me (wine 1.1.21 / nvidia 180.51 / kubuntu 8.04).

---

### Post by darkwalt on 2009-05-27
Yeah, tried that, and it did the same thing.  I tried taking a screenshot and it actually showed the screen displaying properly.  However, it shows it with the upper third of my monitor being the lower half, and it cuts out the center of the game.  

I'm running Wine 1.0.1, an nvidia geforce 6200 and Jaunty.

---

### Post by JGJones on 2009-05-28
The first time the game starts it'll be in fullscreen mode - which does cause issues (ie very slow or show part of screen).

Switching to a windowed mode solves this and work very well under wine with no tweaking needed - simply just start the game - and while in full screen mode (ie you see the PopCap logo) press Alt-Enter to switch to a windowed mode and Bob's your uncle.

Hope that works for you.

---

### Post by batwingnz on 2009-06-08
gidday, running under wine via steam on msi u100+, previously had it working full screen but switched to windowed. now it hangs before even popcap logo is displayed and cannot switch to full screen again using alt+enter.

does anyone know of launch options that would force it back to full screen?

---

### Post by H2SO_four on 2009-06-25
i was having issues as well, am running in windowed mode and its great!

---

### Post by Seraphim x on 2009-11-06
If you do not want to use the emulated desktop you can follow these instructions to set Plants vs. Zombies to open without fullscreen and without the emulated desktop

1. browse to ~/.wine/drive_c/program files/plants vs. zombies
2. open drm.xml with gedit (or similar text editor)
3. enter the following line below the "CheckActivity" line
<Boolean id="Fullscreen">false</Boolean>
4. now save the file and Voila!

---

### Post by Ninja duck on 2010-01-15
I have been having the same problem while using wine (input not supported) but with another program (halo) but all i have is a blank screen with the monitor's error message. I have tried it with wine configured to open in a desktop but nothing different happens.

UPDATE: never mind, it works now. I don't know what changed but it does.

---

