---
title: "Installing NVIDIA GeForce 6200 Tubrocache Video Card"
date: 2008-10-16
forum: Hardware
---

### Post by matt2369 on 2008-10-16
I've been attempting to install the drivers for my NVIDIA GeForce 6200 Turbocache video card and I just cannot get it to work.

First I Ctrl+Alt+F1 to get into the terminal from X.

Then I stop X by /ect/init.d/gdm stop

Then i log in as root by sudo su

Then I install the driver and it goes fine.  I automatically had the config file edited by the installer.  

Everything appeared to go fine.  It spit me back into the terminal after the installation completed.

Then I didn't really know what to do.  I restarted X and still no video card.

Would appreciate any help!

---

### Post by jerome1232 on 2008-10-16
I would try reconfiguring x.

```
sudo nvidia-xconfig
```

If it's not installed then install it
```
sudo apt-get install nvidia-xconfig
```

If you are desperate to get back to a gui you can uninstall the driver
```
./NVIDIA*.run --uninstall
dpkg --reconfigure -phigh xserver-xorg
```

Just curious have you tried the easier way's to install the nvidia driver? a 6 series card ought to be supported by nvidia-glx-new.

---

### Post by matt2369 on 2008-10-16
Thank-you jerome1232, somehow by starting over and using you tip I got the card to work.  But...Now when I boot up my machine the resolution settings are still stuck at the 800x600 and not what I want it to be.  When I try to save the X configuration file after I change the resolution it gives me an error "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

I tried saving it through terminal by 

sudo nvidia-settings

Which opened up the NVIDIA settings and I didn't get an error when saving the X config file. But still when I boot up the resolution is still at 800x600.

Any Help?

---

### Post by jerome1232 on 2008-10-16
Yeah that utility doesn't save the file right for some reason, as a workaround I just click save to x configuration file, then click show preview.

Open a new terminal and backup your old configuration, then open the file for editing, delete everything in the xorg.conf and copy that preview over.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
gksu gedit /etc/X11/xorg.conf
```

edit: For some reason I didn't read your later post :), Let me mow over my xorg.conf and see if I can find anything to help you.

---

