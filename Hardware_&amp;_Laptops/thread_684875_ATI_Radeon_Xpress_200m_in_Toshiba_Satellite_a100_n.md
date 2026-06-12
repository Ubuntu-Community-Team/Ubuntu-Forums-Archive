---
title: "ATI Radeon Xpress 200m in Toshiba Satellite a100 not working"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by darkmaster on 2008-02-01
Hello everyone, I'm having problems solving a problem with the laptop of a friend of mine. He has this Satellite Pro a100 laptop with a damned ATI Radeon Express 200m card. Out of the box, 3D didn't work with Ubuntu Gutsy. So he tried and turn the restricted drivers on. They were not working correctly, the problem was weird: in 1280x800 resolution only part of the screen was usable there was also a brownish part of the screen (an entire large part on the right of the desktop) absolutely unresponsible to any mouse movement or user interaction. As if the screen didn't work in that part of the screen... 

So we downloaded the ati drivers from the official website, installed them, looked as if they were working ok but hey, Compiz Fusion works and looks fully accelerated but what a surprise, glxinfo informs me that we have no direct rendering!!! How can Compiz Fusion work at full speed without 3D? Plus, I thought that with the ATI drivers, to use something like Compiz or Beryl you had to install xgl!!! But we didn't, Compiz (called desktop effects in Ubuntu) works fantastically without XGL!!! How is it possible, did I miss something? Since when ATI supports AIGLX?? So we tried starting a 3D game and it crashed the x session: back to gdm.

We also tried using Alberto Milone's Envy, same results... if we change the driver in xorg from fglrx to ati then x won't even start... black screen...
there's also to say that the monitor cannot be autodetected, reconfiguring xorg crasches in the attempt, so it is setted to generic monitor...

What can we do now? What ca we try to have it working? Trying to activate the restricted drivers now doesn't work, maybe because there are the ATI drivers installed already from the latest version available in the ATI's website... if I enable the ati drivers from the restricted manager, I am asked to reboot and after reboot nothing changes: looking in the restricted manager I see the "v" on the ATI proprietary drivers but next to it a red ball (not green) specifying: not in use!
Absurd....

Never had such problems. Please, can anyone help us on this? What can we do?

---

### Post by Yellow Pasque on 2008-02-01
> Since when ATI supports AIGLX??
I think it's been about a half-year now. What rock have you been under? :P Anyway, as you've seen, it's still buggy. I do not recommend any proprietary ATI drivers except the Ubuntu fglrx drivers (and I don't recommend using XGL/Compiz if you watch DVD's/video on your PC.)

Try booting into recovery mode and run these commands:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --Overlay-type=Xv
```

---

### Post by darkmaster on 2008-02-02
Ok, thank you, I'll tr it :)
I've been under an Intel GMA Rock ;)
And it really Rocks with OpenSource drivers, even if it is not as powerfull as an ATI or Nvidia. I use Ubuntu on my MacBook, you know, never had an ATI since a year :)
I heard rumors about ATI going gradually more opened and releasing new drivers but actually I knew nothing sperimented on my own computer :)

---

### Post by darkmaster on 2008-02-02
Well I followed your instructions... Aiglx doesn't work anymore of course, but the graphics are really messed up... no direct rendering anyway, opening the terminal resulats in a very slow frame starting from the icon and expanding sloooooooowly 'till it reaches full screen, then a terminal window appears, showing the flashing cursor all messed up... there are a lot of glitches even opening the various menu... I'm Gnome afterall, didn't know if I told you. Even if it has nothing to do with the driver....

So what should I do now? It works even worst than it did before :(
At least with the latest driver it was fast and I had aiglx... but I never have direct rendering :(

---

### Post by DrFreeze on 2008-02-02
this might not be of much help, but i myself have a laptop with x200 graphics (well, x1100, but its the same basic chip)

i just installed the default restricted drivers and then i think xgl, and i have a fully working 3d desktop with compiz, in xorg.conf my driver is listed as fglrx

---

### Post by darkmaster on 2008-02-02
> **DrFreeze said:**
> this might not be of much help, but i myself have a laptop with x200 graphics (well, x1100, but its the same basic chip)

i just installed the default restricted drivers and then i think xgl, and i have a fully working 3d desktop with compiz, in xorg.conf my driver is listed as fglrx

In mine it is listed fglrx too. No, it doesn't help because if I have no 3d acceleration, it is not like installing xgl something would go better :(

---

### Post by Yellow Pasque on 2008-02-02
> So what should I do now? It works even worst than it did before
If ATI's drivers don't work and Ubuntu's drivers don't work, then you're probably SOL. The other option is the open-source radeon driver.

If you'd like to go back to the ATI driver, you can follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by darkmaster on 2008-02-03
Extract from the first part of my post:

[INDENT]So he tried and turn the restricted drivers on. They were not working correctly, the problem was weird: in 1280x800 resolution only part of the screen was usable there was also a brownish part of the screen (an entire large part on the right of the desktop) absolutely unresponsible to any mouse movement or user interaction. As if the screen didn't work in that part of the screen...[/INDENT]

When things where that weird, in that strange situation, 3D worked but all the rest was messed up as described above. So the IS A WAY to have 3D working, I just don't understand which is it!!! I don't know what caused the system not to have 3D anymore!! Isn't a way to understand it and have that damned driver working correctly? They aways says that in Linux things can always be fixed, no real need for formatting, but it looks like in this occasion there's nothing else to do.... 

What could I do alone from formatting and trying all again??

Ah and the ATI OS driver doesn't work. Black screen. No GDM, nothing,

---

### Post by Yellow Pasque on 2008-02-03
> When things where that weird, in that strange situation, 3D worked but all the rest was messed up as described above. So the IS A WAY to have 3D working,...

> So we tried starting a 3D game and it crashed the x session: back to gdm

I don't think you ever had full 3D acceleration working properly. You may have had Compiz running with AIGLX (indirect rendering), but as you noted, you didn't have direct rendering enabled. If you figure out how to do that, please post the solution (I don't think a reinstall is the answer, but I guess it's worth a try if 3D is important to you).

---

### Post by darkmaster on 2008-02-03
> **Temüjin said:**
> I don't think you ever had full 3D acceleration working properly. You may have had Compiz running with AIGLX (indirect rendering), but as you noted, you didn't have direct rendering enabled. If you figure out how to do that, please post the solution (I don't think a reinstall is the answer, but I guess it's worth a try if 3D is important to you).

Ehm... maybe I didn't express myself right. I can ensure you that when I had that horrible screen resolution bug, 3D was working. I tested several games, even wine and it worked! I had 3d acceleration! Not only. If I turned on Compiz, ta-daaaan! The resolution suddenly became fixed! But I didn't want to use compiz at all costs... that's why I and my friend ended up messing things up :(
I can ensure you that, believe me. Infact I cannot achieve the same horrible resolution bug anymore!! I don't know what the heck did my friend to to end up in that absurd situation.... but at least 3D worked!

In any case, the other problem I noticed is that any video in fullscreen mode is very slow, something like 2 frames per second!! :(
It really looks like the driver is working very badly. Very very badly.

---

