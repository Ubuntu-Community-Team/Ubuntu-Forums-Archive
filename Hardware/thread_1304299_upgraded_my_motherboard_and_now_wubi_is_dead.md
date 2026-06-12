---
title: "upgraded my motherboard and now wubi is dead"
date: 2009-10-29
forum: Hardware
---

### Post by steve51184 on 2009-10-29
hey guys my motherboard died the other day so i had to get a new one and after installing a few new driver windows 7 is all ok but i can't say the same for ubuntu 9.10 beta (via wubi) is there a way i can fix this?

*will post the error i get in a min just need to reboot...*

---

### Post by steve51184 on 2009-10-31
here's the error

[IMG]http://i35.tinypic.com/ncbn6v.jpg[/IMG]

can anyone help me with this please?

---

### Post by gamewolf on 2009-10-31
try this: [http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)

---

### Post by steve51184 on 2009-10-31
> **gamewolf said:**
> try this: [http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)

thanks for the reply but that is if you have ubuntu installed on it's own partition and i use wubi so it's installed into a root.disk file :(

---

### Post by steve51184 on 2009-10-31
nevermind i guess i can do [THIS]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?") :KS

---

### Post by gamewolf on 2009-10-31
Alright hope it works. let me know how it turns out.

---

### Post by steve51184 on 2009-10-31
will do... booted into my live cd now ;)

---

### Post by steve51184 on 2009-10-31
right i'm stuck on this bit (bold):

> sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
**sudo chroot /mnt /bin/bash**

and i'm getting this error:

> $ sudo chroot /vdisk /bin/bash
chroot: cannot run command `/bin/bash': Exec format error

please note that my install is mounted as /vdisk and not /mnt from the "[mount wubi drive guide]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")"

---

### Post by steve51184 on 2009-10-31
just tried again but mounted my root.disk as /mnt and not /vdisk but i got the same error:

> $ sudo chroot /mnt /bin/bash
chroot: cannot run command `/bin/bash': Exec format error

i'm soooo close can i please just get a little more help? :(

---

### Post by steve51184 on 2009-10-31
i'm using a 32bit boot cd on a 64bit wubi install.. is this the problem?

---

### Post by gamewolf on 2009-10-31
I am not sure why you are doing those commands.

Looks like you need to do these first:

```
sudo mkdir /win
sudo mount /dev/sda1 /win
```

Remember to replace sda1 with whatever your hard drive is.

Here you mount the disk file as its own hard disk:

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

Then to check the filesystem is mounted properly:

```
sudo fsck /win/ubuntu/disks/root.disk
```

Try this and see if that works better. If you need to, restart the livecd to start fresh.

---

### Post by steve51184 on 2009-10-31
thanks for the reply gamewolf but that is just for mounting my wubi root.disk and i've done that fine what i need to do after is in this guide:

[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)

this is where i'm having the problems

---

### Post by steve51184 on 2009-10-31
> **steve51184 said:**
> i'm using a 32bit boot cd on a 64bit wubi install.. is this the problem?

yeah that was the problem... continuing with the guide :)

---

### Post by gamewolf on 2009-10-31
sorry about that didn't realize you had gotten it mounted.

looks like you were not able to chroot into your disk image. go into your mounted directory and make sure everything still is there.

so if you mounted the image file into /mnt and inside of mnt is the bin boot, etc folders. then this command should work:

```
sudo chroot /mnt /bin/bash
```

---

### Post by steve51184 on 2009-10-31
right 1 last error and this should be fixed.... after running apt-get-upgrade (after apt-get update) i get this error:

> # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  checkbox checkbox-gtk deskbar-applet desktopcouch emacsen-common firefox
  firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support hwtest
  hwtest-gtk ia32-libs info install-info jockey-common jockey-gtk
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common khelpcenter4 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libtrackerclient0 libusplash0
  lupin-support miro miro-data mountall nvidia-173-modaliases
  nvidia-185-kernel-source nvidia-185-libvdpau nvidia-185-modaliases
  nvidia-96-modaliases nvidia-glx-180 nvidia-glx-185 pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils
  python-desktopcouch python-desktopcouch-records software-center ubuntu-tweak
  uptrack uptrack-manager usplash wine xserver-common xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-vmmouse xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support
62 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: **Could not open lock file /var/cache/apt/archives/lock - open (5: Input/output error)**
E: Unable to lock the download directory

how do i fix this?

---

### Post by gamewolf on 2009-10-31
look like another program is using apt and preventing other programs from using it.

try these and paste the results back

```
ps -A | grep apt
ps -A | grep update
```

---

### Post by steve51184 on 2009-10-31
seems that my drive unmounted and wouldn't mount again so i did a reboot did all the commands again and the updates are installing now lets hope when it's done that my install works again :)

---

### Post by gamewolf on 2009-10-31
arlight! hope it works.

---

### Post by steve51184 on 2009-10-31
all went fine but i still get the same error when booting into ubuntu... any ideas now?

---

### Post by steve51184 on 2009-10-31
any more ideas guys?

---

### Post by steve51184 on 2009-11-13
guys please it's been 2 weeks and this is still not fixed i'm begging you :(

---

