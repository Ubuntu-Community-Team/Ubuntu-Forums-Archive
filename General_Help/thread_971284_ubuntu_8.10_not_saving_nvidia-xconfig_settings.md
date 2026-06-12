---
title: "ubuntu 8.10 not saving nvidia-xconfig settings"
date: 2008-11-04
forum: General Help
---

### Post by infiniah on 2008-11-04
hello i run dual screen one in 1280x1024 and the other in 1024x768.

i have a nvidia geforce 9600 GT and when i set my settings up and click save or what ever its called, i restart and my settings have not changed and its back to 1024x768 on the bigger screen and the other screen, the smaller one, is disabled. so i have to go back into nvidia settings and set it back up constantly after every restart. i like to keep my computer off when i am not on it to save power so you can see how this could annoy one.

---

### Post by infiniah on 2008-11-04
any help?

---

### Post by infiniah on 2008-11-04
hmm cant seem to find the problem... im not that good with ubuntu as it is...

anyone.........?

---

### Post by pirattrev on 2008-11-04
maybe after setting the new setup you should restart the xserver or logout then back in.  what are you using exactly to setup the screens?

---

### Post by infiniah on 2008-11-04
i have restarted the x server many times,
i am using the nvidia settings manager i think its called

---

### Post by pissedoffdude on 2008-11-04
Open up a terminal and type ```
gksudo nvidia-settings
```
Then edit the settings to what you want, hit apply, and click save to x configuration file.  This should keep your settings even after rebooting.

---

### Post by tilapia on 2008-11-05
I have the same problem. Running gksudo nvidia-settings does allow you to save the config file. However, when you reboot it defaults back to a low resolution.

---

### Post by Woody1987 on 2008-11-05
try typing
```
sudo nvidia-xconfig
```
then run nvidia-settings

---

### Post by TeXtonyx on 2008-11-05
I think the problem may be the nVidia driver isn't persisting. Try
making an xorg.conf with nvidia-settings and keep it safe, making
sure it saved. I copied everything and pasted it into another file
which became xorg.conf. Then used Envyng to establish the driver. 

Also the 8.10 release notes say:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade.

------------------------------------

My working xorg.conf for 8.04 has an entry for the driver 'nvidia'

---

### Post by bribera on 2008-11-05
I had the same issue with Xubuntu 8.10. The issue was that the settings program needed root privileges to write to xorg.conf.

Additionally, the default setting of this program is to merge your existing xorg.conf with the new settings. This may produce conflicting "screen" sections; I manually edited my xorg.conf file after the merge and deleted the old default screen section.

I also added the nonlogo = true setting to the nvidia-generated section, since it was omitted.

Hope that helps!

---

### Post by freescuba on 2009-01-11
I had a problem with nvidia-settings values not persisting as well.  Turned out I needed to uncheck 'include X display names' in the nvidia-settings Configuration in the GUI.  

By having that on it generated some crap at the beginning of each line which caused it to break on startup.  

Once I unchecked that and saved (Quit) all was wonderful.  (remember to add "nvidia-settings -l" as part of your session start as well.

Thanks to those that found this solution here: [http://ubuntuforums.org/showthread.php?t=778260](http://ubuntuforums.org/showthread.php?t=778260)

---

