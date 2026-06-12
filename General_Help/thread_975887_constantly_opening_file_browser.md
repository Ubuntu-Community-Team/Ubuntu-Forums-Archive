---
title: "constantly opening file browser"
date: 2008-11-08
forum: General Help
---

### Post by AntiHeroJoe on 2008-11-08
I've made the mistake of trying to put an icon on my desktop. Suddenly tons and tons of file browsers are opening in the gnome panel...though I don't see them opening, just in the panel. I restart and it continues to happen. Help?

---

### Post by taurus on 2008-11-08
You can remove it from your ~/Desktop if you wish.  Do you know which program is that?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by AntiHeroJoe on 2008-11-08
Oh yes! Thanks, I was able to remove the item and it stopped. I was creating a shortcut to synaptic, so the file was synaptic.desktop. What on would cause that? Is this going to happen every time I want to add an icon? Right now I have no icons, but if I'm scared to add any now!

---

### Post by taurus on 2008-11-08
You can add an icon for synaptic on the top panel, not on your desktop.

---

### Post by AntiHeroJoe on 2008-11-08
Just as a test-run, I right clicked on the desktop, and went to Create Document > empty file, and it started spawning the taskbar items again. So it's not just my attempt to add synaptic to the desktop.

Here's the interesting thing, after I deleted the file (which I can't see on the desktop itself by the way, only through terminal) the taskbar items begin to disappear one-by-one.

So it seems I can't have any desktop items.

This only started happening after upgrading to 8.10

Any thoughts?

---

### Post by taurus on 2008-11-08
Why don't you try to download something because the it will save to your Desktop as a default directory.  Then, do you get multiple copies?

---

### Post by AntiHeroJoe on 2008-11-08
Yes, just tried saving an image to the desktop and it began spawning these file browser taskbar items again.

---

### Post by taurus on 2008-11-08
There is something going on with your Desktop then.  What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by AntiHeroJoe on 2008-11-08
```

joseph@Netzach:~/Desktop$ ls -la ~/Desktop
total 7
drwxrwxrwx   2 joseph joseph 1024 2008-11-08 20:44 .
drwx------ 137 joseph joseph 6144 2008-11-08 20:41 ..
joseph@Netzach:~/Desktop$ 

```

---

### Post by soro2005 on 2008-11-08
I think your Nautilus or Gnome Panel are in a weird loop. Try killing them.

```
killall gnome-panel
```
and
```
killall nautilus
```

---

### Post by AntiHeroJoe on 2008-11-08
Earlier I killed gnome-panel and it simply restarted and carried on. If I restart, when gnome starts it carries on. Only if I have something on my desktop though. Very bizarre. Is there a way to permanently fix this besides killing processes and not having items on the desktop?

---

### Post by soro2005 on 2008-11-08
> **AntiHeroJoe said:**
> Earlier I killed gnome-panel and it simply restarted and carried on. If I restart, when gnome starts it carries on. Only if I have something on my desktop though. Very bizarre. Is there a way to permanently fix this besides killing processes and not having items on the desktop?

Well, it's certainly not normal. How do you know there're file browsers opening if they aren't actually opening? What exactly happens in the Gnome Panel, and in which part of it?

---

### Post by AntiHeroJoe on 2008-11-08
Here's a screenshot. You can't see the file browsers open, and clicking on them doesn't maximize them. They just appear in the taskbar.

[IMG]http://www.awfulrofl.com/desktop.jpg[/IMG]

---

### Post by adult swim on 2008-11-08
maybe if you ran ```
top
``` from a terminal and then put something on the desktop it might show you some process thats gone awry.

---

### Post by soro2005 on 2008-11-08
That is very weird, indeed. There is something wrong either with your Nautilus, or just with your Gnome Panel. Have you put any additional applets onto the panel?

I would be inclined to suggest that you reset all your gnome panels with
```
gconftool-2 --recursive-unset /apps/panel
```
but you would have to customize it from scratch, and perhaps that's the completely wrong track. :confused:

---

### Post by AntiHeroJoe on 2008-11-08
top shows the following processes with the highest CPU usage:

Xorg
nautilus
gnome-panel
gconfd-2

Don't know what to do with this info though. I have another problem: [http://ubuntuforums.org/showthread.php?t=975608](http://ubuntuforums.org/showthread.php?t=975608)  that has possibly something to do with X11 / Xorg...maybe is something wrong with this? Is there a way to reinstall Xorg? Or would this trash my system?

---

### Post by soro2005 on 2008-11-08
I think it's safe to say it's not the X server, so don't worry about Xorg. If the main menu also doesn't open, it looks to me like your gnome panel is borked. You can use synaptic to reinstall the gnome-panel related items, and you can also try to reset your gnome panel with the command given above.

Or rather: It looks to me like your gtk stuff hasn't managed to do the upgrade. Do several times the following:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
until there is nothing left to be installed/upgraded.

---

### Post by AntiHeroJoe on 2008-11-08
I have tried the command supplied which reset the gnome panels, re-installed any gnome-panel items I could find in Synaptic, and ran the second set of update commands several times.

If I try to add something to the desktop, the same thing occurs. (side: I am also unable to edit the main menu via the main menu app/util).

---

### Post by soro2005 on 2008-11-08
Yes, and from your other threat, it is quite clear that your computer is using an outdated version of gtk. Are you sure that your system is fully up to date?

Can you give us the output of
```
dpkg -l | grep libgtk2.0
```

---

### Post by AntiHeroJoe on 2008-11-08
What's the latest version?

```

joseph@Netzach:~$ dpkg -l | grep libgtk2.0
ii  libgtk2.0-0                                2.14.4-0ubuntu1                                      The GTK+ graphical user interface library
ii  libgtk2.0-bin                              2.14.4-0ubuntu1                                      The programs for the GTK+ graphical user int
ii  libgtk2.0-cil                              2.12.1-1ubuntu2                                      CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                           2.14.4-0ubuntu1                                      Common files for the GTK+ graphical user int
ii  libgtk2.0-dev                              2.14.4-0ubuntu1                                      Development files for the GTK+ library
joseph@Netzach:~$ 

```

---

### Post by soro2005 on 2008-11-08
Looks good. :confused: Perhaps:
```
sudo dpkg-reconfigure gnome-panel
```

---

### Post by AntiHeroJoe on 2008-11-08
Just tried your last command, but my re-test continues to spawn the taskbar items. Any other options?

---

### Post by adult swim on 2008-11-08
im pretty sure the desktop and nautilus are related.  try quitting nautilus from a terminal ```
nautilus -q
``` and then start it back up with alt-f2 and then ```
nautilus
```

---

### Post by soro2005 on 2008-11-08
well, better start it from a terminal than with alt+f2, and show us the output.
```
nautilus
```

---

### Post by AntiHeroJoe on 2008-11-08
so I've tried your commands, let me show you some terminal output:

```

joseph@Netzach:~/Desktop$ nautilus -q
joseph@Netzach:~/Desktop$ nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:22184): WARNING **: Unable to add monitor: Not supported
nautilus: symbol lookup error: nautilus: undefined symbol: pango_layout_set_height
joseph@Netzach:~/Desktop$ ls
new file
joseph@Netzach:~/Desktop$

``` 

I run your commands...when I right click on the desktop then select Create Document > empty file, it crashes with the error displayed. The file is there, and no windows are spawning, but now nautilus is dead. If I try to restart it, the same error occurs.

What's up with pango? That's the same error from my other thread!

---

### Post by adult swim on 2008-11-08
run this 
```
sudo apt-get install libpango1.0-0
```
and stop and start nautilus again

---

### Post by AntiHeroJoe on 2008-11-08
Here's the terminal output from what you've suggested. The error still occurs when trying to create the empty file on the desktop.

```

joseph@Netzach:~$ sudo apt-get install libpango1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  apport apturl discover1-data linux-restricted-modules-2.6.22-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joseph@Netzach:~$ nautilus -q
joseph@Netzach:~$ nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:23035): WARNING **: Unable to add monitor: Not supported
nautilus: symbol lookup error: nautilus: undefined symbol: pango_layout_set_height
joseph@Netzach:~$ 

```

---

### Post by adult swim on 2008-11-08
edit: not a good idea

---

### Post by AntiHeroJoe on 2008-11-08
eep, doing that says it would remove 314 items. Is that normal (or safe)?

```

joseph@Netzach:~$ sudo apt-get remove --purge libpango1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  beryl-core libcommons-collections3-java evolution-common mesa-utils
  nvidia-71-modaliases libpurple0 menu syslinux libarts1c2a libtwolame0 junit4
  kdelibs4c2a libartsc0 libmtp8 libmono-security1.0-cil libecj-java
  libcommons-pool-java libcompizconfig0 libglitz-glx1 libpth20
  libsigc++-2.0-dev libwxbase2.8-dbg libatk1.0-dev libportaudio2 libxine1-x
  libsdl-console nvidia-177-modaliases libmono-sharpzip0.84-cil liblucene-java
  beryl-settings-bindings libgda3-common ubuntu-gdm-themes sqlite
  mplayer-skins libotr2 libcommons-el-java libspectre1 x11proto-xinerama-dev
  libsilc-1.1-2 libmono-system-web1.0-cil libbeagle1 junit gthumb-data
  compiz-wrapper libglew1.5 libwpg-0.1-1 python-gdata libregexp-java
  libcommons-modeler-java libxcb-xv0 libdca0 libart2.0-cil
  compizconfig-backend-gconf liblog4j1.2-java libpt-1.10.10-plugins-alsa
  amarok-common libtrackerclient0 libfftw3-3 ubuntu-wallpapers libcairo2-dev
  libsgutils1 totem-common libx11-xcb1 libass1 gvfs-bin
  libpulse-mainloop-glib0 libpt-1.10.10 apport pidgin-data libtomcat5.5-java
  libglide2 libdvbpsi4 libmono-cairo2.0-cil pptp-linux libfontconfig1-dev
  x11proto-composite-dev jockey-common ruby1.8 libbcel-java ttf-liberation
  libhesiod0 libdmx1 libberylsettings0 libvlc2 libxcursor-dev
  libcairomm-1.0-dev libmono-addins0.2-cil ant libcommons-launcher-java ruby
  libcommons-logging-java default-jdk libenca0 vlc-nox python-compizconfig
  default-jre libggi2 libavahi-gobject0 libglibmm-2.4-dev x11proto-damage-dev
  libgii1 python-brlapi libflickrnet2.1.5-cil libxcb-render-util0-dev
  libxcb-shape0 openjdk-6-jdk libmono1.0-cil system-config-printer-common
  libxdamage-dev libcommons-dbcp-java libglitz1 libmono-data-tds1.0-cil
  liblzo2-2 libtunepimp5 libifp4 libmono-system-data1.0-cil fglrx-modaliases
  libgii1-target-x xdg-utils x11proto-fixes-dev libcommons-collections-java
  frozen-bubble-data libcommons-beanutils-java libopal-2.2
  nvidia-173-modaliases libiso9660-5 libgnome-speech7 libxcomposite-dev
  libmozjs0d libsdl-perl libgtkhtml-editor-common pulseaudio-module-zeroconf
  discover1-data libxvmc1 libexpat1-dev libcommons-digester-java
  dmz-cursor-theme python-4suite-xml liblua5.1-0 nvidia-common libmeanwhile1
  libgda3-3 python-pkg-resources filezilla-common libpt-1.10.10-plugins-v4l
  libgpgme11 libmodplug0c2 vlc-data libzephyr3 libpixman-1-dev libxft-dev
  libgconfmm-2.6-1c2 fb-music-high libgnome-keyring1.0-cil libtar
  liblucene-java-doc beryl-plugins-data
  linux-restricted-modules-2.6.22-14-generic libxcb-render0-dev libxul-common
  libruby1.8 libjsch-java gnash-common libxfixes-dev libadns1 sqlite3
  compiz-core libecj-java-gcj libberyldecoration0 libgnome-vfs2.0-cil
  libvlccore0 libxcb-shm0 ant-optional libxinerama-dev libvcdinfo0 libebml0
  transmission-common libmpcdec3 nvidia-96-modaliases libmx4j-java
  libmatroska0 libnjb5 libofa0 wireshark-common libspeexdsp1 libiptcdata0
  python-rdflib libsvncpp1 libpisync1 hwtest
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte* amarok* amarok-engine-xine* apturl* at-spi* beryl* beryl-manager*
  beryl-plugins* beryl-settings* bluez-gnome* brasero* brltty-x11* bug-buddy*
  compiz* compiz-fusion-plugins-extra* compiz-fusion-plugins-main*
  compiz-gnome* compiz-plugins* compizconfig-settings-manager*
  contact-lookup-applet* deskbar-applet* devilspie* eclipse* eclipse-jdt*
  eclipse-pde* eclipse-platform* eclipse-rcp* ekiga* eog* eve* evince*
  evolution* evolution-exchange* evolution-plugins* evolution-webcal* f-spot*
  fast-user-switch-applet* file-roller* filezilla* firefox* firefox-3.0*
  firefox-3.0-branding* firefox-3.0-gnome-support* firefox-gnome-support*
  flashplugin-nonfree* frozen-bubble* fusion-icon* gcalctool* gconf-editor*
  gdebi* gdm* gdm-guest-session* gedit* gens* gimp* gimp-dds* gimp-normalmap*
  gimp-resynthesizer* gimp-texturize* gkrellm* gksu* gnash* gnome-about*
  gnome-accessibility-themes* gnome-app-install* gnome-applets*
  gnome-btdownload* gnome-control-center* gnome-games* gnome-icon-theme*
  gnome-keyring* gnome-mag* gnome-media* gnome-menus* gnome-mount* gnome-mud*
  gnome-netstatus-applet* gnome-nettool* gnome-orca* gnome-panel* gnome-pilot*
  gnome-pilot-conduits* gnome-power-manager* gnome-screensaver* gnome-session*
  gnome-settings-daemon* gnome-spell* gnome-system-monitor*
  gnome-system-tools* gnome-terminal* gnome-themes* gnome-user-guide*
  gnome-utils* gnome-volume-manager* gstreamer0.10-plugins-good*
  gstreamer0.10-x* gthumb* gtk2-engines* gtk2-engines-murrine*
  gtk2-engines-pixbuf* gucharmap* human-theme* hwtest-gtk* jockey-gtk*
  kdebase-runtime* kdebase-runtime-bin-kde4* kdelibs-bin* kdelibs5*
  khelpcenter4* konsole* language-selector* libatspi1.0-0* libavahi-ui0*
  libbonoboui2-0* libcanberra-gnome* libcanberra-gtk-module* libcanberra-gtk0*
  libcryptui0* libdeskbar-tracker* libedataserverui1.2-8* libeel2-2*
  libexchange-storage1.2-3* libgail-gnome-module* libgdl-1-0* libgegl-0.0-0*
  libgimp2.0* libgksu2-0* libgksuui1.0-1* libglade2-0* libglade2-dev*
  libglade2.0-cil* libglademm-2.4-1c2a* libglademm-2.4-dev*
  libgnome-desktop-2-7* libgnome-media0* libgnome-window-settings1*
  libgnome2-canvas-perl* libgnome2-perl* libgnome2.0-cil* libgnomecanvas2-0*
  libgnomekbd3* libgnomekbdui3* libgnomeprint2.2-0* libgnomeprintui2.2-0*
  libgnomeui-0* libgpod-common* libgpod3* libgraphviz4* libgtk-vnc-1.0-0*
  libgtk2-perl* libgtk2.0-0* libgtk2.0-bin* libgtk2.0-cil* libgtk2.0-dev*
  libgtkgl2.0-1* libgtkgl2.0-dev* libgtkglext1* libgtkglext1-dev*
  libgtkhtml-editor0* libgtkhtml2-0* libgtkhtml3.14-19* libgtkmm-2.4-1c2a*
  libgtkmm-2.4-dev* libgtksourceview1.0-0* libgtksourceview2.0-0*
  libgtkspell0* libgucharmap7* libgutenprintui2-1* libgweather1*
  liblaunchpad-integration1* liblpint-bonobo0* libmagick10* libmbca0*
  libmetacity0* libmono-addins-gui0.2-cil* libnautilus-burn4*
  libnautilus-extension1* libnotify1* libpanel-applet2-0* libpango1.0-0*
  libpango1.0-dev* libpangomm-1.4-1* libpangomm-1.4-dev* libpolkit-gnome0*
  libpoppler-glib3* librsvg2-2* librsvg2-common* libsdl-pango1* libsexy2*
  libswt3.2-gtk-java* libswt3.2-gtk-jni* libtotem-plparser12* libtracker-gtk0*
  libvte9* libwmf0.2-7* libwnck22* libwxgtk2.6-0* libwxgtk2.8-0*
  libwxgtk2.8-dbg* libwxgtk2.8-dev* libxine1* libxine1-gnome*
  libxine1-misc-plugins* libxine1-plugins* libxul0d* metacity* mousetweaks*
  mozilla-mplayer* mozilla-plugin-gnash* mplayer* nautilus*
  nautilus-cd-burner* nautilus-sendto* nautilus-share* network-manager-gnome*
  network-manager-pptp* notification-daemon* nvidia-settings*
  obex-data-server* onboard* openoffice.org* openoffice.org-base*
  openoffice.org-calc* openoffice.org-common* openoffice.org-core*
  openoffice.org-draw* openoffice.org-emailmerge* openoffice.org-evolution*
  openoffice.org-filter-binfilter* openoffice.org-filter-mobiledev*
  openoffice.org-gnome* openoffice.org-gtk* openoffice.org-impress*
  openoffice.org-java-common* openoffice.org-math* openoffice.org-officebean*
  openoffice.org-report-builder-bin* openoffice.org-style-human*
  openoffice.org-writer* openoffice.org-writer2latex* padevchooser* paman*
  paprefs* pavucontrol* pavumeter* phonon* phonon-backend-gstreamer* pidgin*
  pidgin-otr* policykit-gnome* python-glade2* python-gmenu* python-gnome2*
  python-gnome2-desktop* python-gnome2-extras* python-gnomecanvas*
  python-gtk2* python-gtkhtml2* python-gtksourceview2*
  python-launchpad-integration* python-notify* python-pyatspi* python-sexy*
  python-uno* python-virtkey* python-vte* rapidsvn* rhythmbox* rss-glx* scim*
  scim-bridge-agent* scim-bridge-client-gtk* scim-gtk2-immodule*
  scim-modules-table* scim-tables-additional* screensaver-default-images*
  seahorse* seahorse-plugins* serpentine* software-properties-gtk*
  sound-juicer* ssh-askpass-gnome* sun-java6-plugin* synaptic*
  system-config-printer-gnome* tangerine-icon-theme* tango-icon-theme-common*
  tomboy* totem* totem-gstreamer* totem-mozilla* totem-plugins* totem-xine*
  tracker* tracker-search-tool* transmission-gtk* tsclient* ubuntu-artwork*
  ubuntu-docs* update-manager* update-notifier* usb-creator* vinagre* vino*
  vlc* wireshark* xdg-user-dirs-gtk* xsane* xscreensaver-data*
  xscreensaver-gl* xulrunner-1.9* xulrunner-1.9-gnome-support* yelp* zenity*
0 upgraded, 0 newly installed, 314 to remove and 0 not upgraded.
After this operation, 1099MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
joseph@Netzach:~$
```

---

### Post by adult swim on 2008-11-08
NO!  dont do that!  im stumped here.

---

### Post by soro2005 on 2008-11-08
No, you can't do purge on libpango. It's going to uninstall everything that's using gtk and gdk!

In any case, this is the same problem you have with your alacarte. Something's not correct between libpango and gtk, and perhaps the gtk python bindings. So the task is to fix that. Let's think.

First off, you want to do
```
sudo aptitude reinstall libpango1.0-0
```

---

### Post by soro2005 on 2008-11-08
Additional idea: I've seen in the "proposed" section that there's a replacement for all the gnome panel stuff, including our beloved libpango here. If you feel adventurous (well not thaaaat adventurous really, but there's a certain possibility of additional breakage), you could open synaptic, then settings --> repository --> updates and enable the "intrepid-proposed" section. Then
```
sudo apt-get update && sudo apt-get upgrade
```
If this solves it, you may want to disable the "proposed" section afterward so you're not caught flat footed at some point in the future.

Also, is there any software you have compiled and installed from source? Any packages from other distros, perhaps Debian?

---

### Post by AntiHeroJoe on 2008-11-09
Tried to reinstall pango, no luck. Tried updating from proposed updates and nothing change.

I tried again to reinstall pango and I'm getting this:

From apt:
```
Reinstallation of libpango1.0-0 is not possible, it cannot be downloaded.
```

From aptitude:
```
E: I wasn't able to locate file for the libpango1.0-0 package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the libpango1.0-0 package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```

---

### Post by soro2005 on 2008-11-09
The last error is because you have disabled the "proposed" section after upgrading --> you would have to enable the section again before you can reinstall the same packages. This error will go away as the packages are released to the main repository. --> No problem.

Can you give us
```
ldd $(which nautilus)
```
please?

---

### Post by AntiHeroJoe on 2008-11-09
I found an entry in launchpad with pretty much the same exact issues ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/289237](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/289237)). One person in the thread solved it by compiling and installing from source. I've tried that myself, but I continue to get the same nautilus message regarding pango (pango_layout_set_height).

---

### Post by AntiHeroJoe on 2008-11-09
```
joseph@Netzach:~/Desktop$ ldd $(which nautilus)
	linux-gate.so.1 =>  (0xb8025000)
	libnautilus-extension.so.1 => /usr/lib/libnautilus-extension.so.1 (0xb7fe6000)
	libeel-2.so.2 => /usr/lib/libeel-2.so.2 (0xb7f81000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0xb7f78000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb7f61000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7e25000)
	librsvg-2.so.2 => /usr/lib/librsvg-2.so.2 (0xb7df2000)
	liblaunchpad-integration.so.1 => /usr/lib/liblaunchpad-integration.so.1 (0xb7ded000)
	libgnome-desktop-2.so.7 => /usr/lib/libgnome-desktop-2.so.7 (0xb7dc6000)
	libgnomeui-2.so.0 => /usr/lib/libgnomeui-2.so.0 (0xb7d3b000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb7d0a000)
	libgnome-2.so.0 => /usr/lib/libgnome-2.so.0 (0xb7cf4000)
	libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb7c98000)
	libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb7c82000)
	libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb7c2e000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7890000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7804000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb77e8000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb77ce000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb775b000)
	libpango-1.0.so.0 => /usr/local/lib/libpango-1.0.so.0 (0xb771e000)
	libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb76ec000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb76e6000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb767e000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7640000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb763a000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7583000)
	libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0xb757a000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb748b000)
	libexif.so.12 => /usr/lib/libexif.so.12 (0xb7461000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb743b000)
	libexempi.so.3 => /usr/lib/libexempi.so.3 (0xb738f000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb7375000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb735c000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb71fe000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb71f4000)
	libpangocairo-1.0.so.0 => /usr/local/lib/libpangocairo-1.0.so.0 (0xb71ea000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb71e6000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb71e3000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb71de000)
	libpangoft2-1.0.so.0 => /usr/local/lib/libpangoft2-1.0.so.0 (0xb71b7000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7140000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb712a000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb70fd000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb70f9000)
	libgsf-1.so.114 => /usr/lib/libgsf-1.so.114 (0xb70c5000)
	libcroco-0.6.so.3 => /usr/lib/libcroco-0.6.so.3 (0xb7091000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb7089000)
	libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0xb702c000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7015000)
	libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb6fb8000)
	libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0xb6fa7000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb6f9d000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb6f85000)
	libesd.so.0 => /usr/lib/libesd.so.0 (0xb6f7a000)
	libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb6f55000)
	libpopt.so.0 => /lib/libpopt.so.0 (0xb6f4b000)
	libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb6f44000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb6f3b000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb6f2c000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6f29000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb6f1f000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6f15000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb6ed3000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6ead000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0xb6ea8000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0xb6ea0000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6e86000)
	libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0xb6e69000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0xb6e31000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb6e07000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6e04000)
	/lib/ld-linux.so.2 (0xb800b000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6ddc000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb6ced000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6cde000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb6ccd000)
	libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0xb6c2f000)
	libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0xb6c2b000)
	libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0xb6c1f000)
	libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0xb6c0e000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb6bfa000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb6bf5000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb6b2d000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6b2a000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6b25000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb6b0c000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb6af9000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb6a90000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb6a8c000)
joseph@Netzach:~/Desktop$
```

---

### Post by soro2005 on 2008-11-09
See, you're using the libpango library from /usr/local/lib, not the one that comes with Ubuntu and which is in /usr/lib. That's the result of installing non-Ubuntu packages, or of compiling programs and installing them from source without making sure you're not duplicating libraries and spreading them all over the place.

As far as I can see from a quick glance, those are the only libraries in a non-standard location. Can you post the output of
```
ls /usr/local/lib
```

---

### Post by AntiHeroJoe on 2008-11-09
```
joseph@Netzach:~$ ls /usr/local/lib
eclipse                               libgtkglext-x11-1.0.a
gtkglext-1.0                          libgtkglext-x11-1.0.la
libanimorph.a                         libgtkglext-x11-1.0.so
libanimorph.la                        libgtkglext-x11-1.0.so.0
libanimorph.so                        libgtkglext-x11-1.0.so.0.0.0
libanimorph.so.0                      libmhgui.a
libanimorph.so.0.0.0                  libmhgui.la
libCEGUIBase.la                       libmhgui.so
libCEGUIBase.so                       libmhgui.so.0
libCEGUIBase.so.1                     libmhgui.so.0.0.0
libCEGUIBase.so.1.0.0                 libNxCharacter.so
libCEGUIDevILImageCodec.la            libNxCharacter.so.1
libCEGUIDevILImageCodec.so            libNxCooking.so
libCEGUIDevILImageCodec.so.0          libNxCooking.so.1
libCEGUIDevILImageCodec.so.0.0.0      libOgreMain-1.4.5.so
libCEGUIExpatParser.la                libOgreMain-1.4.7.so
libCEGUIExpatParser.so                libOgreMain.la
libCEGUIExpatParser.so.0              libOgreMain.so
libCEGUIExpatParser.so.0.0.0          libOIS-1.0.0.so
libCEGUIFalagardWRBase.la             libOIS-1.2.0.so
libCEGUIFalagardWRBase.so             libOIS.a
libCEGUIFalagardWRBase.so.1           libOIS.la
libCEGUIFalagardWRBase.so.1.0.0       libOIS.so
libCEGUIFreeImageImageCodec.la        libpango-1.0.la
libCEGUIFreeImageImageCodec.so        libpango-1.0.so
libCEGUIFreeImageImageCodec.so.0      libpango-1.0.so.0
libCEGUIFreeImageImageCodec.so.0.0.0  libpango-1.0.so.0.1900.0
libCEGUILibxmlParser.la               libpangocairo-1.0.la
libCEGUILibxmlParser.so               libpangocairo-1.0.so
libCEGUILibxmlParser.so.0             libpangocairo-1.0.so.0
libCEGUILibxmlParser.so.0.0.0         libpangocairo-1.0.so.0.1900.0
libCEGUIOgreRenderer-1.4.7.so         libpangoft2-1.0.la
libCEGUIOgreRenderer.la               libpangoft2-1.0.so
libCEGUIOgreRenderer.so               libpangoft2-1.0.so.0
libCEGUIOpenGLRenderer.la             libpangoft2-1.0.so.0.1900.0
libCEGUIOpenGLRenderer.so             libpangox-1.0.la
libCEGUIOpenGLRenderer.so.0           libpangox-1.0.so
libCEGUIOpenGLRenderer.so.0.0.1       libpangox-1.0.so.0
libCEGUISampleHelper.la               libpangox-1.0.so.0.1900.0
libCEGUISampleHelper.so               libpangoxft-1.0.la
libCEGUISampleHelper.so.1             libpangoxft-1.0.so
libCEGUISampleHelper.so.1.0.0         libpangoxft-1.0.so.0
libCEGUITGAImageCodec.la              libpangoxft-1.0.so.0.1900.0
libCEGUITGAImageCodec.so              libPhysXCore.so
libCEGUITGAImageCodec.so.0            libPhysXCore.so.1
libCEGUITGAImageCodec.so.0.0.0        libPhysXLoader.so
libCEGUITinyXMLParser.la              libPhysXLoader.so.1
libCEGUITinyXMLParser.so              libpurple.la
libCEGUITinyXMLParser.so.0            libpurple.so
libCEGUITinyXMLParser.so.0.0.0        libpurple.so.0
libcodeblocks.la                      libpurple.so.0.0.2
libcodeblocks.so                      OGRE
libcodeblocks.so.0                    pango
libcodeblocks.so.0.0.1                pidgin
libgdkglext-x11-1.0.a                 pkgconfig
libgdkglext-x11-1.0.la                purple-2
libgdkglext-x11-1.0.so                python2.5
libgdkglext-x11-1.0.so.0              site_ruby
libgdkglext-x11-1.0.so.0.0.0
joseph@Netzach:~$
```

---

### Post by soro2005 on 2008-11-09
Well, that's a lot, including the python stuff which might be responsible for your problem with alacarte.

In general, the /usr/local directory structure is going to contain stuff which you have installed on your own, not the one from Ubuntu repositories. This may conflict with the libraries that Ubuntu installs, as in this case, where Nautilus is trying to use methods and objects from libpango, but is being served with an old version from /usr/local/lib, instead of the current one.

So safest, and cleanest, I believe, would be to try to remember all the programs you have installed from source, and uninstalling them with (sudo make uninstall from the directory in which you have compiled them). If that's not an option and you want to procede with care and deliberation, you can begin with moving the pango related stuff out of that directory and to some backup location. If you want to get out the axe, just move the entire /usr/local/lib directory somewhere else, and see what that solves and whether it produces new problems.
```
sudo mv /usr/local/lib backup-location
```
You will only help yourself down the road if you use the opportunity to also look into the pidgin related clutter you've collected there, never mind python, and the gdk gl stuff might also be in the way of your Gnome bliss.

For good measure, and after you move libraries around, I believe you will have to update your links with
```
sudo ldconfig
```
Then log out and in of Gnome, or even restart.

---

### Post by AntiHeroJoe on 2008-11-09
:):):):):):):):)

A million smileys for you! I moved the entire contents of usr/local/lib to another dir, ran sudo ldconfig, restarted my machine, and everything works now! Brilliant!

Now, just for future knowledge: should anything ever go in usr/local/lib?

---

### Post by soro2005 on 2008-11-09
Well, /usr/local is part of the infrastructure, so it must be good for something. But for our pedestrian purposes, I guess it should remain empty.

I'm no pro on these issues, but it is my understanding that the preferred location also for your self-compiled stuff in Ubuntu systems is in /usr. Normally, you can define this upon compilation, e.g.
```
./configure --prefix=/usr
```
But in any case, I think it is an extremely good idea to keep track of what you compile and install, and what regular Ubuntu packaged files you overwrite. If you install things insto /usr, you may, of course, be producing another pandemonium by overwriting packaged libraries with faulty stuff or wrong versions. But if it's in the location Ubuntu knows, then I would believe that it's possible to just reinstall the Ubuntu package to get back to normal.

Bottom line: Wherever possible, install packages so that the package managers can keep track of the mess you're doing. If you need to compile from source, try hard to produce a package that you can install. Use debian/rules if it exists, and checkinstall if it doesn't. If you cannot produce a package, keep the directory with the source, and keep it configured, so that you can just uninstall from there should need be.

Now, if somebody wants to correct me on any of these points, please do so for my own education. :popcorn:

---

