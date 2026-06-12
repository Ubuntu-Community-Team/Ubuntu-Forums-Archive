---
title: "Intel and 3D problem (ASUS U3S)"
date: 2011-01-05
forum: Hardware
---

### Post by L33tCh on 2011-01-05
Ok, I've been looking everywhere trying to find a solution to this, but so many come close, but are not my exact issue.

My system is as follows:

Ubuntu 10.10
ASUS U3S
Switchable graphics cards:
[LIST]
[*]Intel (Mobile GM965/GL960 Integrated Graphics Controller)
[*]NVidia (GeForce 8400M G)
[/LIST]
I don't think the rest is relevant for this issue, but if you need, let me know.

I have set up a script to switch between the cards with respect to which the switch is set to, but only while running the nvidia am I getting 3D acceleration. I cannot at all get 3D on the intel card to work.

The output of glxinfo for example (while on the intel card) is:
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I also noticed this line in the Xorg log:
```
[  1612.300] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

Maybe this is the main issue? Why is the glx module still looking for the NVidia when I'm running the Intel card?
I have seen a few threads on removing all NVidia references to get an Intel card to work, but of course this is not a solution for a system that runs both...

I have also played a lot with xorg.conf, but nothing I do seems to have any effect, though after some changes, the display stays black after rebooting, just after the Ubuntu loading screen, but when I reboot again it's back to how it was.

Any ideas would be hugely appreciated!

---

### Post by MarcSpitz on 2011-01-06
I have done the exact same thing as you (using Alienware m15x) and it works quite well except for 3D games on intel chip. So any solution would help me as well!

Compiz does not work on my intel card (and I can't activate it when on Nvidia card either - maybe this works with your solution?).

---

### Post by L33tCh on 2011-01-07
So I've read [here]("http://ubuntuforums.org/showthread.php?t=276040") that the problem has to do with the glx drivers for whichever card you used when installing... They mentioned where to find them etc, but essentially, from another post somewhere, the idea is as follows:
[LIST=1]
[*]Uninstall nvidia-glx
[*]Allow linux to install Intel GLX when rebooting
[*]Backup the GLX.so file
[*]Switch back to NVidia and reboot again
[*]Install NVidia GLX again
[*]Back the GLX.so up again
[*]Include switching the glx files in the switching script
[/LIST]

Now I didn't see confirmation and it is very possible I've missing some steps or files that need to be backed up, but I'm gonna do what I can to see if it works... 

On another post, they seem confident it is a glx/dri conflict, the above being a solution. [Here is the post]("http://ubuntuforums.org/showthread.php?t=331163").
Here is an example of a script used on the GLX files in that thread:
```
VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf-speed /etc/X11/xorg.conf
modprobe drm
modprobe nvidia-agp
rm /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/libGL.so -f
ln -s /usr/lib/xorg/modules/extensions/libglx.so.1.0.8776.bak /usr/lib/xorg/modules/extensions/libglx.so

ln -s /usr/lib/libGL.so.1.0.8776.bak /usr/lib/libGL.so.1
else
modprobe intel-agp
cp -f /etc/X11/xorg.conf-stamina /etc/X11/xorg.conf
rm /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/libGL.so -f
ln -s /usr/lib/xorg/modules/extensions/libglx.so.bak /usr/lib/xorg/modules/extensions/libglx.so
ln -s /usr/lib/libGL.so.1.2.bak /usr/lib/libGL.so.1

fi
```

Again, I'm not sure if this is the golden solution in this case, but it sounds damn promising.
Let me know if you get anywhere. I'll keep my progress updated as well. When I find the correct steps to a solution I'll update this post.

---

### Post by L33tCh on 2011-01-07
Arg, so I don't have nvidia-glx installed... I'm going to just uninstall everything nvidia, see if I can get my intel card to work... then if it does, I'll start making backups as above, oi.

*EDIT* 

Woohoo, ok, so I now have Compiz running on my Intel card... Now I just need to try keep it that way when I get my NVidia back up. Oh, and glxgears is running at 60fps, syncing with my LCD I assume.

Now let's see if I can get both going... (though it may have to wait a while... I should get back to some work;))

---

### Post by MarcSpitz on 2011-01-24
Happy to see that you got it running!

I will try to adapt your script to my config and see if it works. If it does I will post the script =).

---

### Post by MarcSpitz on 2011-01-24
I tried to run compiz on the Intel chipset with no luck.
I purged xorg and reinstalled it, regenerated xorg.conf ans rebooted. It still doesn't want to work.

Can you detail what you did in order to get compiz running on your intel chipset?

Thanks

EDIT : I also uninstalled everything Nvidia before trying

---

### Post by L33tCh on 2011-01-26
I stayed with the Intel card for so long it was only much later that I tested whether the script had worked... and sadly it had not. I'm almost certain though that it's only due to incorrect or not all the needed files being switched.

With regard to getting the Intel card to work in the first place, I was lucky enough that merely uninstalling the NVIDIA files was enough, and then merely restarting gdm.

I'll link my xorg.conf when I'm on that system again (the companie's got me a company laptop now so I can't mess around in my free time anymore:( )

---

### Post by amjad22 on 2011-01-26
I found the problem. Seems the kmod drivers for nvidia are broken. I used the sh file directly from the nvidia site and it work no problem.

---

