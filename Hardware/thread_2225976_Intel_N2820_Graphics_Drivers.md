---
title: "Intel N2820 Graphics Drivers"
date: 2014-05-24
forum: Hardware
---

### Post by al1n4 on 2014-05-24
Hello! I have an Intel Celeron N2820 in an Acer Aspire E1-510-2500. I used to do some light gaming on Windows (Counter-Strike Source, Crysis on low, GTA IV, and so on), and now when I try to install graphic drivers for Lubuntu 14.04, I get this:
```

W:GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)/dists/trusty/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```


Any help?

---

### Post by jeremy31 on 2014-05-24
>  wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | sudo apt-key add -
> wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | sudo apt-key add -

> [FONT=Ubuntu Mono]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A902DDA375E52366[/FONT] This might work by itself

---

### Post by deadflowr on 2014-05-24
Aside from fixing the key for the intel site, you also need to disable the cdrom entry.
I'm not sure how lubuntu' software center works.
In normal Ubuntu's software center you go to edit > software sources > other software
and uncheck the entries for cdrom( they'll be the top entries, normally)
See if something like that works in lubuntu.

---

### Post by jeremy31 on 2014-05-24
Could always download the intel-linux-graphics-installer from [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux)
Might have to edit the /etc/lsb-release file to tell the installer it is ubuntu instead of lubuntu, just have to replace what is in the lsb-release and put this in there
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"

---

### Post by Yellow Pasque on 2014-05-24
It is not a good idea for end users to install drivers straight from Intel's site, especially if the drivers are not needed (and users coming from Windows often think they need drivers when they're already installed).
Can you give the output of glxinfo?
```
glxinfo
```

---

### Post by Devanil_Choudhury on 2014-09-08
I used this code but It gave an error like -

gpg: keyserver receive failed: keyserver error

---

