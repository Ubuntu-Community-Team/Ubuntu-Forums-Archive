---
title: "Can't save changed Nvidia settings?"
date: 2009-11-21
forum: Hardware
---

### Post by Ironhorse_somo on 2009-11-21
I have the 3rd party drivers installed for my Nvidia 8800 video card. Every time the system starts up, it sets the resolution on my monitor to 1280x1024, making everything TINY. I have to manually set it to 1024x768 (my preferred setting) and if I try to save that setting, I get this error message:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

I'm using Ubuntu 9.10 (Karmic) 64 bit edition.

Help?

---

### Post by realzippy on 2009-11-21
Log out,press alt+ctrl+F1

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig

alt+ctrl+F7,login

gksudo nvidia-settings

Hit "Save To X Configuration File" button...

---

