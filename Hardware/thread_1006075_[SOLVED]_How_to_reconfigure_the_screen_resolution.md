---
title: "[SOLVED] How to reconfigure the screen resolution"
date: 2008-12-08
forum: Hardware
---

### Post by JunCTionS on 2008-12-08
I just installed Intrepid Ibex on a VAIO VGNFW270.
The liveCD didn't load at first so I tried it in Safe Graphics Mode (F4 at the first screen for those with this same laptop).
After that everything seems to work fine (sound, wifi, mouse, etc.) except for the fact that it's in 800x600 (the resolution on this beautiful laptop is 1600x900).
So after installed the resolution stays at this setting (800x600) and the old
```
sudo dpkg-reconfigure xserver-xorg
```
does nothing else than reconfigure the keyboard.

I 've also noticed that the xorg.conf has changed a bit and now carries almost no information, so I preferred not to tinker with it.

If I do this:
```
xrandr --fb 1600x900
```
I tells me that screen cannot be larger than 800x600.

I see I could add a newmode, but I'm not sure how to determine many variables such as clock MHz, hdisp, hsync-start and so on.

So, can anyone please help me telling me how to auto-reconfigure or how to determine those variables so that I can add the newmode to the configuration?.
Thanks :)

---

### Post by JunCTionS on 2008-12-12
no need now.
I found the solution: reinstalling the intel drivers for new patched ones.
This works for the Sony VAIO VGN-FW270.
daniel in launchpad was nice enough to compile them.
Here they are (the 64-bit version of the drivers): [http://launchpadlibrarian.net/203928...0driver.tar.gz](http://launchpadlibrarian.net/203928...0driver.tar.gz)
Just install the three files in there (they replace the old intel ones so no need to uninstall them) and then change "vesa" for "intel" and then restart the X Server (Close and save anything important then press "Alt+Ctrl+Backspace" which will also log you out or reboot).

The thread that helped me is [here]("http://ubuntuforums.org/showthread.php?t=996395"). There you may find the 32-bit drivers if you wish to go with that.

---

