---
title: "Compiz error: Checking for Xgl: not present, no whitelist driver..."
date: 2008-08-30
forum: General Help
---

### Post by nouseforaname7 on 2008-08-30
When I type 'Compiz' into the terminal I get this...

zak12345@Z:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by myidisvoid on 2008-12-10
If you are using 64 bit installation and compiz-check showing all ok, you may want to check the /usr/bin/compiz  to make sure

XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"
is changed to 
XORG_DRIVER_PATH="/usr/lib64/xorg/modules/drivers/+"

So, it can find the driver correctly based on Xorg.0.log.

Cheers,
Void

---

### Post by ellalan on 2008-12-11
> **nouseforaname7 said:**
> When I type 'Compiz' into the terminal I get this...

zak12345@Z:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
You are OK to run Compiz, do not worry about these warnings and I can assure you it shows up in my system as well but I have compiz working perfectly.
In synaptics tick the following for installation:
compiz-configuration-setting-manager
simple ccsm
fusion-icon
Abd see whether you have compiz config settings manager under system->preferences.
HTH.

---

