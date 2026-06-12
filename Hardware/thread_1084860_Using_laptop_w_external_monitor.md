---
title: "Using laptop w/ external monitor"
date: 2009-03-02
forum: Hardware
---

### Post by ggtsu on 2009-03-02
Today my boss tried to surprise me with a nice new external monitor to use along with my laptop. Little did I know how much of a curse this would actually be. I've used dual monitor setups in windows in the past and always found this easy to setup. I'm going to take a wild guess and assume that this is not the case with ubuntu. At least, it hasn't been so far.

First, my monitor's native resolution isn't on the list of supported resolutions. I want 1920x1080, but the highest I managed to get is 1440x900. I've already gone around looking for the best way to change resolutions, but there doesn't seem to be much consensus on the best way to do this. Also, aren't there any kind of dual monitor utils, like ultra mon for windows? Dual monitor support seems to be lackluster at best in ubuntu. Please help before I jump kick this monitor off my desk with my karate.

---

### Post by kvarley on 2009-03-02
I need help with this too! :(

---

### Post by Nostalos on 2009-03-02
Not sure which version of Ubuntu you are using.   Laptop setup me under 8.10 was very simple.   The Screen Resolution tool works quite well for me.

Previous versions where a little more work but realativly easy.    What resolutions are you trying to put the laptop screen and the external monitor in to?

---

### Post by ggtsu on 2009-03-02
I'm trying to get both running at their native resolution. The 1920x1080 native resolution of my external monitor isn't available in the list of resolutions. I'm using 8.10.

---

### Post by sgosnell on 2009-03-02
Have you tried clicking on the Detect Displays button, the big one in the Monitor Resolution Screen?  By default, all you'll see listed when you open that is what has previously been used.

---

### Post by wsonar on 2009-03-02
what video driver?

for my nvidia I used the nvidia-settings to configure

---

### Post by ggtsu on 2009-03-02
Weird. I decided to try and start again from scratch. I changed everything back to the way it was before I added the external monitor. I un-clicked mirror monitors and then detect displays. Then I noticed that I had a bunch of new options on the resolution. The thing is, I had done everything exactly this way several times before without any success. Well, now that things are working is there any way I can have one background image per monitor? My wallpaper is stretched across both screens and looks like crap.

---

### Post by wsonar on 2009-03-02
that's one thing I don't like how it handles extending the desktop and stretching the wallpaper instead of having the correct resolution for both screens

---

### Post by jalexstark on 2009-03-02
The display switching apparatus in Intrepid is poor.  Some "improvements" have been made to the windowing infrastructure that have caused breakage all over the place.

I was about to give up (well, last night we did), but this thread prompted me to try again.  On _this_ occasion, the external monitor and "mirror screens" feature failed completely until I unchecked the mirroring, then clicked on the external monitor, then selected a resolution for it, and then clicked "Apply".

There is a bug somewhere underneath.  On hitting "Apply" in "Monitor Resolution Settings" the external monitor would get a momentary signal.  Note that the login window _did_ appear on both monitors.  (Dell Inspiron E1505 MM061 with updated A17 BIOS.)

If you do get the login window on the external monitor, it often seems possible to give the video a "kick up the behind" by playing with the resolution settings widget.

On my other machine in the port replicator (a Thinkpad), nothing appears until the login screen, but that may be a BIOS problem...

---

### Post by jpaul6160 on 2009-03-10
This hadn't worked in the past.  But it is now.  Thanks.:P

I am using ubuntu 8.10 on an HP nx6325 in a docking station connected to a 32" i-INC via the vga port.  I needed the 1920x1200 display and it is working great.

---

