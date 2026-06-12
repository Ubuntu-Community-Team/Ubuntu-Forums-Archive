---
title: "Nvidia 8600GT Driver Problem..."
date: 2009-05-13
forum: Hardware
---

### Post by mellowtoad on 2009-05-13
Hi folks. I've installed a Nvidia 8600GT and have tried everything I know of trying to get it to work.

The install of Jaunty 9.04 went smoothly and I was able to load everything up in full resolution. However when I went to turn on the advanced graphics through the Apperance menu, I was given a message saying that Ubuntu was searching for my drivers. It goes through and installs and then tells me to restart. I do so. After the restart it loads up then goes to a screen saying that Ubuntu is loaded in Low Graphics mode. It also gives me an option to reload graphics drivers. So I do that, and it reloads in with the basic defualt drivers, no advanced graphics enabled.

After this I tried installing the drivers through the Hardware Drivers menu. This gave me an option of NVidia 176 or 180. I clicked 180 and hit apply. And it looked like it installed. It then tells me to reboot. I do so, and I once again get the boot screen saying running in low graphics mode. So I have to choose to reload my original drivers again. And reboot.

I then went in through EnvyNG and let it choose the drivers. Same problem was before. Low Graphics mode. The last thing I did was completely uninstall the Nvidia drivers, everything I could find, through Synaptic. I then went in and repeated all these steps again. No go. Finally I rebuilt the system, restarted from scratch and reinstalled. Same problem. 

Any ideas? I'm stuck.

---

### Post by Dark_Stang on 2009-05-13
Did you try the 176 driver?

---

### Post by mellowtoad on 2009-05-13
Yes I have. Sorry that I forgot to mention that. Had the same problem each time I tried that as well where I'd have the Low Graphics mode error.

---

### Post by osx on 2009-06-30
I was having the same problem, but for me using a VGA cable was the fix. My monitor has a DVI and VGA port, but my nvidia graphic card only has DVI ports. So, I removed the DVI cable, attached the VGA cable to the VGA port on the monitor, attached the VGA-to-DVI adapter that came with my video card to the VGA cable, attached that to my video card and have had the full 1680x1050 resolution ever since without having to tweak my xorg.conf file. I'm using a Viewsonic VX2025wm monitor (for some reason, the Viewsonics seem to be the most problematic in regards to passing correct EDID data).

---

