---
title: "How can I do this on my Macbook?"
date: 2008-08-26
forum: General Help
---

### Post by Tigercat212 on 2008-08-26
[http://www.youtube.com/watch?v=jzVB7h4UvTc]("http://www.youtube.com/watch?v=jzVB7h4UvTc")

How do I get the windows to dissapear by catching on fire, write on the screen using fire? How do you activate multiple desktops? How can I activate "wiggly windows?"

---

### Post by Genius314 on 2008-08-26
You need to turn on Compiz-Fusion.

Go to System>Preferences>Appearance, click on the Visual Effects tab, and click on Normal or Extra.

Now to tweak the settings, and enable additional effects (like fire), you need to install CCSM. Open a terminal and type:
> sudo apt-get install compizconfig-settings-manager

Now go to System>Preferences>CompizConfig Settings Manager.

Wobbly windows should be activated by default. If not, check the box next to "Wobble Windows."

To draw with fire, scroll down to the plugin "Paint Fire on the Screen." Check the box. If you click on the plugin, you can change settings, like color, and keyboard shortcuts. Click "Back" when you're done.

To have windows burn up when you close them, go to the "Animations" plugin. In the "Close Animation" tab, there should be a list of window types and animation types. Click on the one that includes "type=Normal," and click "Edit."
Change the "Close effect" box to "Burn."

Multiple desktops should also be enabled by default. I think the default is Ctrl-Alt-Left or -Right to switch desktops.

Hope that helps. :popcorn:

---

### Post by Tigercat212 on 2008-08-26
Thank you Genius314!

---

### Post by kooperWD4 on 2008-08-28
Does anybody know what more I have to do to get Compiz Fusion to work on Ubuntu 8.04. I am running Ubuntu on my macbook which has a intel GMA x3100 graphic card.

Here is where I am at so far. I supposedly installed xserver-xgl, but it still says no xgl???

desktop:~$ compiz
Checking for Xgl: not present. 
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): Operation not permitted
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x720) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
captain@captain-desktop:~$

---

### Post by rakan21 on 2008-11-30
Make sure your not using VMWare Fusion or Parallels. you can't run any of the graphic effects through virtual machines.

---

