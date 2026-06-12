---
title: "Monitor Resolution"
date: 2008-08-13
forum: Hardware
---

### Post by mercules2178 on 2008-08-13
Ok, I have been having trouble with this for a couple of weeks now. I have an 8500gt card and a dell 20 inch e207wfp. After the install of nvidia drivers ubuntu sets my screen resolution to 800x600@73 and it should be 1680x1050@60. Each time I reboot I end up with a low graphics mode box. I would like to have the correct resolution. I have completely removed all nvidia drivers and would like some help with the reinstall. Not too sure about which are the correct drivers and will need help with the screen resolution problem. Thanks!!!!!

---

### Post by cowsled on 2008-08-13
Try the following in terminal:
sudo apt-get install envyng-gtk
then:
sudo envyng-gtk

When EnvyNG pops up, select NVIDIA on the left panel and select "Install the NVIDIA driver (Automatic Hardware Detection)".

Hit Apply.

There is no loading screen for it so just be patient. EnvyNG will let you know when its done. You'll need to reboot.

This worked fine for my 8800GT so I hope it works for you too. ^^

---

### Post by mercules2178 on 2008-08-13
I have tried with envy also. I really do believe that once the driver is installed that it does not understand that my monitor does not support the resolution it is trying to use at start up and it puts itself into hibernation.

---

