---
title: "NVidia Drivers on Dell XPS M1710 with 7900GTX"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by oddball on 2007-04-03
Evening all...

Just wnated to share my experience with Feisty beta and the XPS M1710 Laptop from Dell, and at the same time ask a couple of questions.

Initially when I first used the Live CD, at least I think it was the install CD, but it MIGHT have been my first boot of the installed OS before any updates, anyhoo, I checked out the restricted drivers section and sure enough my Intel Wifi card was there enabled and working away and my NVidia 7900GTX was also listed, but at this point I didn't enable it.

Any time passed, I installed Feisty (assuming I was in Live mode) and I started by making sure everything worked just as I wanted and it did, everything was looking very good, infact, the best Ubuntu I've seen yet!!

So, I figured I'd head back to the restricted drivers section and enable the NVidia drivers, but they'd gone?!?

Hunted around on the Net for answers, and in the end did a:

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo nvidia-settings
```

and then set everything up like that, which is fine.

Have I gone mad??  Was I seeing things??  Should the Nvidia driver be listed in the restricted modules manager??

The last thing is, after having setup my card using the above commands, I've noticed that whilst the desktop looks splendid, the username and password box on the gdm login screen has disproportionally large fonts in it - nothing major, just curious as to why this happens and if it can be fixed.

That's all for now!

Byeee!!

---

### Post by Ekril on 2007-04-08
There is a problem within fonts folder.
check out your xorg.conf and look if the fonts folder shows the right place

---

### Post by hardatk on 2007-06-06
I also noted the problem after installing the nvidia drivers, the font was unusually large on the login screen.... and then I installed enlightenment DR16 and the font had issues there too...

The font path's in my xorg.conf file are set to the default:

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Should they be set to something else?

Thanks in advance for the help!

---

### Post by orz on 2007-07-02
I am having a similar issue with my M1710 and just joined these forums explicitly for a solution to it.

I'm admittedly new to Linux, and while I can find my way around a DOS prompt like the back of my hands, I'm new to this shell and interface.  I have downloaded [nVidia's Linux IA32 driver (100.14.11)]("http://www.nvidia.com/object/linux_display_ia32_100.14.11%20.html") but don't know how to work with the .run file.  I'm supposed to use 'sh' to run it, and configure my xconfig file, but I'm a bit lost with the syntax.  When I type 'sh NVIDIA-Linux-x86-100.14.11-pkg1.run' in the directory of the file, nothing happens at the prompt.  :(

I need a primer or walkthrough for the shell to get a handle on this process.

---

