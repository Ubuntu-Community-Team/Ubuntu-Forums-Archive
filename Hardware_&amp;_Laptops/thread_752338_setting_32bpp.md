---
title: "setting 32bpp?"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by Doctor J. on 2008-04-11
I'm running Feisty on a PowerBook G4 with a GeForce FX Go5200 video card.  There's a game i'd like to run that won't go in the current settings
```

------- video initialization -------
SDL version: 1.2.11
I: desktop depth: 16bpp
I: setting mode 6: 1024x768 (fullscreen: no)
SDL SetVideoMode failed: Couldn't find matching GLX visual - try to change the r_bitdepth, r_colordepth and r_stencilsize value
Failed to set video mode 1024x768 windowed.
SDL SetVideoMode failed: Couldn't find matching GLX visual - try to change the r_bitdepth, r_colordepth and r_stencilsize value
```

The support forums for the game advise that desktop depth needs to be set to 32bpp.  I don't see any color depth settings in System -> Preferences -> Screen Resolution.  How do i go about setting this?  
P.S. I know the card is capable, as the game runs fine when booted into OS X.

---

### Post by prshah on 2008-04-11
> **Doctor J. said:**
> I'm running Feisty on a PowerBook G4 with a GeForce FX Go5200 video 
The support forums for the game advise that desktop depth needs to be set to 32bpp.  I don't see any color depth settings in System -> Preferences -> Screen Resolution.  How do i go about setting this?  
P.S. I know the card is capable, as the game runs fine when booted into OS X.

You can set the color depth to 32bpp by editing the **/etc/X11/xorg.conf** file and finding and changing the line "DefaultDepth". Note that by default color depth _is_ 32bpp (which is 24-bit + addl gamma information). If you can't find the line, you can add it in the relevant Screen option: I quote mine below as an example:

> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"SyncMaster"
[color=red]	DefaultDepth	24[/color]
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


---

### Post by Doctor J on 2008-04-14
> **prshah said:**
> You can set the color depth to 32bpp by editing the **/etc/X11/xorg.conf** file and finding and changing the line "DefaultDepth". Note that by default color depth _is_ 32bpp (which is 24-bit + addl gamma information). If you can't find the line, you can add it in the relevant Screen option: I quote mine below as an example:

ARGH!  I changed it to 24 [there is no 32 bit section given for my setup] and, per the comment in the configuration file, ran "sudo dpkg-reconfigure -phigh xserver-xorg" and accepted the already selected values.  Now i appear to be hosed, as the initial login screen is a blur of psychedelic colors.  I did the ctrl-alt-F1 to go back to the command line, and changed xorg default back to 16 bit.  This somewhat changed the psychedelic colors, but it's still not intelligible.  Since i already restored the only thing i changed back to its original condition, why isn't xorg giving me a viewable screen?  I did also rerun the dpkg-reconfigure, but it didn't help.

---

### Post by prshah on 2008-04-14
> **Doctor J said:**
> and, per the comment in the configuration file, ran "sudo dpkg-reconfigure -phigh xserver-xorg" and accepted the already selected values.  Now i appear to be hosed, as the initial login screen is a blur of psychedelic colors.  I did the ctrl-alt-F1 to go back to the command line, 

FIRST THINGS FIRST:

Check your /etc/X11 for backup xorg.conf's; there will be atleast "xorg.conf~". Try copying one of them over your existing xorg.conf and see what effect you get.

There's no need to do the "dpk-..." unless you actually want to change your configuration. Try editing the file again, set DefaultDepth to 16, then save and exit. Switch back to Ctrl+Alt+F7 then press ctrl-alt-Bkspace to restart the server... any improvements?

---

### Post by Tillanz on 2008-04-20
I have almost exactly the same error.  I'm also running an Nvidia card - the 8800GT.

------- video initialization -------
SDL version: 1.2.11
I: desktop depth: 32bpp
I: setting mode 6: 1024x768 (fullscreen: no)
SDL SetVideoMode failed: Couldn't find matching GLX visual - try to change the r_bitdepth, r_colordepth and r_stencilsize value
Failed to set video mode 1024x768 windowed.
SDL SetVideoMode failed: Couldn't find matching GLX visual - try to change the r_bitdepth, r_colordepth and r_stencilsize value
Error: Video subsystem failed to initialize

I get a similar error when trying to run several other games... (okay, one of them just worked, which I find a little creepy since I don't think I changed anything...) mainly 3D games I think.

e.g.1
error   : Error: SDL_SetVideoMode failed (Could not create GL context).

e.g.2
Exception: Couldn't set video mode 640x480 (32bpp 0 stencil 16 depth-buffer). SDL Error is: Could not create GL context

I'm hoping it's just a case of missing a library somewhere...  but I get the feeling it might be a driver issue.  I'm running the latest Nvidia drivers...

...I could probably try changing to the open-source drivers or something, but at the moment I'm not particularly game.  It took me long enough to get my setup working the way it is now.

---

