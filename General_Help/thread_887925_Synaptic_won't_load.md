---
title: "Synaptic won't load"
date: 2008-08-12
forum: General Help
---

### Post by smmalis on 2008-08-12
When starting Synaptic (or aptitude) I get the following error message:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
So i run the command and get this output:
```
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24.3-steven
Cannot find /lib/modules/2.6.24.3-steven
update-initramfs: failed for /boot/initrd.img-2.6.24.3-steven
dpkg: subprocess post-installation script returned error exit status 1
```

Seems like there are some remnants of my custom kernel (which I thought I uninstalled and no longer use), but I can't figure out how to get rid of it.

---

### Post by Crafty Kisses on 2008-08-12
What happens if you run Synaptic through the Terminal?

---

### Post by Fixman on 2008-08-12
Open a terminal, and write:

```
dpkg --configure -a
```

---

### Post by smmalis on 2008-08-12
Nothing other than the eroor messages that normally pop up are printed into the console.  The output of dpkg --configure -a is already posted in my first post.

---

### Post by rohas on 2008-08-13
same problem with synaptic but with different [url=http://ubuntuforums.org/showthread.php?t=887446]error....
[/url]

i believe if there is a way to "clean" the packages that synaptic receive (and don't install) to "know" that no updates were downloading and start the process from the beginning would be a solution...but don't know how i can do this :(

---

### Post by smmalis on 2008-08-13
SOLUTION TIME!!!
I ran a locate to try and find any files relating to my custom kernel.  I deleted those files, and then dpkg --configure -a completed without any problems.

---

