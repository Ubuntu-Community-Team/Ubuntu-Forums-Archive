---
title: "ATI good drivers for Lucid 10.04"
date: 2010-05-07
forum: Hardware
---

### Post by kapcom01 on 2010-05-07
Hello, i've been using Ubuntu since 9.04 and ever since i have this problem with my Ati X800. The default (open source) drivers doesn't support fully the card so opengl is not as fast as it should. The biggest problem though, is the flash videos on youtube and such which are slow...

So i deceided either to fix it by installing proprietary drivers or to buy a nVidia card.. I can't live with it anymore #-o

I followed [[_these instructions_]]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide") but it doent work for me.. I get this:
```

kapcom01@Manolis-PC:~$ aticonfig --initial
aticonfig: No supported adapters detected

```

Then i reboot and opengl is gone..
```

kapcom01@Manolis-PC:~$ fglrxinfo
Segmentation fault
kapcom01@Manolis-PC:~$ aticonfig --initial
aticonfig: No supported adapters detected
kapcom01@Manolis-PC:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]

```

Can anyone help me with this? Thanks.

---

### Post by sephiroth2212 on 2010-05-11
Hi. I'm having the same problem with my ATI X2300.
I'm sure it's something I'm doing wrong.
Any advice?

---

### Post by metallus on 2010-05-11
Open a terminal and enter:
sudo aptitude update
sudo aptitude install fglrx fglrx-amdcccle fglrx-kernel-source fglrx-modaliases
If you get an error, post it here.

---

### Post by khelben1979 on 2010-05-11
Getting a newer graphics card is the way to go if you intend on using Ubuntu Lucid.

Otherwise, if your budget won't allow it, you can always go for a really old version of Ubuntu and then you can look at YouTube with your current hardware.

---

### Post by mattlach on 2010-05-11
> **khelben1979 said:**
> Getting a newer graphics card is the way to go if you intend on using Ubuntu Lucid.

Otherwise, if your budget won't allow it, you can always go for a really old version of Ubuntu and then you can look at YouTube with your current hardware.

Problem is, if you get too new hardware, it doesn't work well either.   Evergreen support is still shaky :p  (not that this is scaring me away from picking up a 5xxx board.)

I prefer Nvidia boards under Linux.  The drivers are simply so much more mature.  That being said, the fastest board I could find that was passively cooled (my current system is going to be QUIET) Radeon 5750.

Wish me luck :p

---

### Post by Yellow Pasque on 2010-05-11
The X800 and X2300 are not supported by fglrx/Catalyst. See this to restore the default video driver configuration: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by toughengineer on 2010-05-20
i did it and i still have the same problem above ..
any help ?!

---

### Post by toughengineer on 2010-05-20
> **kapcom01 said:**
> Hello, i've been using Ubuntu since 9.04 and ever since i have this problem with my Ati X800. The default (open source) drivers doesn't support fully the card so opengl is not as fast as it should. The biggest problem though, is the flash videos on youtube and such which are slow...

So i deceided either to fix it by installing proprietary drivers or to buy a nVidia card.. I can't live with it anymore #-o

I followed [[_these instructions_]]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide") but it doent work for me.. I get this:
```

kapcom01@Manolis-PC:~$ aticonfig --initial
aticonfig: No supported adapters detected

```

Then i reboot and opengl is gone..
```

kapcom01@Manolis-PC:~$ fglrxinfo
Segmentation fault
kapcom01@Manolis-PC:~$ aticonfig --initial
aticonfig: No supported adapters detected
kapcom01@Manolis-PC:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]

```

Can anyone help me with this? Thanks.

got solution ?!

---

### Post by w2vy on 2010-05-20
> **metallus said:**
> Open a terminal and enter:
sudo aptitude update
sudo aptitude install fglrx fglrx-amdcccle fglrx-kernel-source fglrx-modaliases
If you get an error, post it here.

No error, but a LOT going to be removed.

Are you sure?

```
tom@w2vy:~$ sudo aptitude install fglrx fglrx-amdcccle fglrx-kernel-source fglrx
-modaliases
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  fglrx-kernel-source
The following packages will be REMOVED:
  acpi{u} anjuta{u} anjuta-common{u} anjuta-dbg{u} apmd{u} autogen{u}
  bittorrent{u} bluetooth{u} bluez-pin{u} bluez-utils{u} bug-buddy{u}
  cupsys-driver-gutenprint{u} devhelp-common{u} diveintopython{u} ekiga{u}
  eog-dbg{u} epiphany-browser-dbg{u} evince-dbg{u}
  evolution-data-server-dbg{u} evolution-dbg{u} exuberant-ctags{u}
  fortune-mod{u} fortunes-min{u} fping{u} freeglut3{u} gimp{u} gimp-data{u}
  gimp-dbg{u} gir1.0-clutter-gtk-0.10{u} gir1.0-gconf-2.0{u} glchess{u}
  glines{u} gnect{u} gnibbles{u} gnobots2{u} gnome-applets-dbg{u}
  gnome-dbg{u} gnome-games{u} gnome-panel-dbg{u} gnome-pilot{u}
  gnome-pilot-conduits{u} gnome-themes{u} gnotravex{u} gnotski{u}
  gstreamer0.10-plugins-base-dbg{u} gstreamer0.10-plugins-good-dbg{u}
  gstreamer0.10-plugins-ugly-dbg{u} gtali{u} hal-device-manager{u}
  hwdb-client-common{u} hwdb-client-gnome{u} iagno{u} intltool{u}
  libapm1{u} libatk1.0-dbg{u} libatspi-dbg{u} libbabl-0.0-0{u}
  libblas3gf{u} libbluetooth2{u} libdb4.6{u} libdevhelp-1-1{u}
  libfontconfig1-dbg{u} libgail-gnome-dbg{u} libgda-4.0-4{u}
  libgda-4.0-common{u} libgda3-3{u} libgda3-3-dbg{u} libgda3-common{u}
  libgda3-sqlite{u} libgdl-1-3{u} libgdl-1-common{u} libgdl-1-dbg{u}
  libgegl-0.0-0{u} libgfortran3{u} libgimp2.0{u} libgladeui-1-9{u}
  libglew1.5{u} libglib2.0-0-dbg{u} libglut3{u} libgnome2-dbg{u}
  libgnomecanvas2-dbg{u} libgnomeui-0-dbg{u} libgnomevfs2-0-dbg{u}
  libgnomevfs2-bin{u} libgoffice-0.8-8{u} libgoffice-0.8-8-common{u}
  libgoffice-dbg{u} libgsf-1-114-dbg{u} libgsf-gnome-1-114{u}
  libgsf-gnome-1-114-dbg{u} libgstreamer0.10-0-dbg{u} libgtkhtml3.14-dbg{u}
  libgtksourceview-common{u} libgtksourceview1.0-0{u} libhsqldb-java{u}
  liblapack3gf{u} libloudmouth1-0-dbg{u} libnspr4-0d-dbg{u}
  libnss3-1d-dbg{u} liboobs-1-4-dbg{u} libopal3.6.6{u} libopts25{u}
  libopts25-dev{u} libpango1.0-0-dbg{u} libpolkit-dbus2{u}
  libpolkit-gnome0{u} libpolkit-grant2{u} libpolkit2{u} libpt2.6.5{u}
  libpt2.6.5-plugins{u} librecode0{u} librsvg2-dbg{u} libuniconf4.6{u}
  libvala0{u} libwebkit-1.0-2-dbg{u} libwvstreams4.6-base{u}
  libwvstreams4.6-extras{u} libxft2-dbg{u} libxml2-dbg{u} lightsoff{u}
  nautilus-dbg{u} odbcinst{u} odbcinst1debian1{u} openoffice.org{u}
  openoffice.org-base{u} openoffice.org-evolution{u}
  openoffice.org-filter-binfilter{u} openoffice.org-filter-mobiledev{u}
  openoffice.org-java-common{u} openoffice.org-officebean{u}
  openoffice.org-report-builder-bin{u} policykit{u} python-bittorrent{u}
  python-cairo-dbg{u} python-dbg{u} python-gobject-dbg{u}
  python-gtk2-dbg{u} python-gtkglext1{u} python-numpy{u}
  python-numpy-dbg{u} python-opengl{u} python2.6-dbg{u} rhythmbox-dbg{u}
  rss-glx{u} scim-modules-table{u} scim-tables-additional{u} seed{u}
  sound-juicer{u} swell-foop{u} tangerine-icon-theme{u} tango-icon-theme{u}
  tango-icon-theme-common{u} totem-dbg{u} ttf-arabeyes{u}
  ttf-arphic-ukai{u} ttf-arphic-uming{u} ttf-baekmuk{u}
  ttf-bengali-fonts{u} ttf-dejavu{u} ttf-dejavu-extra{u}
  ttf-devanagari-fonts{u} ttf-gujarati-fonts{u} ttf-indic-fonts{u}
  ttf-kannada-fonts{u} ttf-kochi-gothic{u} ttf-kochi-mincho{u}
  ttf-malayalam-fonts{u} ttf-mgopen{u} ttf-oriya-fonts{u}
  ttf-sazanami-mincho{u} ttf-sil-gentium{u} ttf-sil-gentium-basic{u}
  ttf-tamil-fonts{u} ttf-telugu-fonts{u} unixodbc{u} vnc-common{u}
  wvdial{u} xsane{u} xsane-common{u} xvncviewer{u}
0 packages upgraded, 1 newly installed, 180 to remove and 0 not upgraded.
Need to get 0B/14.0kB of archives. After unpacking 984MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

EDIT: I think much the remove was 'autoremove' which is clearer with apt-get vs aptitude

---

### Post by w2vy on 2010-05-21
> **Temüjin said:**
> The X800 and X2300 are not supported by fglrx/Catalyst. See this to restore the default video driver configuration: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

I tried those and ended up with this:

(Reading database ... 182618 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bcschmerker on 2010-05-21
I am currently debugging a video installation that, as of 21 May 2010, won't hold Visual Effects settings in GNOME Appearance Properties (None where I expect Basic after startup).  My experience is that the ATI Radeon GPU's up to the X Series are good with the open-source X.org-ATI driver; I actually *need* FGLRX myself, as X.org-ATI does not support the latest Radeon HD GPU's such as the HD3200 on my "all-AMD" system.

---

### Post by UpnOvr on 2010-05-21
I am in the exactly same situation with a Radeon X800 GTO.
It seems to be a catch 22. fglrx doesn't need a xorg.conf and that's the rub.
It looks like lots of people are experiencing the same issue.
Has anyone cracked this nut yet?
(segmentation fault with fglrxinfo) and (no supported adapters detected with aticonfig)
:mad::mad::mad::mad::mad:

---

### Post by Yellow Pasque on 2010-05-21
> **UpnOvr said:**
> I am in the exactly same situation with a Radeon X800 GTO.
...
> The X800 and X2300 are not supported by fglrx/Catalyst. See this to restore the default video driver configuration: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Yellow Pasque on 2010-05-21
> **w2vy said:**
> I tried those and ended up with this:
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx
Run this first:
```
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2
```

---

### Post by ggorman on 2010-05-28
I'm having similar issues. Fglrx seems to barely work, won't enable any desktop effects. If I enable ATI then my dual-monitor setup is horrible, the 2nd screen is fuzzy and scrambled, and eventually everything comes crashing down.

Worked great in 9.10, what happened? 

Don't tell me to get a new graphics card, it's a laptop with embedded FireGL 5250...

---

### Post by khelben1979 on 2010-05-28
> **ggorman said:**
> I'm having similar issues. Fglrx seems to barely work, won't enable any desktop effects. If I enable ATI then my dual-monitor setup is horrible, the 2nd screen is fuzzy and scrambled, and eventually everything comes crashing down.

Worked great in 9.10, what happened? 

Don't tell me to get a new graphics card, it's a laptop with embedded FireGL 5250...

Then the graphics driver which is provided by Ubuntu Lucid is probably not the same as the version which gets shipped by Ubuntu Karmic and there you got the problem.

Try and use the same version of the ATi driver which you used in Karmic with Ubuntu Lucid would be my advice. At the same time, the driver version must be supported by the new version of the X server which gets shipped with Ubuntu Lucid.

---

### Post by bcschmerker on 2010-06-04
> **bcschmerker said:**
> I am currently debugging a video installation that, as of 21 May 2010, won't hold Visual Effects settings in GNOME Appearance Properties (None where I expect Basic after startup).  My experience is that the ATI Radeon GPU's up to the X Series are good with the open-source X.org-ATI driver....Update:  A routine clue-fish in Synaptic indicates that X.org may already have a usable driver for my system in the xserver-xorg-Video-radeonhd package.  I'll purge FGLRX and see whether Video-RadeonHD will work....

---

### Post by bcschmerker on 2010-08-24
> **bcschmerker said:**
> Update:  A routine clue-fish in Synaptic indicates that X.org may already have a usable driver for my system in the xserver-xorg-Video-radeonhd package.  I'll purge FGLRX and see whether Video-RadeonHD will work....Update 2:  I ended up having to reinstall 10.04 anyway, as the i386 version, due to an incompatibility between Adobe® Flash Player 10.1.53.64 (32-bit only) and Mozilla® Firefox® 3.6.3 for AMD64 (64-bit only).  Apparently the data carried over on /home from 8.04.4 wouldn't work with the new packages:  I saved my docs and .mozilla to a USB memory chip, reinstalled with ext4 on all partitions; all systems were go with the docs and .mozilla restored to my new ext4 /home.  Problem solved in this case. ;-)

---

### Post by mastablasta on 2010-08-24
that's good to hear. i just wanted to comment that HD 3200 is not so old and it should work with Ubuntu.
 
i guess i got lucky with mine (for now) as radeon 9600 seems to work ok with opensource drivers.

---

### Post by Vera eikon on 2011-01-29
Good news! This is solved in Ubuntu 10.10!!!! :KS:KS:KS
Here's what I did:

1. Upgrade to 10.10 (software source: Server from United States).
2. I've installed my ATI card drivers through System/Administration/Additional Drivers. Tip from: [http://www.webupd8.org/2010/09/fglrx-finally-works-with-ubuntu-1010.html](http://www.webupd8.org/2010/09/fglrx-finally-works-with-ubuntu-1010.html). Now catalyst is working!!!
3. I did sudo /usr/lib/fglrx/bin/amdcccle, and configured catalyst. Tip from: [http://ubuntuforums.org/archive/index.php/t-1601189.html](http://ubuntuforums.org/archive/index.php/t-1601189.html)

This worked for me!!! Hope it helps someone else! :P

---

