---
title: "3D doesn't work for some games (intel)"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by pumaman_scotland on 2007-06-16
Hi,

I have an "Intel(R) 945GM 20061017 x86/MMX/SSE2" onboard graphics card on my laptop. 3D graphics are working find with some applications, but not with others:

Works:
crack-attack
blender

Not works:
oolite
defcon 
TA spring

Games that don't work are running _really_ slow, and the CPU usage goes to full.

I have tried both the default i810 driver and the new intel driver. I have also tried disabling the composite extension.

glxgears gives me >800 FPS. I also tried SDLgears, which gave similar values.

I am using Feisty Fawn.

Any ideas? Any other opengl or SDL games you think I should try?

thanks
David

---

### Post by pseudonatural on 2007-06-17
I am having the same problems.  Every game I've tried (Oolite, Vega Strike, a few others) runs fairly choppy.  glxgears gives me close to 1,000 FPS and beryl runs great.  I have an Intel 945.

I've used both the i810 and the Intel driver.  My only guess is that the driver doesn't support some function that these games are trying to call, or it is implemented very poorly and results in slow down.  Anyone have any idea what it could be?  

I'm curious to hear if anyone has had any success gaming with this graphics chipset in Ubuntu, because I can't seem to think of what to do to improve this just short of getting a new computer/laptop so that I can get a video card with more support under Linux on it (NVIDIA, basically).

---

### Post by adamorjames on 2007-06-17
Same problem for me. I'm using Intel 945GM on a Toshiba Laptop A105 S4284. Oh and related to running slow, some games take a bit of messing with (pressing buttons, etc) before they will go from a black screen to a working screen.

---

### Post by betchern0t on 2008-01-17
Hi,
    I have the same problem. Looks like the oolite developers are focused elsewhere so it may take some time. The biggest issue with this behaviour is docking. What I have done as a work around is enabled the docking computer.

1) open oolite and save a game - F2

2) navigate to the oolite-saves directory in your home directory.

3) open the save file in an editor like gedit. find:

<key>has_docking_computer</key>
	<false/>

4) change this to:

<key>has_docking_computer</key>
	<true/>

and save the file.

5) restart oolite and load the saved game

6) when you approach a space state you will see an "S" bottom left corner.

to activate the computer press <shift>-C. If that doesn't work and you get a message saying the station can't do computer docking, use <shift>-D

hope this helps

Paul

---

### Post by statto1977 on 2008-02-22
I've just installed Oolite on my laptop (HP530 1.83Ghz Dual Core with 2GB RAM), and the screen comes up, I get the nice rotating ship/space station, and I can select all the options via the F keys. As soon as I leave the space station the graphics drop to one frame every couple of seconds and none of the keys respond. Any ideas, as it's got me completely stumped?

UPDATE: Turns out that it's working, just incredibly slowly. I've dropped the screen resolution down and reduced the detail but all to no avail. :(

---

