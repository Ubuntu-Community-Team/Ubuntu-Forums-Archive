---
title: "[TUTORIAL] Ubuntu 12.10 on HP dv6t"
date: 2012-11-24
forum: Hardware
---

### Post by Dans564 on 2012-11-24
[COLOR=Red][SIZE=4]**How to run Ubuntu 12.10 on the HP dv6t-6100**[/SIZE][/COLOR]
~Up-to-date as of November 24th, 2012~
[IMG]http://www.blogcdn.com/www.engadget.com/media/2011/02/hppaviliondv612.jpg[/IMG]

So if you have the laptop pictured above, these are the steps too make Ubuntu 12.10 run without problems.  **_THIS TUTORIAL ASSUMES YOU"RE USING 64BIT_**

Here are the things that, for me, didn't work out of the box:
[INDENT]- Switchable graphics
- Beats Audio
- Screen brightness adjustment 
- Wifi after suspend
- Finger print reader <---**no fix for this**[/INDENT]**[COLOR=Red]How to obtain switchable graphics[/COLOR]**

1) ```
cd Desktop
```2) ```
mkdir xserver-xorg-video-intel && cd xserver-xorg-video-intel
```3) ```
wget https://launchpad.net/~andrikos/+archive/ppa/+build/3941876/+files/xserver-xorg-video-intel-dbg_2.20.9-0ubuntu2%2Bandrik2_amd64.deb
```4) ```
wget https://launchpad.net/~andrikos/+archive/ppa/+build/3941876/+files/xserver-xorg-video-intel_2.20.9-0ubuntu2%2Bandrik2_amd64.deb
```5) ```
sudo dpkg -i xserver-xorg-video-intel*.deb
```6) ```
sudo dpkg-reconfigure Xorg
```7) ```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 linux-headers-generic
```8 ) ```
sudo apt-get install ia32-libs-multiarch:i386 lib32gcc1 libc6-i386
```9) for this one actually type "y" when asked whether to install or not, otherwise it aborts for some reason.```
sudo apt-get install ia32-libs
```10) ```
cd /usr ; sudo ln -svT lib /usr/lib64
```11) ```
sudo apt-get install fglrx-updates
```12) ```
sudo amdconfig --initial -f
```13) ```
gksu gedit /etc/X11/Xsession.d/10fglrx
```14) delete everything and paste this in its place:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```15) save and reboot!  Enjoy switchable graphics!

**[COLOR=Red]How to obtain screen brightness control[/COLOR]**

1) ```
gksu gedit /etc/default/grub
```2) add acpi_vendor=backlight , as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```3) ```
sudo update-grub2
```4) reboot and enjoys screen brightness control!

**[COLOR=Red]How to fix no wifi after resume[/COLOR]**

1) ```
gksu gedit /etc/modprobe.d/iwlwifi.conf
```2) paste this to the end as a new line:
```
options iwlwifi bt_coex_active=N
```3) reboot and enjoy functional wifi after resume!

**[COLOR=Red]How to gain a full Beats™ audio experience[/COLOR]**

1)```
gksu gedit /etc/modprobe.d/alsa-base.conf
```2) paste this to the end as a new line:
```
options snd-hda-intel model=ref
```3) reboot and enjoy improved audio!

That is just about everything you need to enjoy Ubuntu 12.10 on your dv6t!
Hope this helps some people out!

-D

---

