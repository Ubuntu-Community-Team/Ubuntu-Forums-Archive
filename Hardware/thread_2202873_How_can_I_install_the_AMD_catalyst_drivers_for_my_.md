---
title: "How can I install the AMD catalyst drivers for my r9 270's?"
date: 2014-01-31
forum: Hardware
---

### Post by mattcallaway1406 on 2014-01-31
Hey, Over the last few days I've been scouring the internet trying to find how I can get my new mining rig up and running - so far Xubuntu is the OS I've had the most luck with. Everything seems to be working. All the guides I've been following have told me to install the AMD catalyst drivers - So I've been doing this:
```
[FONT=Consolas]sudo apt-get install fglrx-[/FONT][FONT=Consolas]**updates**[/FONT][FONT=Consolas] fglrx-amdcccle-updates fglrx-updates-dev[/FONT]
```
And it appears to install. However, when rebooting my system it brings up the xubuntu loading screen and then I just see a black screen with a little white square in the top left (kind of looks like a cursor you'd see in a command prompt) and a big AMD unsupported Hardware logo in the bottom left. I 've seen some people who say this is just a watermark however for me - my system is completely unusable with just a black screen showing. The only way to get out of this is to press Ctrl + Alt + F1 and shut down the machine!

i have a 2 MSI R9 270's  and I'm using Xubuntu 12.04 - Is there anybody who knows how to get the drivers for these cards installed? As I assume I do need them for mining! If this isn't possible - does anyone know of a linux distro that supports the r9 270 and the realtek RTL8188CUS wifi usb dongle? Because the distros that are meant for mining (BAMT / SMOS) don't support my wifi dongle.

Any help would be greatly appreciated! I'm starting to get desperate I've been working on this rig for so long!

---

### Post by slooksterpsv on 2014-01-31
You can try downloading and installing the latest drivers from AMD I'm not sure if the fglrx-updates has the latest for the R9 series. If it does you can try to run the following commands to get back into the GUI:

```

sudo aticonfig --initial

```

Restart.

If that doesn't work here's a temporary solution to get you in:

```

sudo Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

```

Restart

---

### Post by Bucky Ball on 2014-01-31
Welcome. Once back at a desktop, do an update, check Additional Drivers.

---

