---
title: "Cant detect monitor/graphics card"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by c_j on 2008-02-29
i just installed 7.10, but after its started up, i get a message saying that my graphics card and monitor could not be detected and it allows me to continue or configure it myself.

Ive tried configuring it or continuing and doing it through the admin menu (screen and graphics). i select nv drivers (i have an 8800GT), and clicking test or ok ends up back at the desktop, looking at the selected driver again, its set back to vesa. Ive tried setting the driver and choosing various monitors too, as it doesnt have my exact monitor (Relisys TL766) i tried either LCD panel or Monitor (and then the resolution i know mine supports). But it always goes back to the default vesa driver and plug and player monitor.

Ive tried updating everything too, but it didnt change anything
Also, if i go onto the restricted drivers manager in the admin menu, it tells me i dont have any hardware that requires that, i tried this as i used to have to use that for my 7600GT before i upgraded my pc.

does anyone have any solutions or ideas?

thanks
Chris

---

### Post by Scarath on 2008-02-29
1. Tried using [Envy]("http://albertomilone.com/nvidia_scripts1.html")? (i suggest using the text version: ```
sudo envy -t
``` with no xserver running, seems to work better for me that way)

2. Generally get rid of the restricted ubuntu drivers and use the ones from Nvidia, much better.

---

### Post by HoLLyw00dGT on 2008-02-29
> **Scarath said:**
> 1. Tried using [Envy]("http://albertomilone.com/nvidia_scripts1.html")? (i suggest using the text version: ```
sudo envy -t
``` with no xserver running, seems to work better for me that way)

2. Generally get rid of the restricted ubuntu drivers and use the ones from Nvidia, much better.

How do you get a driver for an nvidia card any other way than going to the restricted driver manager and enabling it? I have "No Signal" on my HDTV with the restricted. BTW not trying to hijack.

-Justin

---

### Post by Scarath on 2008-03-01
> **HoLLyw00dGT said:**
> How do you get a driver for an nvidia card any other way than going to the restricted driver manager and enabling it? I have "No Signal" on my HDTV with the restricted. BTW not trying to hijack.

-Justin

None Gui option:

Go to the restricted driver manager, disable the graphics, fall back to terminal mode (Alt+F1).

Then do:

```
sudo envy -t
```

And it will do the rest.

To get the drivers manually. Go the the nvidia website and get them or open a terminal and go:

```

wget copy_web_link_to_the_drivers_here
```

This will download the drivers into your home folder. 

[Here]("http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation") is more instructions

---

