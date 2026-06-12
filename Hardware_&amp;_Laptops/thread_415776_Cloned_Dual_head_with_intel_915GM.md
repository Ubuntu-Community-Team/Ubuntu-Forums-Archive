---
title: "Cloned Dual head with intel 915GM"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by surhudm on 2007-04-20
Hi,

I was able to configure dual head on Ubuntu Feisty on Acer Extensa with a Dell monitor that supports 1280x1024@60Hz.

Here is a howto:
1. Make a backup of your xorg.conf and then open up xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X111/xorg.conf.bak
```
```
 gksudo gedit /etc/X11/xorg.conf 
```

2.Go to Section Device and add the following lines after **Driver i810**
```
       
        Option  "VBERestore" "yes"
        Option  "Clone" "true"
        Option  "MonitorLayout" "CRT,LFP"
        Option  "DevicePresence" "yes"
 
```

3. Go to the Screen section and in the Subsection Display for the default depth (usually 24 ) add the following line after **Modes           "1280x800"**
```
  
         Virtual         1280 1024

```

4. Save the file. And logout of your system. You should restart your gdm/kdm for the new settings to take effect. For this press Ctrl-Alt-F1 and login with your username password. Then
```

sudo /etc/init.d/gdm/start
OR
sudo /etc/init.d/kdm start

```

Hopefully if everything worked fine then your laptop display will have a virtual mode of 1280 1024 and your external display will be running...

Here are the sections that have to be modified once again:
```

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
#Added for the dual mode.
        Option  "VBERestore" "yes"
        Option  "Clone" "true"
        Option  "MonitorLayout" "CRT,LFP"
        Option  "DevicePresence" "yes"
#
        BusID           "PCI:0:2:0"
EndSection

```

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
                Virtual         1280 1024
        EndSubSection
EndSection

```

If your xserver fails or you do not want the dual mode, restore the backup file:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X111/xorg.conf 
```

Enjoy the Fawn...

---

### Post by bratgitarre on 2007-04-20
Is your external monitor a CRT or a TFT?

---

### Post by surhudm on 2007-04-20
It is a TFT. But it worked with CRT, I am not sure if there is also a TFT option.

---

