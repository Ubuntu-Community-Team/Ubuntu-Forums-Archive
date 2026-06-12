---
title: "NVIDIA resolution gets reset"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by tit4tat on 2009-06-11
Hello, 

Videocard resolution does not get saved on my 9.04 system when I restart. 

I go to NVIDIA X Server Settings and pick the resolution. I click Apply and everything works great until next restart when it resets to 800x600. The ideal resolution for my laptop is 1280x800. 

If I click Save to X Configuration file, it says "Failed to parse existing X config file '/etc/X11/xorg.conf'!"
 
I'm using Driver Version 180.44 and I have the same problem in a desktop running Xubuntu. 

This is what I have on the xorg.conf file:
```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection



```

I tried to use Modeline tool but no 1280x800 resolution is provide as an option.

Thank you in advance for your help.

---

### Post by kzersatz on 2009-06-11
I had a similar issue with Nvidia xserver settings awhile back with a different video card

my solution consisted in changing the read/write settings on the xorg.conf file located within /etc/X11/

you do this by the command chmod
Your best bet is to set it so root can make changes to the file, if you check the properties through the GUI for permissions, you may note that nobody has permissions to do anything to the file but "read"

Sorry I cannot give the exact chmod command line you would need to run, the last time I did it was 4 months ago and it was all hazy to me then too

Good luck! :D

---

### Post by tohnster on 2009-06-11
Problem solved for me after reading this. I tried sudo chmod +xw xorg.conf and it seemed to work perfectly. Settings now save w\o a hitch!:D

---

### Post by kzersatz on 2009-06-11
> **tohnster said:**
> Problem solved for me after reading this. I tried sudo chmod +xw xorg.conf and it seemed to work perfectly. Settings now save w\o a hitch!:D

Woot!

Way to go for following vague instructions haha ;)

---

### Post by tit4tat on 2009-08-02
Well I followed those instructions and it doesn't work for me. I get Failed to parse existing X config file /etc/X11/xorg.conf

Same thing with the desktop which also has an nVidia card. 

Anyone else has an idea?

---

### Post by carldon on 2009-09-19
Hi,  I have a nvidia 6600 GT with a Dell 2007 FPW and had the same issue. The resolution would default to 800X600 everytime I restarted.   Here are the things that did not work for me,  1. Used root user to change save xorg.conf file 2. Changed resolution with the default display manager rather than nvidia settings manager  What worked for me,  - Looking through the xorg.conf file, the vertical refresh rate for the monitor was higher than specified. (56 - 76 hz was specified) The monitor could handle 1680X1050 at 60 hz. I changed the vertrefresh from 56.0 - 76.0 to what is below.          

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection


Hope this helps.  Arun

---

### Post by Jimmyfj on 2009-09-19
Back on my old CTR monitor I had that same issue of resolution defaulting to 800x600. The method that worked in my case was: In a terminal type:

```
sudo nvidia-settings
```

Once in the setting-manager I chose the resolution I wanted, 1280x1024x60 and hit the "Save to xserver.conf file" ( or some thing lige that). Never had any issues after that.

---

### Post by Laibcoms on 2009-10-07
If this will help for Karmic users (like me), this method worked -> [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6933051&postcount=4](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6933051&postcount=4)

---

