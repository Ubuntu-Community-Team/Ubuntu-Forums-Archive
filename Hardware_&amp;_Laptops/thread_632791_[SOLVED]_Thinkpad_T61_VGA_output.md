---
title: "[SOLVED] Thinkpad T61 VGA output"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by hvac3901 on 2007-12-05
Has anyone made this work, my VGA output is not working with the factory hotkey.

I have found some information but it reads in a language i am not familiar with :P

Does anyone have better information or links available for setting this function up?

---

### Post by victorgreen on 2007-12-07
The hotkeys are shot. To get gutsy to connect to an external monitor or projector I have to  plug it in and restart. Other people with these machines have reported that they can simply cntrl alt backspace to kill and restart x to get the external working, but that doesnt work for me for whatever reason.

---

### Post by hvac3901 on 2007-12-07
he he, i wish i could get a restart to do it for me, I am completely dead in the water. and to be quite honest, i tried some disastrous attempts to modify my xorg.conf file, with horrible results. 

So hence my reason for posting. this. gonna send a long and nasty letter to IBM about poorly supporting my OS of choice. HAHAHA i love sending those emails it like a sport for me.

---

### Post by hvac3901 on 2007-12-10
anyone else have some experience?? bump.

---

### Post by nguyenx86 on 2007-12-10
My Acer-5104's VGA output and hotkey only work outside Ubuntu (in flash screen mode).
You can try: Go to System -> Administration -> Display ..... (I've forgot) and enable 2nd monitor (projector), then disable your laptop's LCD, set resolution you want, restart X server.
I don't know why I must disable the LCD for the VGA output working, but when my main display is active, I can't do anything to enable the 2nd.

---

### Post by arajeev1 on 2007-12-13
hvac3901:

I had a similar problem.  I've got a T61 running Gutsy with a Lenovo D221 Wide monitor connected.  I'm using the Nvidia restricted drivers.  Here's the procedure I used:

   1. Connect the external monitor to the laptop
   2. Open up a terminal and run "nvidia-settings &" at the prompt *as root*. This is a configuration program from the package "nvidia-glx-new" (I think it gets installed when you install the restricted nvidia drivers, but not sure).
   3. Within nvidia-settings, select "X Server Display Information". It should show two monitors in a little box called "Layout". The external monitor may be disabled.
   4. Click on the external monitor's icon, then click "Configure", then select "Separate X Screen".
   5. Click on the laptop screen's icon (which is probably enabled), then click "Configure", then select "Disabled".
   6. Note: This step will overwrite the X Confuration File (usually /etc/X11/xorg.conf). You may first want to backup that file to something like xorg.conf.bak.01. When you've backed it up, click "Save to X Configuration File".

Hope that helps.  I don't know how to easily switch between external monitor and T61 screen, though.

PS.  You have to restart X after step 6.

---

### Post by hvac3901 on 2008-06-20
This problem was fixed with HERON. Works like a champ.

---

