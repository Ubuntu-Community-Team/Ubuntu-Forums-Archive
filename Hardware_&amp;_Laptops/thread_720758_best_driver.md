---
title: "best driver?"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by phoenix5002 on 2008-03-10
What would you recommend is the best video driver for my card?
I am on a laptop and have an ati "Radeon IGP 345M" video card.  The original drivers Ubuntu gave me worked good,  When I updated to ati's official linux mobility radeon drivers now I have no direct rendering.  So something needs to be done about this.  Also, I don't think I can use fglrx, because someone said this card isn't supported and also because I tried it and I get errors when the Xserver tries to initialize.

I wouldn't mind reverting back to the same drivers Ubuntu 7.10 gave me originally, but I don't know how.  So if someone knows how I could, or knows of any better, maybe third party(like Omega drivers or something), drivers I can get that work with this card I would be most grateful.
I ask because the most up to date drivers aren't always the best for certain cards.
Also, I can't edit any video options, some people said there should be an ATI tray but I don't have one, and I can't open ATI Catalyst Control Center either.  Is there anyway to change graphics settings such as texture quality and mipmapping from the command line, or some other app I can get to manage this?

---

### Post by Rocket2DMn on 2008-03-10
Let's try purging the fglrx driver, then autoconfiguring X which should hopefully pick up your original settings.
```
sudo apt-get remove --purge xorg-driver-fglrx
```
followed by
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.

If you have any problem, post your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

---

### Post by phoenix5002 on 2008-03-10
Thanks for the quick reply rocket :)

I got it working now, "direct rendering: Yes"

While I got this thread running I might as well ask this other question I have.  So the driver I currently have again is the default Open Source driver Ubuntu gave me upon install.  I don't have a Catalyst Control Center or an ATI control panel or anything.

Would it be possible for me to edit graphics settings such as texture quality and mip mapping ect...?  Possibly via the terminal?

---

### Post by Rocket2DMn on 2008-03-10
That is correct about your drivers and control center stuff.

I don't know how to edit (or if you can edit) those other settings with "ati", but with direct rendering and 3d acceleration enabled, it should be OK unless you're doing some really funky stuff.  Let me know if you find anything like that so I can spread the word when asked again.

---

### Post by phoenix5002 on 2008-03-11
Nope, nothing funky :)
Just want to squeeze a few extra FPS out of a game by reducing quality...

However the game in question uses wine, so is there anyway to increase performance, I've already done WINEDEBUG=-all but I'm hoping to reduce the quality of the game such as textures to get a decently large FPS increase.

---

### Post by Rocket2DMn on 2008-03-11
You can check your normal Ubuntu FPS capacity by running
```
glxgears -info
```
You will certainly lose some capacity under wine, but I always find it reassuring when I remember that LCDs typically only refresh at 60hz anyway.  So essentially, anything more than 100 or 120 FPS is more or less wasted capacity.  Latency is your biggest problem, not FPS.  Games often give the option of what resolution to run the game at, and running it in a window can help, too.  Also, turn off Compiz Fusion before you play.  If the game supports it, use OpenGL to take advantage of hardware acceleration (Direct3D is a windows thing, so you won't get too far with that!).

To turn off CF:
```
metacity --replace
```
To re-enable CF:
```
compiz --replace
```

What game are you dealing with anyway?

---

### Post by phoenix5002 on 2008-03-11
Well this is actually a pretty old laptop, and practically the most graphically intensive game I could play under windows was counter-strike 1.6 lol.  So ya, that's the game I would like to be able to run under Ubuntu, and then I won't even miss windows at all :) not that I do....

If I run it in a window at 640x480 I can get about 30-50fps, and I only go below 30 when there is smoke.  I actually find that I get a higher MUCH higher framerate in the presence of smoke grenades under Ubuntu then I ever did with windows which is good.
I would just like to increase the framerate a little so that I could run it in fullscreen with a widescreen resolution.
I can easily live with the framerate I'm getting now, but I would like it to be maybe a little higher because 30FPS is undetectable at 640x480, but at higher resolutions it can get choppy.

Also, I can live with this...I guess... but I do have 1 bug with counter-strike 1.6.  Certain images don't appear right, and I couldn't care less about the adds, but when I zoom in with say a sniper rifle it appears that the "scope" image doesn't show up right and is very obstructive to my view.  Most of the time the whole screen just goes black.  but as long as I don't use a scope with a gun then it runs perfectly, I would just like a slightly higher framerate. and I don't use compiz.

[EDIT] I get about 280-290 FPS with glxgears
I have a "Radeon IGP 345M"

---

### Post by Rocket2DMn on 2008-03-11
You may not be able to get a much better framerate than that.  I play cs 1.6 on my lapop which is about 4 years old, but I get a better framerate in Ubuntu than you do.  I run CS 1.6 in a window using OpenGL.  From within CS you can set the resolution, enable window mode, and drop the quality of the graphics to low.
You may find that the steam community stuff doesn't work under wine, but you can access your account stuff like adding friends and groups from [https://steamcommunity.com/](https://steamcommunity.com/)

Any other tweaks need to be done through Ubuntu, but I'm not sure there is much left you can do.

---

### Post by phoenix5002 on 2008-03-11
I increased my FPS by a good amount by finding some commands to put in a configuration file that cs loads.
Now I can play at my low widescreen resolution (800x500) fullscreen and I get about 40FPS or higher.  I bet I get really good FPS when I run it in windowed mode at 640x480.

Thanks for your help :)

---

