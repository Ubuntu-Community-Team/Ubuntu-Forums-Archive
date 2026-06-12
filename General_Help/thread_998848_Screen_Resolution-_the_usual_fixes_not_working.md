---
title: "Screen Resolution- the usual fixes not working"
date: 2008-12-01
forum: General Help
---

### Post by Belbarid on 2008-12-01
My parents just installed Ubuntu on one of their computers, and are having a problem with the screen resolution being maxed at 800x600.  So they called me and I did some basic research.

What I have done:
Enabled nVidia 3rd party drivers- the computer has on board video using an nVidia chipset.

sudo dpkg-reconfigure xserver-xorg.  I read that part of the reconfigure should be the ability to choose a default screen resolution, but I did not get that option.

Manually editing xorg.conf

None of this has allowed me to get a higher screen resolution than 800x600. I've run out of things to try and places to look for the solution.  What sort of things should I be looking at now?  

They are running Kubuntu 8.10, but also had this problem with Ubuntu 8.10.  I switched them to Kubuntu because that's what I run, and it's easier to do over the phone tech support when we're running the same version.

*Any* help would be greatly appreciated

---

### Post by Fire_Chief on 2008-12-01
Have you tried using the Nvidia control panel (System -> Administration -> Nvidia X Settings) to set the resolution? This should also allow you to save the new settings to the xorg.conf file.

Also, some monitors have trouble displaying higher resolutions by default because Ubuntu is not using the correct vertical and horizontal frequency settings. I have a monitor at home like this and it's a pain. But once it is set, it works like a champ. Might want to make sure the settings (if configured) for the monitor are correct in the xorg.conf as well.

Cheers!

---

### Post by Belbarid on 2008-12-01
> **Fire_Chief said:**
> Have you tried using the Nvidia control panel (System -> Administration -> Nvidia X Settings) to set the resolution? This should also allow you to save the new settings to the xorg.conf file.


Nerts- I knew I was forgetting something.  Yes- I tried that.  No effect.

> **Fire_Chief said:**
> Also, some monitors have trouble displaying higher resolutions by default because Ubuntu is not using the correct vertical and horizontal frequency settings. I have a monitor at home like this and it's a pain. But once it is set, it works like a champ. Might want to make sure the settings (if configured) for the monitor are correct in the xorg.conf as well.

Cheers!

Thanks- I'll start looking into that.

I'm sure that something like this exists, but I wasn't able to find it.  Can someone point me to a guide for editing the xorg.conf?

---

### Post by Fire_Chief on 2008-12-01
Here is a sample Monitor section.

```
Section "Monitor"
	Identifier	"PL201M"
	Option		"DPMS"
	HorizSync	30-94
	VertRefresh	50-85
EndSection

```

For your specific monitor model, lookup the ranges from the specs listed in the manual or online and then put them here. Save the config and then reboot.

Cheers!

---

### Post by LeslieL on 2008-12-01
I'm feeling really dumb, because I had exactly the same problem about a month ago and solved it but now can't remember what I did! I know it involved downloading and using Envy-NG to get my System > Administration > NVIDIA X Server Settings working usefully. I found the answer on this board, I know - try searching for Envy and see what comes up. 
Even now, though, the screen resolution is still a little low when I start up. But now I can go into NVIDIA X Server Settings and fix it. 

Just for interest, my current Xorg.conf file has this in it:
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7150M / nForce 630M"
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "TV: 1024x768 +0+0, DFP: 1280x800 +0+0"
# Removed Option "metamodes" "1280x800 +0+0"
# Removed Option "metamodes" "DFP: 1280x800 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Hope this helps.

---

### Post by Fire_Chief on 2008-12-01
Silly me...I forgot about EnvyNG. That is a great app for handling the drivers and (sometimes) resolutions stuff. I've read that it makes additional changes that work better than just using the Nvidia driver installer alone. Note I have not confirmed this but many many people report good success via this method.

---

### Post by STUMPOFWAR on 2009-02-24
I can't get Nvidia X server to save the settings. Everytime I reboot I have to go back into X server and change the resolution to "auto" or "1280 by 800".

When I try to save the setting I get the error:
When I go to save the setting I get the following error

```
Failed to parse existing x config file '/etc/x11/xorg.conf'
```

and when I click OK and try to save the back-up I get

```
"unable to create new x config backup file '/etc/x11/xorg.conf'
```

It is really annoying. I started using KDE and XFCE boot with full resolution. This only happens in Gnome. 


Any thoughts on what I should do?

---

### Post by LeslieL on 2009-02-24
I had that problem too. That and a whole bunch of other things (like wanting to get rid of the Vista I was dual-booting to) made me reformat the disk and reinstall 8.04. After a huge update (it was an old disk I installed from) everything works fine. 
A drastic solution, but that's what it took for me.

---

