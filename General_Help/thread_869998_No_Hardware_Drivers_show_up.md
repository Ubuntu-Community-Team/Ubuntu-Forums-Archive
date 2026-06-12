---
title: "No Hardware Drivers show up"
date: 2008-07-25
forum: General Help
---

### Post by jamh.unm on 2008-07-25
I seem to be having a problem with my system recognizing my graphics card, when I open up Hardware Drivers, it gives me an empty list and says "No proprietary drivers are in use on this system."  I'm trying to enable my Desktop Effects from compiz but am failing miserably, any help would be appreciated.  I know it can work because I have got it to work earlier, but that was on a previous install.

Kubuntu Hardy Heron 8.04.1
Nvidia 8800 GTX with driver 173.04.05 installed (latest off of Nvidia site)

---

### Post by psyopper on 2008-07-25
What the "Hardware Drivers" app is saying is that you haven't installed any of the drivers from Ubuntu's restricted repository.

What happens if you type "compiz -- replace" in a terminal? Please post the output here. Also, please post a copy of your /etc/X11/xorg.conf and lastly, download and run the [compiz-check script]("http://forlong.blogage.de/article/pages/Compiz-Check") and post the results here

---

### Post by InfSauce on 2008-09-22
Hello, I'm having a similar problem, (amongst many others)... I supposedly installed the nvidia drivers for the 9600 Gt graphics card, everything appears to be working (sort of). But when I look in the Hardware Drivers, the list is empty... These are the results I got after running the "compiz -- replace" command..

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3360x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

