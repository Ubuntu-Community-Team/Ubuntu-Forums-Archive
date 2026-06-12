---
title: "Customizing a LiveCD using Ubuntu 8.04 and debootstrap"
date: 2008-07-31
forum: General Help
---

### Post by bravespear on 2008-07-31
Hello everyone.

I not a total Linux newbie but my employer wants me to create a Linux boot disk for our work at home users.  I have a feeling this is going to be a long post, but I'm a little overwhelmed with how much I still need to do, and desperately need some assistance from anyone who can help.

The requirements my employer has given me:

The Live CD needs to boot successfully on 90-95% of different types of PC's which our work at home users may have in their homes.

Needs to have a web browser, which is locked down, and which supports Flash (with sound) and Citrix (I've installed Firefox 3.0 and have managed to get both Flash and Citrix running, but not sure how to lock down Firefox).

Needs to have VPN solution to connect to our company network. (I am attempting to use vpnc with kvpnc gui front-end, but running into issues getting the profile working)

LiveCD can *NOT* mount any other drives (whether USB flash, HDD, zip, floppy, etc) to protect against possible data theft and liability issues.

Lock the video refresh rate to 60hz and screen size to 1024x768.

Remove unnecessary applications (like the Konqueror web browser, kwallet, and anything else that may pop up on their screens).


The steps I am taking to do this are to create an environment using debootstrap, creating a sources list and chrooting into the environment.  I then install the kernel using:

```
apt-get install linux-generic linux-headers-generic ubuntu-minimal ubuntu-standard
```

I then install a core GUI, sound, firefox, vpnc and kvpnc using:

```
apt-get install xorg kdm kde-core alsa-base alsa-oss alsa-utils apmd libapm1 linux-sound-base build-essential firefox vpnc kvpnc
```

at this point I install and configure Citrix for use with the web browser.

Next I install the files for the livecd to run:

```
apt-get install casper discover1 xresprobe
```

then clean up the livecd, update the initramfs, etc and exit chroot.  umount the mount points, use mksquashfs to create the livecd file system, setup grub, create MD5 hashes and then create the LiveCD iso.

I have had a lot of luck with this method, but the issues I am having are:
[LIST]
locking down firefox from within the chrooted environment (no clue how to do it)
setting up /etc/vpnc/default.conf with the correct info to connect to our VPN and populate as a profile in KVPNC
remove unneeded apps (not sure which one's I can get rid of and which I can't)
Prevent mounting of any other drives (no idea how to do it) 
[EDIT] making any mounted drives read-only may also be an option, but not being mounted at all is preferable.
[/LIST]

The VPN problem is the most critical at this time, as its putting me behind my employers time line for the project.  I can manually type in the info for KVPNC and it will connect to the VPN concentrator, then after 15 seconds, prompt for the IPSec group password.  I can type it in again and stay connected to the VPN for another 15 seconds.. rinse and repeat ad nauseum.

Any help would be greatly appreciated.

---

### Post by bravespear on 2008-07-31
Anyone?

---

### Post by bravespear on 2008-08-01
Can anyone help?

---

### Post by whizbaby on 2008-10-02
Perhaps a bit late, but take a look at this it looks like what you are looking for:
[HTML]http://ubuntu-mini-remix.crealabs.it/[/HTML]

---

