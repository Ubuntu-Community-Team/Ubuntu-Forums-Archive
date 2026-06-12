---
title: "Audio through HDMI"
date: 2015-01-24
forum: Hardware
---

### Post by Trevas on 2015-01-24
I have a question about NVidia drivers. I have an ASUS N76V laptop. It has Intel and Gefore 635M graphics cards. When I hook the laptop to HDMI with Windows I am able to play the sound through the HDMI (ie the 52" TV the computer is connected to). I know that this is accomplished with the Windows NVidia driver and not the sound card because I had to set it up that way in Windows. Since the same options are not available in the NVidia linux control panel, is there a way that I can get sound through the TV from Linux?

---

### Post by SeijiSensei on 2015-01-25
Try installing **pavucontrol** from the repositories.  It should show you both audio outputs and let you choose between them.  In KDE I use plasma-widget-veromix which replaces the default mixer app.  I believe you can install [**Veromix**]("http://code.google.com/p/veromix-plasmoid/") on GTK systems like standard Ubuntu with "sudo apt-get veromix" as well, but I haven't tried that.

---

