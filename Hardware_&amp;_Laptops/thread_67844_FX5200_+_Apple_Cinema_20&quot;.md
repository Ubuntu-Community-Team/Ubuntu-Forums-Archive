---
title: "FX5200 + Apple Cinema 20&quot;"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by persis on 2005-09-21
Just popped a FX 5200 video card / DVI in so I could interface with my long awaited arrival of the Cinema 20".  Of course - on bootup I wasn't able to load X Gui and was taken to the command line.  I suppose I need to install the nvidia drivers and then possible do some other tweaking.  Haven't found many resources here regarding the Apple Cinemas with non-macs (I'm running Pentium 4)

Anyone willing to lend a hand, or maybe even a leg...?

thanks -

---

### Post by persis on 2005-09-21
[B]I did the following to try and install the NVIDIA drivers:
[/B]

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

[B]
However, when I get to the command "sudo nvidia-glx-config enable"[/B] it gives me an error:

"Error: you X configuration has been altered.  This script cannot proceed automatically.  If you believe that this is not correct, you can update the md5sum entry executing the following command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum otherwise edit manually /etc/X11/xorg.conf to change the Driver section from nv to nvidia."


Anyone have a clue as to how I should go about getting the driver going to I can see some beauty - and perhaps even share the beauty ;)

---

