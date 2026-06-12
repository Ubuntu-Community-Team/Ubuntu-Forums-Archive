---
title: "Will there be conflicts between official nVidia driver, nVidia-GLX and Mesa?"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by rykel on 2005-04-14
Hi pal,

I have nvidia-glx and mesa libraries installed in my Ubuntu system.

But there was no 3D rendering, and the fps from glxgears was barely 70fps...

So I installed the official nvidia driver, and now my 3D works. I can play Tuxracer, SuperTux (thanks, autopackage!) and other great stuff...

HOWEVER, I wonder if there might be software conflicts between the official driver, nvidia-glx and the mesa packages?

If so, what can/should I do about it?

Thanks for helping me!


Best Regards,

Rykel
Singapore

---

### Post by Firetech on 2005-04-14
You should atleast uninstall the nvidia-glx driver, else it will break the official driver on an upgrade (just run "apt-get remove nvidia-glx" or remove it with synaptic/kynaptic). I don't know about the mesa driver though.

---

### Post by rykel on 2005-04-15
Hi thanks for the info... in fact, I believe they DO conflict and break each other... I cannot log into my login screen!

When I remove nvidia-glx, I can log in... BUT!

There is no 3D acceleration once again, and glxgears program is now missing.

Do you have any extra ideas?

---

### Post by s_ridenour on 2005-04-15
You need nvidia's GLX driver installed or else you won't be able to have 3D acceleration. Just install nvidia-settings (which is a nifty utility to let you adjust your hardware's settings), and everything else needed for 3D acceleration should also get installed (including nvidia-glx).

Once nvidia-glx is installed, do:
```

sudo nvidia-glx-config enable

```

And it should switch over to use nVidia's driver instead of Mesa. You might need to restart your computer.

And there shouldn't be any conflicts. nvidia-glx-config will make sure any OpenGL-related symlinks are pointed to the nVidia driver's OpenGL and GLX implementations. You'll know for certain that there aren't any conflicts if you run glxinfo and don't see anything about Mesa.

---

### Post by rykel on 2005-04-15
well, now i have reinstalled nvidia-glx AND the official nvidia driver...

i had just run glxinfo, and thanks, seems like i dont see any mesa stuff.

glxgears runs fine too...

whichever it is tat is working now i do not know, but i do know tat my 3D nvidia card is working now.    :)

---

### Post by Firetech on 2005-04-17
The nvidia-glx package and the official driver work fine side by side. BUT if the nvidia-glx package is apt-get upgraded (or via synaptic/kynaptic), the official driver will break. At least they acted like that for me.

---

