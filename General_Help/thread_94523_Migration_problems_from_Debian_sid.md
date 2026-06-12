---
title: "Migration problems from Debian sid"
date: 2005-11-24
forum: General Help
---

### Post by dmegg on 2005-11-24
I've just migrated my notebook in place from the latest Debian sid over to Breezy using aptitude.  It took a bit of fiddling and downgrading, but I did manage to end up with a working system, aside from two strange problems:

1. Using madwifi, my DWL-G650 is detected and I can scan access points, etc., but pump or dhclient cannot get a DHCP lease through it.

2. Using the restricted nvidia driver, I can get the NVIDIA splash screen, but then the X.org server fails with a signal 11 right after trying to load GLX (I do have nvidia-glx installed).

Both of these were working with sid and kernel 2.6.9, but they required that I build the drivers myself.  I wonder if there's some configuration that I missed because I migrated in place rather than installing onto a blank partition.  Has anyone else seen these problems?  Is it worth backing up and installing onto a clean disk, or would that just be a waste of time?

---

### Post by dmegg on 2005-11-25
I've solved half the problem -- the X.org accelerated nvidia driver works now.  I have a Geforce2Go, and tried the legacy nvidia driver, but with no success.  Unfortunately, I had not changed to the legacy nvidia glx package (somehow, apt let me get away with that).

The switch was not easy -- I couldn't uninstall the nvidia-glx-dev and nvidia-glx packages because of a problem with dpkg-divert, so I had to manually edit the postrm scripts for the two of them, and then manually edit the diversion file before purging everything nvidia-related and manually removing the /usr/lib/nvidia and /usr/X11R6/lib/nvidia directories.  Once that was done (and I'd upgraded to 2.6.12-10, just to be safe), I installed the restricted driver package, the legacy nvidia restricted driver, the legacy glx packages *and* modify xorg.conf to make sure that the GLCore and dri modules were not selected.  After that, the nvidia driver worked.

I still have not managed to get the madwifi driver working with my DWL-G650.

---

