---
title: "How can I tell if I have Xubuntu Alternative installed"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by inearlygaveup on 2009-11-08
How can I tell if I have Xubuntu _Alternative_ installed and not the standard Xubuntu.

---

### Post by kellemes on 2009-11-08
What is "Xubuntu Alternative"?

---

### Post by Bjalf on 2009-11-08
You look at the install CD?

---

### Post by inearlygaveup on 2009-11-08
The Alternate Install CD only requires you to have 64 MB RAM at install time.
Its for older PC's

---

### Post by inearlygaveup on 2009-11-08
Just to re-cap
I originally installed Xubuntu Alternate, but had big problems.
Although when it was running it ran very fast on my old PC, but the problems eventually made me re-install it.
During the installation the system downloaded a lot of files ( Iam thinking that it may have upgraded the install to a Full Xubuntu) as my PC dosent run as fast as it did with the first install.
So I was looking for an easy way of telling which one I have installed.

---

### Post by kellemes on 2009-11-08
As far as I know there is only one version of Xubuntu.
The alternate installer works on systems with less than 192MB of RAM but this has to do with the installer, not the end-result.
It's still the same Xubuntu.

Correct me if I'm wrong..

---

### Post by Bjalf on 2009-11-08
As I understand it, the alternate CD gives you the opportunity to install a command-line only system, but you have to specify that with F4. If not, a full Xubuntu system will be installed, just like with the Live CD.

I believe that the Live CD just unpacks a pre-installed system from the CD, while the alternate CD downloads (updated?) packages and actually installs them.

Alternate full install should be identical to Live CD install + updates.

If you want to run on a low-spec computer, do an alternate CLI install + install of separate packages afterwards. This is what I am trying to do, but I have run into kernel-related problems.

This is my current post-CLI-install script:
```
#!/bin/sh

gui=xorg
de="xfce4-session xfdesktop4 xfce4-panel xfce4-utils xfce4-settings xfce4-mixer xfce4-datetime-plugin"
wm="xfwm4 xfwm4-themes"
themes="gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-xfce xfce4-icon-theme tango-icon-theme tango-icon-theme-common"
guiutils="menu gksu synaptic xfce4-terminal mousepad software-properties-gtk thunar thunar-volman"
utils="galculator tuxcmd tuxcmd-modules"
web="firefox thunderbird"
games="aisleriot gnome-mahjongg glchess gnomine glines gnobots2 same-gnome gnometris gtali gnotski"
sound="alsa-base alsa-utils"
misc="acpi-support smartmontools"
slimdeps="libjpeg62 libpng12-0 libxft2 libxmu6"
slim=slim_1.3.0-2_i386.deb

sudo aptitude update
sudo aptitude -y safe-upgrade

sudo aptitude -y install --without-recommends $gui $de $wm $themes $guiutils $utils $web $games $sound $misc $slimdeps

cd
wget http://mirrors.kernel.org/ubuntu/pool/universe/s/slim/$slim
sudo dpkg -i $slim
```
It installs most of xfce4, but tries to avoid the bloated stuff. Slim login manager from Jaunty. Lots of gtk engines, I haven't decided on a theme yet.
Still under construction.

---

### Post by inearlygaveup on 2009-11-08
Thanks kellemes and Bjalf

My mistake I thought it was a slimmed down version with less features.
You have saved me a lot of time as I was thinking of reinstalling Xubuntu again.

---

