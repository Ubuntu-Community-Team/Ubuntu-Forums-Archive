---
title: "Problem with Graphics driver"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Alex Demille on 2009-06-16
I just installed 9.04 and I'm having a small problem with my screen resolution. I keep getting this when I attempt to go to my 

"It appears that your graphics driver does not support the necessary extensions to use this tool"

I wish to have a resolution of 1200x--- +
Any one have any tips to clear this and expand my desktop?

---

### Post by Mark Phelps on 2009-06-17
> **Alex Demille said:**
> I just installed 9.04 and I'm having a small problem with my screen resolution. I keep getting this when I attempt to go to my   ... your "what"??

How are you attempting the change the resolution?

Also, what video chip/card are you using and what is the current screen resolution?

---

### Post by Alex Demille on 2009-06-17
(Heh, that's called a 'slight' brain fart :P)
I'm opening up "display" under System->Preferences. 
I'm using Nivida driver, and the screen res. is currently 1024x768

---

### Post by tommcd on 2009-06-18
If you have installed the nvidia driver (it is not installed by default) then open a terminal and run:
```
sudo nvidia-settings
```
The nvidia settings window should give you the option to change the screen resolution to what you want.

---

### Post by Alex Demille on 2009-06-18
\sigh, alright thanks, I was tinkering with the wrong setting.

---

### Post by Alex Demille on 2009-06-18
Alright, now more problems blast!. 

I can change the size of my screen to another setting but after restart it reverts to the "auto" setting.
This is really ticking me off, any help?

(The picture below is what I'm opening. I'm changing the "Resolution" setting. The Pop down bar (first).)

---

### Post by tommcd on 2009-06-18
Can you post the output of:
```
cat /etc/X11/xorg.conf
```
These days, xorg is supposed to automatically detect your screen resolution and refresh rates without having to specify them in xorg.conf. If xorg is not setting it up right then you can add the resolution and refresh rates manually to xorg.conf and it should hopefully work.

From the screen shot you posted, it shows the resolution as 1152 x 864 (as best as I can read it anyway). Is that the screen resolution you want? The "auto" is for the refresh rate. As long as the screen looks ok, and doesn't have a lot of flickering it should be ok to leave it there.

Is this a CRT monitor? If so, does the monitor have controls to adjust the resolution and refresh rates? If it does then try using them.

---

### Post by Alex Demille on 2009-06-19
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Is what I got when I entered the code.

I like the 1152x864 size, but each time I restart the screen reverts to "auto" with seems to be a 10--x--- size (to small). (The "Auto" You see for refresh isn't what I'm concerned about, it's the size that keeps changing).

And yes, (sadly) I'm running an old CRT. It doesn't have the Refresh/resolution as much as I can tell. The closest I can see on it is the information where is says "Recommended Timing: 1280x1024 / 76Hz" But that's all.

---

