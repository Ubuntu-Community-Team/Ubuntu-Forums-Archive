---
title: "Strange Notebook Problem with intel onboard graphics"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by fragility14 on 2007-06-29
I just installed Linux for the first time (Ubuntu Studio), and I am having problems with my notebook's graphics card, in Intel's 82852/82855 line.

On windows my notebook was actually showing the graphics card twice (and two monitors) and if I restarted the computer after uninstalling both, both would show up again (very strange, there is distinctly only one, no idea when it started doing that), And I could disable the one getting less resources and it made it work a bit better...

I reformatted, in no small part because my computer wasn't working well, installed Ubuntu, and now it shows two video cards and three video card controllers. Yet, none of them actually show up as having the i810 driver, though I downloaded the newer version from the packet manager.

I am very frustrated, and downloaded the supposed intel driver but am unable to even succesfully install it, though I've tried in the command line. My computer runs EXTREMELY sluggishly, significantly worse than it did on XP. I have a 1.5 centrino with 1024 DDR 333 Ram, and a 64 MB Intel Extreme Graphics 2 video card. There is now definitely no 3d acceleration. I am almost sure the graphics card just needs to be installed.

Also, there is a weird error when it starts, which comes up after it stalls at the beginning of the loading bar for Ubuntu Studio, it goes to a bunch of text, and then comes back. When it is starting it shows two smaller and pink versions of the screen on top and a clear view of the bottom half of the screen.

When it loads it in general works fine just very sluggishly (like it is using the most basic graphics card ever).


Edit: that error is Intel_RNG FWH Not Detected

---

### Post by fragility14 on 2007-06-29
...please?

---

### Post by tronica on 2007-06-29
So you don't have the drivers installed? If not try this from the terminal

```
sudo apt-get install xserver-xorg-video-intel
```

also can you post the contents in your /etc/X11/xorg.conf

---

### Post by fragility14 on 2007-06-30
When I put in that command it said I already had the newest driver.

I followed different steps which involved converting an rpm file that was an intel driver, and then putting in some code and it sped up a little bit but not really. /etc/x11/xorg.conf doesnt work, no such file or directory, sudo apt-get xorg doesnt do anything, sudo xorg.conf doesnt do anything.

also, sudo glxinfo fails because of insuffecient resources (bad allocation)

---

### Post by tronica on 2007-06-30
To post the contents of your xorg.conf put this into the terminal:

> gedit /etc/X11/xorg.conf

and copy/paste it.

---

### Post by fragility14 on 2007-07-02
somehow I messed up but the sound and internet on my notebook, so I can no longer actually copy and paste from my notebook, I havnt tried it with a wired connection but it doesnt show a connections options at all, sound is just missing something. The system is finding all sorts of errors...I have some ideas for working on things....




The result from entering that is 

"ALSA lib pcm_direct.c.1588: (snd_pcm_direct_parse_open_conf) The field ipc_gid must be a valid group (create group audio)"


repeated three times, a blank .x11.xorg.conf (/etc) - gedit showed up, and my command line never came back on terminal.

I'll google that message at least...

---

### Post by fragility14 on 2007-07-03
I reformatted my computer and started over. I tried to do things in a better order. I still am unable to run xorg.conf or glxinfo. My computer still runs atrociously. I have installed the recommended driver and all of the updates, but it's been completely unproductive.

Also, now I can't access network tools, even though my computer is connected to a wireless connection while showing itself as being wired.

---

