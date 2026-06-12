---
title: "[SOLVED] Resolution with 8600GT"
date: 2008-07-14
forum: General Help
---

### Post by leveliv on 2008-07-14
Alright I tried searching for anything to fix my Resolution ...even 1024x768 would be nice...but all I can get is 640x480 with the nvidia drivers on...and without them on I can get 800x600. I tried using EnvyNG..same thing happens there...Also now after using NG, whenever I check the drivers box in the restricted drivers dialogue and reboot a box comes up saying it has to run in low graphics mode..but if I install the drivers with Envy it works fine..just a HUGE resolution. Also my monitor isn't ever found by either. I have a Samsung Syncmaster 950p with an 8600GT What do I do...?? Thanks in advance, I hope.:mad:

---

### Post by Afkpuz on 2008-07-15
When that dialog comes up that says "low graphics mode", click configure and try to set the res manually.  You'll need to make sure the nvidia driver is in use(can be done through that configuration dialog) and pick a monitor that matches your resolution.

That area is called "screens and graphics" and you can get there without going through the reboot process.  

Right lick on "Applications".  Then "Edit Menus" Click "Other", then check "screens and graphics".  then, select it in Applications>Other

---

### Post by jonian_g on 2008-07-15
You might try this:

Remove the driver with EnvyNG

Open synaptic and completely remove everything that starts with nvidia-glx-*

Delete your xorg.conf file located at /etc/X11

Reboot and install the driver with EnvyNG.

Install nvidia-settings (if not installed) and go to System>Admin>NVIDIA X Server Settings to set your resolution (Press "save to X configuration file" to save your settings).

---

### Post by jonian_g on 2008-07-15
To make it recognize your monitor model open a terminal and type

sudo displayconfig-gtk

Click where it says "Model" and at the screen that comes up click add and locate the *.inf file in the cd-rom that came with your monitor. Then select you monitor model and press ok.

Don't set your resolution from here. Better do it from nvidia-settings.

---

### Post by leveliv on 2008-07-15
Alright heres what I did to get it working..

Reinstalled Ubuntu 8.04 (just for a clean slate)
Changed my monitor to LCD 1280x1024 in SCreens and Graphics then I clicked enable on the restricted drivers. Restarted and Ta Da!! It works.

---

### Post by Afkpuz on 2008-07-15
Glad to hear it.  Also, you should mark this thread as solved in the thread tools drop down box

---

