---
title: "X: have to use &quot;NoPowerConnectorCheck&quot; option"
date: 2009-01-07
forum: Hardware
---

### Post by mrowth on 2009-01-07
I have a Geforce 7600 GS (AGP) and the Nvidia drivers from the nvidia-glx-new 169.12+2.6.24.14-22.53 package. 

After powering up the PC or resuming from suspend-to-RAM, the fan on the card needs help spinning up... every now and then. At the moment it doesn't. 

Gkrellm/Conky report GPU temps at around 51°C while running Compiz. That's actually cooler than I'm used to (but then again it's January). Either way, it's fine.

But since yesterday I can no longer start X without disabling the power connector check in Xorg.conf. It'll flash black a few times then go into some lo-res setup GUI that doesn't list my monitor (monitors, actually), nor will it let me leave.

When I put Option "NoPowerConnectorCheck" "true" in Xorg.conf's "Screen" section the Nvidia logo will appear as usual, and everything's fine. Twinview, 3D, Compiz, temperatures, resolution, all is as it should be.

What I want to find out is -- what's broken, exactly? Fan? Card? Sensor on card? Sensor on mainboard? Driver? Something?

---

### Post by an0nu4nc3 on 2009-11-20
This has just started happening to me on 2.6.31.15 Karmic with nvidia-glx-185.18.36 drivers installed, running wine 1.1.33 (1.2) and EVE online Apocrypha.

Everything was working fine (apart from the BITS bug) for a couple of days until last night when my system froze up (it seems to be related to alt-tabbing) and the keyboard started flashing the Caps-Lock and Scroll-Lock lights simultaneously. I restarted my computer and disabled my network, started EVE, alt+tabbed to a VOIP client to get access to the systray, activated the network, logged in to the VOIP client, clicked on the EVE window which is still in the background (where the desktop should be), logged into EVE and there was a problem logging into the VOIP client so i alt-tabbed again and this time everything just froze. No flashing lights.

Upon a restart i encountered this:

```
(EE) NVIDIA(GPU-0): Your GeForce 7800 GT graphics card does not have the necessary
(EE) NVIDIA(GPU-0):     external power cables attached; X will not start unless
(EE) NVIDIA(GPU-0):     this is rectified.  Please shut down your computer, open
(EE) NVIDIA(GPU-0):     its case, and attach the appropriate power connectors. 
(EE) NVIDIA(GPU-0):     Your video card may have multiple power connectors.  If
(EE) NVIDIA(GPU-0):     so, each must be attached to a separate power cable. 
(EE) NVIDIA(GPU-0):     Please see the documentation provided with your video card
(EE) NVIDIA(GPU-0):     for more details.  If you think you have received this
(EE) NVIDIA(GPU-0):     message in error, you may specify the
(EE) NVIDIA(GPU-0):     "NoPowerConnectorCheck" X configuration option in the
(EE) NVIDIA(GPU-0):     Screen section of your X config file.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

Then it gives me options to generate a new xorg.conf or debug it myself etc.

Whatever i do, everything seems to be fine eventually and i can then start my system with everything running as normal, nvidia drivers enabled etc. Until i start EVE and try to Alt+Tab out in order to re-activate my network. Now it just freezes or flashes Caps+Scroll-Lock at me every time. No more EVE. No more working graphics cards. WTF?

I'll do the NoPowerConnectorCheck option for now... but this really ought to be looked at sometime, don't you think?

Is it an SLI incompatibility?

I hope they fix the BITS thing soon as that would avoid the problem as long as i don't alt+tab anywhere.

---

