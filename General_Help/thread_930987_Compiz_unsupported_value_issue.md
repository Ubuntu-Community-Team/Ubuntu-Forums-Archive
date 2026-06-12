---
title: "Compiz unsupported value issue"
date: 2008-09-26
forum: General Help
---

### Post by breathoflife on 2008-09-26
Ide like to thank all whom take the time to read this, i am very gracious for the help as I am a total noob.

Im trying to enable compiz running on a 3DForce2-MX which seems to be working alright with the Nvidia legacy driver.  Ive installed emerald and compiz useing the standard procedure through synaptic package monitor.  I believe Emerald is running alright.  However when I try to run compiz only a few features work and in a terminal I  I get the following:

administrator@administrator-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Ive tried to find and examine the location its referring to with the file system browser but I haven't had much luck, nor would I know what I was looking at if I did find it.  Any advice is much appreciated!
Thanks to all

---

### Post by loomsen on 2008-09-26
Open up your settings manager by running ccsm.
Navigate to window management--> scale

And check your bindings.

The string you posted the problem is an initiate edge setting, so check the settings with a screen icon for their bindings, in doubt just disable them.

initiate edge means, for example, that you just gotta move your mouse somewhere to the screen to have a plugin enabled.
I, i.e., set the expo plugin to be initiated if I move my pointer to the bottom left edge and remain there for 350msec. But you can configure it as you like, just it shouldnt conflict with another binding you set, or it wont work.

---

### Post by breathoflife on 2008-09-26
Thanks, I didnt see any initiate edge settings enabled under the bindings tab in scale under window managment so I just disabled the scale plugin and it seems to have cleared the problem.  However I am now getting:

administrator@administrator-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (mag) - Warn: GL_ARB_fragment_program not supported. Fisheye mode will not work.

Ive noticed even when enabled I can only get about 50% of the plugins to function, When I try to enable the Cube Plugin and a few others, I get the following:

Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

which repeats for about 50 lines or so in the terminal

---

### Post by loomsen on 2008-09-26
Do this please:
```

wget http://blogage.de/files/3855/download?compiz-check_0.4-1_all.deb
sudo dpkg -i compiz-check_0.4-1_all.deb
compiz-check

```

This will install a script cheking your hardware. Your logfiles show it is pretty likely you either don't have the right driver for your graphics card installed or your xorg.conf isn't set up as it should be.

*edit*

You may want to look [at this too](https://help.ubuntu.com/community/CompositeManager/Xgl) according to your log.

---

