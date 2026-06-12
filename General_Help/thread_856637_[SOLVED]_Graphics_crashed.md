---
title: "[SOLVED] Graphics crashed"
date: 2008-07-11
forum: General Help
---

### Post by Paul T. on 2008-07-11
After trying to update graphics driver and restarting system, I can only get black screen with command prompt, says something about updating x org config file manually which is way beyond my ability being a newbie to Linux. 
Is there some sort of rescue disk I can create, or an online tutorial I can follow to restore Ubuntu?

---

### Post by danwood76 on 2008-07-11
What drivers were you trying to install and what graphics card do you have?

Also what steps have you taken to install the drivers?

---

### Post by Paul T. on 2008-07-11
I'm using Nvidia card FX5200 chipset. I came across a prog on synaptic manager that installed driver automatically, it appeared to be successful until I restarted system.

---

### Post by Ataris on 2008-07-11
You are facing a similar problem that I experience just yesterday, and am posting everywhere I can about it. I would try rebooting or entering ```
sudo dpkg-reconfigure xserver-xorg
```

Look at this thread for more info: 

[http://ubuntuforums.org/showthread.php?t=856542]("http://ubuntuforums.org/showthread.php?t=856542")

---

### Post by danwood76 on 2008-07-11
There are two main versions of the nvidia driver for linux.
The best way to install the proprietry drivers is through the 'Hardware Drivers' control panel and it does the configuration for you.

If the command suggested by Ataris doesnt work then you will need to change the xorg driver to the 'nv' (open source) driver to get the GUI back.

Basically boot up in recovery mode and edit the xorg config file
```

nano /etc/X11/xorg.conf

```
look through this file and wherever it says 'nvidia' replace with 'nv' then save the file (ctrl+o) and exit (ctrl+x) then to restart do:
```

reboot

```
When you restart you should have a GUI back, then you can install the proprietry drivers through the 'Hardware Drivers' control panel.

---

### Post by Paul T. on 2008-07-11
Thx Ataris & Danwood76, I printed out your instructions and re-booted into Ubuntu, from the menu I chose recovery mode, then from next menu there was an option to automatically re-configure x org file. I selected this and it worked!! 
The reason I initially updated graphics driver was because of refresh rate, I could run at 1024 x 728 but only at 58 hz, which gave a flickering screen, I'm now running at 85 hz which is perfect! Long live Ubuntu =D>

Btw, the prog I initially used to update graphics driver was EnvyNG

---

### Post by Ataris on 2008-07-13
I haven't ever used Envy, and have always thought that using a script for updating drivers when I didn't even understand the script was a bad idea. People should update their drivers manually or risk screwing things up. I already have manually. Hey. Linux drivers are weird.

---

### Post by danwood76 on 2008-07-14
Every time I used envy it screwed up my drivers.
I always do a manual install now, helps you to learn ;)

Well done for getting it going.

---

