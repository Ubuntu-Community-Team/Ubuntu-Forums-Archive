---
title: "Compiz-Check results...."
date: 2008-10-01
forum: General Help
---

### Post by RickDJ on 2008-10-01
studio@studio-desktop:~$ sudo compiz check
[sudo] password for studio: 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'check'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Plugin 'mousepoll' not loaded.

/usr/bin/compiz.real (ezoom) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ezoom'

Graphics processor: GeForce 6600 128MB 

Is this card good enough...?
Thanx

---

### Post by knix on 2008-10-06
definitely good enough. It's been run on Intel graphics and geforce 2s.
Take a look at this thread.[http://ubuntuforums.org/showthread.php?t=936386&highlight=software+rasterizer]("http://ubuntuforums.org/showthread.php?t=936386&highlight=software+rasterizer")

---

