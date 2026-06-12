---
title: "Installing latest nV drivers?"
date: 2009-01-19
forum: Hardware
---

### Post by stdPikachu on 2009-01-19
I've just bought myself a lovely Asus motherboard with a 730i/9300 chipset to use as my new HTPC frontend but have found out that the nVidia drivers in Hardy don't support the 9000 series, as evidenced by this line from Xorg.0.log:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I've tried to manually install the 180.xx nVidia drivers, but they don't appear to "stick" - every time I modprobe, I get the old 169.xx driver inserted instead, and thus continued lack of graphics. Can anyone give me any pointers on how I should be installing these? Information on the wiki and friends seems to be out of date (i.e. 7.10 and earlier only).

Using 8.04 Hardy (mythbuntu flavour).

---

### Post by mikewhatever on 2009-01-19
Any chance you can use Intrepid instead of Hardy? The 180.11 driver is in the repositories.

---

### Post by stdPikachu on 2009-01-20
Intrepid wasn't an option as there's no KDE3 available for it (long story).

Finally got around the issue once I understood how Hardy's binary blob driver package works. Added "nv nvidia_glx_new" to the restricted modules blacklist, and then uninstalled the restricted drivers package along with the nvidia drivers - sicne the ubuntu package basically ships as a ramdisk that's mounted at boot generated from static files that aren't in /lib/`uname -r`, so whatever kernel modules you install they'll always be "overwritten" by the tmpfs mount - blacklisting and removing the drivers stops this from happening.

After that I was able to install the 180.11 drivers and have them stick and all now appears to be hunky dory.

---

### Post by mikewhatever on 2009-01-20
Cool, thanks for the update.

---

### Post by speed32219 on 2009-01-21
Thank you stdPikachu, I have been looking for a way to install the newer Nvidia dirvers (acceleration support for 8200 chipset) with out upgrading to Intrepid.  Going to try this tonight on a fresh install along with the newer Alsa drivers for 5.1 sound over HDMI using hardy. 

Then on to battle the soungraph IMON driver issues using newer drivers.

---

### Post by stdPikachu on 2009-01-22
No problem, it was just a matter of figuring out which bits of the various howto's still applied. Think the process basically went:

Uninstall restricted drivers metapackage and all versions of the nvidia drivers
Add nv, nvidia and nvidia_new to the modules blacklist
Install the nvidia driver from downloaded .run package (most users will need to install libc6-dev IIRC)
Add nvidia to /etc/modules
Modprobe nvidia
startx

That's about as detailed as it's gonna get as I'm about a jillion miles from an ubuntu machine at the moment.

Not tried any of the apps that use VDPAU yet... maybe when blu-ray becomes an option. Until then, I yawn in the face of hi-def ;)

---

