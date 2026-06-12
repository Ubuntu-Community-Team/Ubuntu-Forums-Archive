---
title: "Can't Change Resolution"
date: 2008-09-07
forum: General Help
---

### Post by Vince4Amy on 2008-09-07
This is mainly a problem when using Kubuntu with KDE 3.5.x. I can't change my monitors resolution or refresh via Kcontrol because that reports something completely different to my xorg.  

I also cannot find any way to edit xorg because everything seems to be autoconfigured, for example there's no mode lines or anything.

Ask if you need more information but it's hard to explain.

---

### Post by wolfen69 on 2008-09-07
2 things you can try: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and ```
sudo displayconfig-gtk
``` do ctrl-alt-bksp after trying each.

---

### Post by Neo_The_User on 2008-09-07
What I do is install the drivers for the GPU I am using. For example, I have an ati card. I go to [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and pick what I have there. I do sudo chmod +x and drag the driver into the terminal. sudo (drag file) and hit enter. I follow the instructions and reboot. I recommend installing the accelerated drivers first because the Catalyst Control Center won't load. I think you would be much more satisfied with the drivers rather than reconfiguring your x server. nVIDIA has drivers as well but I had an nVIDIA card when I used to have 7.04 with Envy so I have no idea what it would be like to download the drivers from the nvidia website with 8.04.

nVIDIA drivers: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by Vince4Amy on 2008-09-07
I don't think that Reconfiguring X is going to do a thing. It's definitely a problem at the Desktop Environment end. I know this because:

In Gnome My Monitor is Set to 1280x1024 and Displayed as This.
In KDE4 My Monitor is Set to 1280x1024 and Displayed as This.
In KDE3 My Monitor is Set to 1280x1024 but displayed as 640x480 in kcontrol and all other Screen resolution applications apart from Catalyst Control Centre.

---

### Post by Vince4Amy on 2008-10-05
Bump: I still have not found a solution to this, and I cannot edit xorg because it seems to have auto configured everything. It is definitely a problem with KDE 3 however as the other DEs have no problem with this.

---

### Post by tonybaqain on 2008-10-05
please paste your /etc/X11/xorg.conf contents here.

---

### Post by Vince4Amy on 2008-10-05
I don't have access to the machine right now but I know posting that will not help, everything is auto configured.

---

### Post by tonybaqain on 2008-10-05
that's allright friend, i tried to help you, hope you find your way out of it.

---

### Post by Vince4Amy on 2008-10-06
I know you did and I know for a fact the problem does not lie within xorg. I was merely stating it so that you did not waste your time trying to help troubleshoot, the problem is definately with the KDE3 Control Centre.

---

### Post by Zimmer on 2008-10-06
Have you investigated the xorg.log to see what X is doing?
[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)

X is now trying to detect and configure more stuff automatically and works in a slightly different way to how it did when I was using 6.06.

There is more reliance on the EDID data from your monitor.
It may not be detecting your monitor correctly.
See what the log tells you.

---

