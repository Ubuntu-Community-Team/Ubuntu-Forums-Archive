---
title: "Install iso updates"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by zoomy942 on 2009-06-24
So, i have trouble when i install 9.04 and do the update manager.  lots of errors and messages.  I have been messing with it for days, and googling like mad.  something i thought of was...

is there an iso image i can DL that will include all the updates for 9.04 so far?  Kind of like the 9.10 has updated iso's.

That would help A TON.

---

### Post by anystupidname on 2009-06-24
Not that I am aware of... We could try to help you with the apt issues if you provided more information.

```
sudo aptitude update && sudo aptitude upgrade
```

For a start, you could provide the output of the above command in a terminal

UPDATE: See:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
It looks like they're working on something like what you want too:
[https://wiki.ubuntu.com/OfflineUpdateSpec](https://wiki.ubuntu.com/OfflineUpdateSpec)

---

### Post by zoomy942 on 2009-06-24
i can do that.  i installed 9.10 alpha 2 just see see what would happen and things have been smoothg.  but i will reinstall 9.04 shortly.

---

### Post by zoomy942 on 2009-06-24
reinstalling now

---

### Post by zoomy942 on 2009-06-24
here is my first error


E: /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.1_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/dri/i915_dri.so')
E: /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-13-generic/kernel/drivers/regulator/wm8350-regulator.ko')

---

### Post by zoomy942 on 2009-06-24
here is more

```
zimmerman@zimmerman-laptop:~$ sudo aptitude update && sudo aptitude upgrade
[sudo] password for zimmerman: 
Writing extended state information... Done
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://security.ubuntu.com jaunty-security/main Packages        
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/restricted Packages  
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done             

W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  linux-headers-2.6.28-13{a} linux-headers-2.6.28-13-generic{a} 
  linux-image-2.6.28-13-generic{a} 
The following packages will be REMOVED:
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
The following packages will be upgraded:
  acpid app-install-data-partner apport apport-gtk apturl bluetooth bluez 
  bluez-alsa bluez-cups bluez-gstreamer bluez-utils brasero checkbox 
  checkbox-gtk compiz compiz-core compiz-gnome compiz-plugins 
  compiz-wrapper compizconfig-backend-gconf consolekit cron cups cups-bsd 
  cups-client cups-common ekiga evince evolution evolution-common 
  evolution-data-server evolution-data-server-common 
  evolution-documentation-en evolution-exchange evolution-plugins file 
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support 
  firefox-gnome-support gnome-about gnome-app-install gnome-desktop-data 
  gnome-settings-daemon gnome-system-tools gvfs gvfs-backends gvfs-bin 
  gvfs-fuse hal libbluetooth3 libbrasero-media0 libcamel1.2-14 
  libck-connector0 libcups2 libcupsimage2 libdecoration0 libebackend1.2-0 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 
  libevdocument1 libevview1 libexchange-storage1.2-3 libfreetype6 
  libgdata-google1.2-1 libgdata1.2-1 libgl1-mesa-dri libgvfscommon0 
  libhal-storage1 libical0 libmagic1 libmagickcore1 libmagickwand1 
  libmetacity0 libmpfr1ldbl libnautilus-extension1 libpam-ck-connector 
  libpurple-bin libpurple0 libsasl2-2 libsasl2-modules libtrackerclient0 
  libudev0 libwmf0.2-7 libwmf0.2-7-gtk linux-generic linux-headers-generic 
  linux-image-generic linux-libc-dev linux-restricted-modules-generic 
  metacity metacity-common nautilus nautilus-data ntpdate pidgin 
  pidgin-data python-apport python-cupshelpers python-problem-report 
  screen-profiles splix synaptic system-config-printer-common 
  system-config-printer-gnome tzdata udev update-manager 
  update-manager-core xserver-xorg-video-intel xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following partially installed packages will be configured:
  linux-restricted-modules-2.6.28-13-generic 
118 packages upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/92.2MB of archives. After unpacking 113MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 101478 files and directories currently installed.)
Unpacking linux-image-2.6.28-13-generic (from .../linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb) ...
Done.
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-13-generic/kernel/drivers/regulator/wm8350-regulator.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Selecting previously deselected package linux-headers-2.6.28-13.
Unpacking linux-headers-2.6.28-13 (from .../linux-headers-2.6.28-13_2.6.28-13.44_all.deb) ...
Selecting previously deselected package linux-headers-2.6.28-13-generic.
Unpacking linux-headers-2.6.28-13-generic (from .../linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb) ...
Preparing to replace linux-headers-generic 2.6.28.11.15 (using .../linux-headers-generic_2.6.28.13.17_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-generic:
 linux-restricted-modules-2.6.28-13-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.28-13 (2.6.28-13.44) ...
Setting up linux-headers-2.6.28-13-generic (2.6.28-13.44) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-headers-generic (2.6.28.13.17) ...
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-13-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 117 updates [-1].
zimmerman@zimmerman-laptop:~$ 

```

---

### Post by anystupidname on 2009-06-26
> **zoomy942 said:**
> here is my first error


E: /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.1_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/dri/i915_dri.so')
E: /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-13-generic/kernel/drivers/regulator/wm8350-regulator.ko')

Sorry for the delay, I'm not on here regularly. Usually others will pitch in... Anyway, for these first problems, try:
```
aptitude clean
```

---

### Post by anystupidname on 2009-06-26
On your latest post, those are not the type of errors you want to be getting for the kernel packages 8-[

I suppose you could try:
```
aptitude -f install
```
and/or have a look in these logs:
/var/log/dpkg.log
/var/log/aptitude

It is interesting you were able to actually "reproduce" this problem as it shouldn't be a regular occurrence and these commands are generally unnecessary...

---

### Post by zoomy942 on 2009-06-28
hi there.  so after a ton of installs and reading, it seems that the 2.28 kernals have a bug that causes file system corruption with my intel HD controller.  I didnt bleieve it but when i have to fsck every 3rd reboot, i was wonderintg what was going on.

that being said i installed 2.29 and started this thread, and so far things seem much much better.

[http://ubuntuforums.org/showthread.php?p=7530849#post7530849]("http://ubuntuforums.org/showthread.php?p=7530849#post7530849")

---

