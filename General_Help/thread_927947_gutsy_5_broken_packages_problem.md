---
title: "gutsy 5 broken packages problem"
date: 2008-09-23
forum: General Help
---

### Post by iVEKK on 2008-09-23
i have 5 broken packages: "gnome2-globalmenu-applet" "gtk2.0-examples" "gtk2-engines-pixbuf" "libgtk2.0-0" and "libgtk2.0-bin"

i cant access update manager because it says software index is broken and suggests to execute command sudo apt-get install -f... When i execute sudo apt-get install -f system wants to remove all packages on ubuntu. why is that? 
also i cant access add/remove programs

is there any way to fix broken packages?

hope you can help me with my problem.. thanks

---

### Post by kokkus on 2008-09-23
Packages are located under /var/cache/apt/archives
You can delete them from there.

EDIT: But how do you know that these 5 packages are the broken packages?

---

### Post by iVEKK on 2008-09-23
> **kokkus said:**
> Packages are located under /var/cache/apt/archives
You can delete them from there.

hmm no packages in that folder.. only folder named "partial" and some unknown file named "lock" ...

---

### Post by kokkus on 2008-09-23
Ok so they are updated packages from the update manager?
Search for the packages and delete them then.
GO to terminal, type gksudo nautilus, now go to filesystem, click ctrl+f to open the search bar. Now you can search for the packages and delete them.

---

### Post by iVEKK on 2008-09-23
> **kokkus said:**
> Ok so they are updated packages from the update manager?

no they are not.. because i cant start update manager.. those are old packages.. but why when i type sudo apt-get install -f in terminal he wants to delete all packages on system? even when i go to synaptics and filter broken packages.. mark them for removal.. synaptics wants to delete all packages on system?
that's my problem... i've tried to search packages with nautilus but none found :(

---

### Post by iVEKK on 2008-09-23
any1 know solution to this problem? i'm kinda desperate.. can't install anything on ubuntu :S

---

### Post by iVEKK on 2008-09-23
btw when i run sudo apt-get install -f i get following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a kdelibs4c2a libartsc0 automake1.9 gnome-pkg-tools
  fftw3 kdelibs-data libxcb-xv0 m4 liblualib50 autoconf mysql-common
  libmysqlclient15off intltool ruby1.8 libtool kdebase-kio-plugins libxcb1
  gettext python-qt3 ruby libkonq4 libavahi-qt3-1 gnome-common python-sip4
  kdebase-bin autotools-dev libxcb-shape0 libtunepimp5 libifp4
  libdbus-qt-1-1c2 kdesktop libxvmc1 libpq5 libmodplug0c2 libpulse0 libqt3-mt
  patch liblua50 libruby1.8 libxcb-shm0 libmpcdec3 libnjb5 libofa0 libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf automake1.9 autotools-dev gettext gnome-common gnome-pkg-tools
  intltool libc6-dev libtool linux-libc-dev m4 patch
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc cvs gettext-doc glibc-doc manpages-dev libtool-doc g77
  fortran77-compiler gcj diff-doc
Recommended packages:
  automaken svn-buildpackage libltdl3-dev
The following packages will be REMOVED:
  alacarte amarok amarok-xine apport-gtk apturl at-spi
  avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr bluez-gnome
  bootchart brltty-x11 bug-buddy compiz compiz-gnome compiz-plugins
  contact-lookup-applet deskbar-applet displayconfig-gtk ekiga eog evince
  evolution evolution-exchange evolution-plugins evolution-webcal f-spot
  fast-user-switch-applet file-roller firefox firefox-gnome-support
  flashplugin-nonfree gcalctool gconf-editor gdebi gdm gedit gimp gimp-print
  gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install
  gnome-applets gnome-btdownload gnome-control-center gnome-games
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media
  gnome-menus gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca
  gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-screensaver gnome-session gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-themes gnome-user-guide gnome-utils
  gnome-volume-manager gnome2-globalmenu-applet gstreamer0.10-plugins-good
  gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks
  gtk2.0-examples gtkhtml3.14 gucharmap hal-cups-utils hal-device-manager
  human-theme hwdb-client-gnome language-selector language-support-en
  libatspi1.0-0 libawn0-bzr libbonoboui2-0 libdeskbar-tracker
  libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-3 libgail-common
  libgail-gnome-module libgail18 libgconf2.0-cil libgdl-1-0 libgdl-gnome-1-0
  libgimp2.0 libgksu2-0 libgksuui1.0-1 libglade2-0 libglade2.0-cil
  libgnome-desktop-2 libgnome-keyring0 libgnome-window-settings1
  libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomekbd1 libgnomekbdui1 libgnomeprintui2.2-0 libgnomeui-0 libgpod2
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0
  libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmm-2.4-1c2a
  libgtksourceview1.0-0 libgtksourceview2.0-0 libgtkspell0 libgucharmap6
  libgutenprintui2-1 liblaunchpad-integration0 liblpint-bonobo0 libmetacity0
  libnautilus-burn4 libnautilus-extension1 libnotify1 libpanel-applet2-0
  libpoppler-glib2 librsvg2-2 librsvg2-bin librsvg2-common librsvg2.0-cil
  libsexy2 libtotem-plparser7 libtracker-gtk0 libvte9 libwmf0.2-7 libwnck22
  metacity mozilla-firefox-locale-en-gb nautilus nautilus-cd-burner
  nautilus-sendto network-manager-gnome notification-daemon nvidia-glx-new
  onboard openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-thesaurus-en-us
  openoffice.org-writer pidgin python-at-spi python-awn-bzr python-glade2
  python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas
  python-gtk2 python-gtkhtml2 python-launchpad-integration python-notify
  python-pygtksourceview python-sexy python-uno python-virtkey python-vte
  restricted-manager rhythmbox scim scim-gtk2-immodule scim-modules-table
  scim-tables-additional screensaver-default-images serpentine
  software-properties-gtk sound-juicer ssh-askpass-gnome startupmanager
  sun-java6-plugin synaptic system-config-printer tangerine-icon-theme
  thunderbird-locale-en-gb tomboy totem totem-gstreamer totem-mozilla tracker
  tracker-search-tool tsclient ubufox ubuntu-artwork ubuntu-desktop
  ubuntu-docs update-manager update-notifier vino xdg-user-dirs-gtk xsane
  xscreensaver-data xscreensaver-gl yelp zenity
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev gettext gnome-common gnome-pkg-tools
  intltool libc6-dev libtool linux-libc-dev m4 patch
0 upgraded, 12 newly installed, 230 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 7103kB/7199kB of archives.
After unpacking 869MB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by kokkus on 2008-09-23
OK have you ever try to fix the broken packages from kernel under the grub menu?
Or if that doesn't work, try sudo --fix-missing

---

### Post by iVEKK on 2008-09-23
nope didnt try under kernel.. can u tell me procedure? i'm newb for ubuntu :)

btw i tried from terminal sudo --fix-missing and pops out this:

sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#ui

---

### Post by kokkus on 2008-09-23
Ok, reboot your PC, Click escape before the bootscreen comes up.
Now you are in the grub menu.
Now go to recovery mode and wait for the new menu with a blue background.
Now put the ubuntu cd in and choose "Try To Fix Broken Packages" from the menu with blue background.

---

### Post by iVEKK on 2008-09-23
thanks i'll try right now :) hope it works

---

### Post by iVEKK on 2008-09-23
> **kokkus said:**
> Ok, reboot your PC, Click escape before the bootscreen comes up.
Now you are in the grub menu.
Now go to recovery mode and wait for the new menu with a blue background.
Now put the ubuntu cd in and choose "Try To Fix Broken Packages" from the menu with blue background.

when i press go to recovery mode it throws me to command line as root@ like i'm in terminal but just as root.. what command do i need to use to fix packages?

---

