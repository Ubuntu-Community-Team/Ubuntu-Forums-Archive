---
title: "Toshiba A100 Laptop 95% Working, here's how"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by calgarystevens on 2007-04-27
OK, I have a Toshiba A100ish laptop with a Celeron 1.46, 1 GB (was 512) ram, ATI Radeon Xpress 200M, 1280x800 15.4"screen, 10/100 net plus Atheros 5211 Wireless, Realtek AC97 sound, Epson CX3810 all-in-one. I thought after all the work I'd done to get everything working I'd share what I'd done and save it for the future for myself. First off, I'm using Feisty, I was unsure after the live cd (some things not working, sound network manager, etc) but pressed on anyways. Boy, am I glad I did! So, here goes....

Sound was down on startup so I did this:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end of the file

Network Manager worked great, my Atheros wireless worked out of the gate with the ath0 driver Feisty installed. To get wep working I had to check my router settings to 'Open Key' not managed or otherwise. 

Video is an ATI Radeon Xpress 200M and worked at 1280 on startup and after checking the box in the 'Restricted Drivers' box it was off to the 3d races, very nice.

Printer is an Epson CX3810 All-in-one. The built-in driver prints beautifully, but scanning was a challenge. So, I found [http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html) for scanner drivers (printers too apparently). And did this to make it work:
install sane libsane-backends then uninstall libsane-backends (weird yes, need pieces, but it then had trouble overwriting the backend driver, and this worked) *shrug*
install iscan *.deb
make menu item for iscan
I love that scanner driver, it's beautiful, simple, and makes nice scans.

Software related you need to: install libdvdcss for DVD playing. Find an MP3, and try to open it, and you'll see the new wizard for codecs, install the good, bad and ugly.
Install sun-java5-plugin for Java, and download frostwire for music sharing (if desired). To get an icon on the menu for frostwire: sudo cp /usr/share/icons/hicolor/32x32/apps/frostwire.png /usr/share/pixmaps
Download Flashplayer for linux, and install Flashplayer with ./flashplayer-installer
Download Realplayer for linux and install Realplayer with ./RealPlayer10GOLD.bin (install to /home/yournamehere/.RealPlayer)
Fix your Firefox plugins: uninstall totem plugin, install mplayer plugin :-) Go to cnn.com or somewhere similar and play a movie clip. Right-click when mplayer is playing movie, and in preferences uncheck the
realplayer and helix player boxes, make sure smil player is checked. That fixes Realplayer playback issues.

**The Big One!** Suspend-to-ram with the ATI fglrx drivers (your mileage may vary, I doubt I can help more, but here's how I did it)
sudo gedit /etc/acpi/sleep.sh
On second line put: sudo chvt 1

sudo gedit /etc/acpi/lid.sh
On second line put: sudo chvt 1

sudo gedit /etc/acpi/resume.sh
On last line put: sudo chvt 7

sudo gedit /etc/default/acpi-support
Edit lines thusly:
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

OK, I now have suspend working with AC plugged in, plus closing the lid works for suspend. But, on battery power it gets stuck going down to suspend, and comes to the locked screen and will not take keyboard input. But it does work!! For the first time in 6 months of distros/fiddling/changing settings. Sorry for the long post but if this helps a handful of people it will be more than worth it! Between family, friends and our house computers, I have 7 people off Windows and using Linux exclusively. ):P

---

### Post by calgarystevens on 2007-05-01
UPDATE: Suspend fixes!!!!!!!!!!!!!!!!!!!
sudo apt-get install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
and in lines that say:
elif [ -x "/sbin/s2ram" ] ; then
	    /sbin/s2ram -f       <--------Add the -f to force suspend
	   RET=$?
To go back to the old type of suspend -> sudo dpkg-divert --rename --remove /usr/sbin/pmi
Get rid of the gnome keyring password bugging you:
sudo apt-get install libpam-keyring
sudo gedit /etc/pam.d/gdm 
And add to the bottom:
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
Other settings are in applications->system tools->configuration editor:
look for apps/gnome-power-manager and check suspend/hibernate set to start on battery power etc.

It all works, every bit of it, my laptop lives, it lives!!!! :lolflag:

---

