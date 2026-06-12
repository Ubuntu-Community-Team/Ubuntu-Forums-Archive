---
title: "problem with update, nvdia driver, login, turn display"
date: 2012-10-10
forum: Hardware
---

### Post by iglinux on 2012-10-10
After an update 2 weeks ago I had problems to login into my session,  doesn't matter if I used lightdm, gdm, or even ubuntu or gnome desktops.
I  discovered that the conflict was caused because of the two displays I  use (one dell 23'LED with displayport and the other HP 19' LCD with  VGA). They were working perfectly before, and the HP display was  inverted 90degrees. I have a HP core i5 Compaq 8200 Elite with one  display port and one VGA port.

After the upgrade, 12.04 64-bits,  something happened with nvidia-current or Xorg.conf files, I don't know.  Every time I've tried to login the screen flashed back to the login  page. The problem was not password, lighdm vs gdm, or anything else  posted before. I then tried to unplug the displayport cable of the dell  display and voilà, I could login! If I used an adapter Diplayport/DVI,  everything OK again. When I changed the HP19'LCD for a HP20'LED, I could  plug again the DELL with the Displayport. Weird!

The problem I  have now is that when I try to turn the HP20' 90degrees, the session  logs out.  I am currently using the driver Intel® Sandybridge Desktop  Experience Standard, since I sudo purged Nvdia-Current. When I try to  install Nvdia-current my desktop does not work well, I loose the  configuration in gnome environment, and if I try ubuntu or ubuntu2D the  unity does not work at all. When I purge and autoremove Nvidia-current,  all work as before, except that I can't turn the HP display.

Here some of the attempts: 
I have updated grub, sudo Xorg -configure, install Nvidia-current-settings, also:
>wget   [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+build/3747934/+files/nvidia-current_304.43-0ubuntu1~precise~xup1_amd64.deb](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+build/3747934/+files/nvidia-current_304.43-0ubuntu1~precise~xup1_amd64.deb)
>sudo dpkg --install nvidia-current_304.43-0ubuntu1~precise~xup1_amd64.deb,..

did not work.

I  do not have an /etc/X11/xorg.conf file, only a xorg.conf.failsafe. When  I tried sudo Xorg-configure I lost resolution and everything was  terrible.

In addition, when I tried to solve the login problem, I  reinstalled grub and also used boot-repair with the live CD. I did  something wrong, because when I boot with something pluged in the USB,  it asks for a boot file and does not boot. I wish I knew how to correct this.

Any Ideas? Thanks, IG.

---

### Post by iglinux on 2012-10-19
OK SOLVED. I don't know why.
I have removed some fix PPAs and I made some changes via ubuntu-desktop (not gnome). All of sudden, I could turn the display and use my old one 19'. Still, I am not using nvidia, and I also do not have a xorg.conf file (only these in /etc/X11):
app-defaults                      xorg.conf.bs
cursors                           xorg.conf.failsafe
default-display-manager           xorg.conf.nvidia-xconfig-original
default-display-manager.dpkg-tmp  Xreset
fonts                             Xreset.d
rgb.txt                           Xresources
X                                 Xsession
xinit                             Xsession.d
xkb                               Xsession.options
xorg.conf.backup                  Xwrapper.config

But...all is working fine now - I guess I will not know what happened.

---

