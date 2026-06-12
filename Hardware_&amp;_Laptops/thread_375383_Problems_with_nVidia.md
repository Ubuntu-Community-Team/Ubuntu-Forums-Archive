---
title: "Problems with nVidia"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by drev on 2007-03-03
I just tried installing nVidia drivers on Ubuntu 6.06, using Automatix2.  When I rebooted, the system came up, but the graphics were messed up... there were vertical lines across the whole screen, the color was weird, and the system would freeze after a very short time.

Does anyone know what's causing this and how I can fix it?

I'm running an HP Pavilion laptop, nVidia GeForce Go 6150 graphics car, 1GB RAM, etc.

Any and all help is appreciated

---

### Post by andreas64 on 2007-03-04
Hi,

why don't you install the Nvidia-driver through Synaptic?

Just enable the multiverse-repository and install 'nvidia-glx'

Andreas

---

### Post by ebichuhamster on 2007-03-05
> **andreas64 said:**
> Hi,

why don't you install the Nvidia-driver through Synaptic?

Just enable the multiverse-repository and install 'nvidia-glx'

Andreas

I have the same video card (and the same laptop it seems) but i dont understand anything of what is said in the quote..

Can anyone translate it for me? In noob language of course

Thx ^_^

---

### Post by blackeagle83 on 2007-03-05
Instead of Synaptic i suggest to download directly the right driver from [nvidia home page]("http://www.nvidia.com/page/home.html")

1. download tar.gz of your video-card version
2. extract the archive
3. enter as root
4. stop gdm (or your graphical server):
    /etc/init.d/gdm stop
5. login as root
6. cd "the extracting directory"
7. type "chmod 755 name_of_driver_installer.sh"
8. type "sh name_of_driver_installer.sh"
9. Everytime type ok :)

P.S. If you want to save your previous configuration file type as root:
   cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

suggest installing
compiz as animated windows manager

---

### Post by El_Matthews on 2007-03-05
Before attempting anything on your box it can be wise to check the documentation [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

in this case the installation of nvdia drivers is completely documented under;
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

follow those guides step by step and you will achieve the installation of your driver without any problem

---

### Post by drev on 2007-03-05
> **blackeagle83 said:**
> Instead of Synaptic i suggest to download directly the right driver from [nvidia home page]("http://www.nvidia.com/page/home.html")

1. download tar.gz of your video-card version
2. extract the archive
3. enter as root
4. stop gdm (or your graphical server):
    /etc/init.d/gdm stop
5. login as root
6. cd "the extracting directory"
7. type "chmod 755 name_of_driver_installer.sh"
8. type "sh name_of_driver_installer.sh"
9. Everytime type ok :)

P.S. If you want to save your previous configuration file type as root:
   cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

suggest installing
compiz as animated windows manager

Okay, I tried doing this.  When I got into the nvidia installation program, it said something like a matching kernel couldn't be found, or some such?  Then it asked if I wanted it to try downloading a kernel, but it was unsuccessful.

Does anyone know what's up with this, and how to fix?

I ran "uname -r" and this is the output:
> 2.6.15-28-amd64-generic

Ubuntu 6.06, 64-bit

---

