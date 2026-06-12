---
title: "Compiz segmentation fault"
date: 2008-11-22
forum: General Help
---

### Post by dpm_edinburgh on 2008-11-22
I have a problem with the very latest version of Compiz (0.7.8) which only seems to have started happening since I updated a few days ago.  Compiz will start fine, but then after a few minutes will quit, and I'll be left with just the plain Gnome window decoration.

Running compiz from the command line, I get the following output:

> 
dpm@dpm-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz.real (group) - Warn: No compatible text plugin loaded.
/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz.real (scaleaddon) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz.real (scalefilter) - Warn: No compatible text plugin found.
Segmentation fault
/home/dpm/.themes/Gilouche/gtk-2.0/gtkrc:42: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dpm/.themes/Gilouche/gtk-2.0/gtkrc:43: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dpm/.themes/Gilouche/gtk-2.0/gtkrc:44: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.


I have an nVidia graphics card in a HP dv6000 series laptop, running Intrepid.  FWIW, the problem seems to coincide with me clicking my mouse in the border of a window.

Can anybody help?

---

### Post by shadowdude1794 on 2008-11-22
This exact thing is happening to me, after updating to the new version. Clicking on the borders causes compiz to crash every time.

---

### Post by damis648 on 2008-11-23
+1, but for me it is random and happens just when clicking on a black space in a window. Any ideas?

EDIT: Running compiz 0.7.8, from the PPA repositories.

---

### Post by damis648 on 2008-11-23
Is anybody else here running compiz updated from the PPA repos? Is there a fix or do we just have to wait for an update?

---

### Post by binbash on 2008-11-23
At the moment i am not on my ubuntu box but last time i used 0.7.8 from ppas it WAS working fine.But this line causes compiz to crash : 

/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

I guess there is a problem with plugins package or configuration.Did you try to purge all compiz ppas and re-install?

---

### Post by mattgif on 2008-11-23
Just wanted to add my name to the list of people with Compiz problems after the PPA update.  Getting the same problem with segmentation fault; for me it's when I click both mouse buttons at once on the desktop (to "grab" it and spin the cube).

nVidia 8800 gt graphics card, v. 177 drivers.

---

### Post by damis648 on 2008-11-23
> **binbash said:**
> At the moment i am not on my ubuntu box but last time i used 0.7.8 from ppas it WAS working fine.But this line causes compiz to crash : 

/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

I guess there is a problem with plugins package or configuration.Did you try to purge all compiz ppas and re-install?

Good call - I purged ALL things compiz, disabled the PPAs, updated sources, and re-installed everything from the Ubuntu repos. :guitar:
List of packages purged and reinstalled (NOT FROM PPAs!):
```
compiz
compiz-core
compiz-dev
compiz-fusion-bcop
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compiz-wrapper
compizconfig-backend-gconf
compizconfig-settings-manager
emerald
```

python-compizconfig (0.7.8-0ubuntu1)
> **mattgif said:**
> Just wanted to add my name to the list of people with Compiz problems after the PPA update.  Getting the same problem with segmentation fault; for me it's when I click both mouse buttons at once on the desktop (to "grab" it and spin the cube).

nVidia 8800 gt graphics card, v. 177 drivers.

Yes, it seems it is for different reasons for different people. My compiz segfault output says nothing about the font plugin...

---

### Post by mormor on 2008-11-23
Same problem here. Acer Travelmate 6291. Happened after last compi* update. Hoping for a fix pretty soon: )

---

### Post by damis648 on 2008-11-23
See post above: Purge all compiz packages, disable PPAs, reinstall.

---

### Post by mormor on 2008-11-23
I dont know how to purge anything : ( or disable ppas.

---

### Post by damis648 on 2008-11-23
like so:
```
sudo apt-get --purge compiz compiz-core compiz-dev compiz-fusion-bcop compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf compizconfig-settings-manager emerald
```

Then, after disabling the PPAs, just reinstall:
```
sudo apt-get install compiz compiz-core compiz-dev compiz-fusion-bcop compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf compizconfig-settings-manager emerald
```

---

### Post by loomsen on 2008-11-23
Or check out one possible (probable) solution for this by clicking the link in my sig... (Majority won't have enabled the repos anyway, and if they might probably already have taken this into consideration...)

I've got git-compiz running fine.

---

### Post by stormtrooprdave on 2008-11-26
If I purge all things compiz will I lose all my settings and emerald themes?

---

