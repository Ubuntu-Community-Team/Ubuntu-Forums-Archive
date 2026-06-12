---
title: "Intel 915, 1280x800 resolution"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by nlippincott on 2005-11-25
I have done some work to get 1280x800 resolution working for a widescreen display on a Gateway laptop that uses the Intel 915 chipset. I have a fair degree of success to this point, but am not getting decent video display out of the Totem Movie Player. Colors appear to be washed out, leading me to believe there is some setup problem.

Here is what I have done so far...

I found that, after installing 5.10 out of the box, xorg.conf was set up to use 1280x800 resolution, but I was actually getting 1024x768. So everything on the display was stretched out. I ran across package 855resolution, and this enabled me to get into 1280x800 mode. All looks good at this point, except for the movie player and some Flash stuff in Firefox.

I have tried a few things in xorg.conf, like taking out 'Modeline', and commenting out all video modes except 1280x800 at 24 bits per pixel, with no success.

Before I got 1280x800 working, I was able to use the movie player without any problem - colors looked great. Only problem, of course, things were stretched out.

Does anyone have any suggestions on where to go from here?

---

### Post by quietglow on 2005-12-04
(sorry to hijack!)

I'd be eternally grateful if you could tell me what you did to get that Gateway laptop into 1280x800!! I'm using a new Platinum edition of one of them (you have a m460?) and cannot get out of 1024x768!

Thank you so much.

---

### Post by simohell on 2005-12-31
I have got a 915GM running 1280x768. I had to rewrite all modes to 1280x768 with 915resolution. For me Totem (Xine) show all the colours nicely on the first time I run the program after booting the laptop. I can even play different movies, but if  I shut Totem down and restart I get something that looks like 8bit video output.

---

### Post by simohell on 2005-12-31
Now I have Totem working as well. I did have the same problem with VLC and that is fixed as well.

I swapped back to Breezy's i810 driver instead of intel's version. Also I added to my xorg.conf the line
```
Load  "drm"
```

Maybe this would work for your Totem also?

---

### Post by er-ku on 2006-01-01
One possible reason for your problems is that you have too little shared RAM reserved as VRAM. Try reserving more shared RAM for video purposes in BIOS.

---

### Post by simohell on 2006-01-20
[QUOTE=er-ku]One possible reason for your problems is that you have too little shared RAM reserved as VRAM. Try reserving more shared RAM for video purposes in BIOS.[/QUOTE]

For some 915GM using laptops it is not possible to reserve RAM in BIOS setup. This can however be done simply by editing xorg.conf. 

```
Section "Device"
        Identifier      "Intel GMA 900 CRT"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "Display"       "CRT"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          1
EndSection
```

However RAM availybility is not likely to be a problem, since X by default appears to be reserving additional RAM when it starts. To check the amount you whould need to check your Xorg.0.log.

---

### Post by darm on 2006-01-26
Sounds strange to me, I have Acer laptop on i915 and simple dpkg reconfigure xserver-xorg helps.

But well, were you able to get accelerated video? My DVD movies are way too 'jumpy'(and dma is on)

---

### Post by kingsidy on 2006-01-26
found this googling

Ubuntu allows one to select 1280 x 800 resolution, which is the right one. However, it adamantly wants to use 1024 x 768, which looks stretched and very ugly. A nifty program called 915resolution is need to hack what the BIOS tries to say. It's a very simple fix.

Use Synaptic to download 915resolution.

Open the terminal and type sudo gedit /etc/init.d/bootmisc.sh to edit the boot-up script.

Add /usr/sbin/915resolution 58 1280 800 before : exit 0 at the end of the script.

Restart the notebook and the resolution should look crisp and clean.

---

