---
title: "Ubuntu linux compiz 3d cube help."
date: 2008-08-05
forum: General Help
---

### Post by frog4044 on 2008-08-05
i installed compiz and enabled the cube but how do i start it? like what do i press or click to get it to show up?

---

### Post by tuxxy on 2008-08-05
You need to enable the **rotate cube plugin** now check what bindings you have it set too usually CTRL + ALT and mouse button 1 by default I think.

press these and then rotate with your mouse once you have enabled the plugin.

---

### Post by frog4044 on 2008-08-05
> **tuxxy said:**
> You need to enable the **rotate cube plugin** now check what bindings you have it set too usually CTRL + ALT and mouse button 1 by default I think.

press these and then rotate with your mouse once you have enabled the plugin.

but where would i go to enable this plugin? im just switched to linux about 3 days ago. just got wireless internet working and a few desktop effects. everything is hard but im learning. i enabled the desktop cube when i go to extra desktop effects is this what you mean? and once i do have everything working how do i start the cube like what do i click or press? thankyou

---

### Post by AnarchyCow on 2008-08-05
Make sure you have "ccsm" installed.
I believe that's
```
sudo apt-get install simple-ccsm
```

CCSM is a simple graphical user interface to configure compiz.
Once you do the command above, it can be found in "System -> Prefrences -> Advanced Desktop Effects Settings"

Mine works perfectly, other than being a little aliased. I installed:
```
simple-ccsm - Simple Compizconfig settings manager
compiz - OpenGL window and compositing manager
compiz-core - OpenGL window and compositing manager
compiz-dev - OpenGL window and compositing manager - development files
compiz-fusion-plugins-main - Collection of plugins from OpenCompositing for Compiz
compiz-fusion-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz
compiz-gnome - OpenGL window and compositing manager - GNOME window decorator
compiz-plugins - OpenGL window and compositing manager - plugins

Just Enter:
sudo apt-get install simple-ccsm compiz compiz-core compiz-dev compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins
```

---

### Post by alsamman on 2008-08-05
To install the Compiz Manager

```
sudo apt-get install compizconfig-settings-manager
```
Go to System>Preferences>Appearance, click Visual Effects and select Extra
Then go to System>preferences>Advanced Desktop Settings and you can find Desktop cube and Rotate Cube, enable those. Then to make a cube go to General Options in Advanced Desktop Settings, click Desktop Size and increase horizontal size to 4. To start the cube, hold ctrl+alt and left click

---

### Post by frog4044 on 2008-08-05
ok got it working thanks everyone!

---

### Post by ikitson on 2009-09-20
I seem to be having the same problem, i followed all these steps and got the plugins installed, but my cube still doesn't come up when i press the hotkey even when it's activated, what should i look into next?

---

### Post by MegaLoler on 2009-09-20
Me too, and when I click on extra in visual effects, it says Dekstop effects cannot be enabled. :confused:

I'm using Ubuntu 9.04 on PPC

---

### Post by ramanabv on 2009-09-21
Thanks everybody. The compiz is working as it is supposed to. I have installed emerald for decorations. The disappointment is that the 3D windows and cube are not so glamorous as we see in youtube etc. I have to hold down the ctl,alt,mouseleft to see the cube. I need to hold on to the keys and move the cursor to rotate the keys. It is too much work for nothing.

The cube is also not perfect. If I have default screen then the cube is some what OK. However if I have applications like firefox etc , these appear big as seperate planes and I can see the actual cube smaller inside. 
How can I adjust so that the cube is perfect?

Thanks 
Ramana

---

### Post by xfearxnxloathing on 2009-09-21
easy, just click your scroll wheel on your mouse down =]

---

### Post by ramanabv on 2009-09-22
> **xfearxnxloathing said:**
> easy, just click your scroll wheel on your mouse down =]

Great. Works fine. One last question. I get ubuntu ( logo screen on top of the cube. Bottom side is a blank screen. How do I change or set the bottom and top wall papers?

Thanks
Ramana

---

