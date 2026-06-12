---
title: "Ubuntu to Xubuntu"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by nocto on 2009-03-08
I've been playing around with a few different distros.  I currently dual boot ubuntu/xp pro, but I want to delete ubuntu and install xubuntu instead.  I did a search and found a list of commands to use synaptic to remove/install various packages to switch it, but I'd rather not go that route.  I'm hoping for a quick guide on how to delete ubuntu so I can use xubuntu instead.

---

### Post by lloyd_b on 2009-03-08
You don't need (and probably don't want) to actually delete all of the Ubuntu components (unless you are short of disk space on that machine).
```
sudo apt-get install xubuntu-desktop
```to install the Xfce4 desktop, and then at the login screen select "session type" and "Xfce".  This will give you exactly the same desktop that you'd get if you had installed Xubuntu instead of Ubuntu (as well as all of the supporting programs).

Doing it this way makes it easy to change back if you decide you don't actually like Xubuntu...

Lloyd B.

---

### Post by Neo_The_User on 2009-03-08
Well that command he told you is to still have Ubuntu running but with the Xfce desktop and Xubuntu apps.

First burn Xubuntu onto a CD.

Now you want to REPLACE Ubuntu with Xubuntu, delete the partitions Ubuntu is stored on using fdisk.

EXAMPLE:

```

sudo fdisk -l /dev/sda

```

replace sda with whatever your partitions are stored on. It says in /etc/fstab if you're not sure.

Now that you've found the exact partitons Ubuntu is stored on, delete them using fdisk -d.

EXAMPLE:

```

sudo fdisk -d /dev/sda1
sudo fdisk -d /dev/sda5

```

**_[SIZE="5"]PLEASE NOTE THAT THOSE COMMANDS WILL DELETE ALL DATA ON THOSE PARTITIONS! BE SURE TO REPLACE /DEV/SDA1 AND /DEV/SDA5 WITH YOUR LINUX ROOT PARTITION AND SWAP PARTITION! BE SURE TO DOUBLE CHECK BECAUSE NOT 100% OF THE TIME IT IS STORED ON THOSE PARTITIONS[/SIZE]_**

---

### Post by Jose Catre-Vandis on 2009-03-08
Hmmm third perhaps balanced view :)

lloyd_b suggests a good halfway house for you to try out xubuntu (or the xfce desktop) without having to go radical and uninstall anything. You might find you prefer ubuntu gnome after all. Lloyd_b's way will give a false sense of xubuntu as just installing the desktop will retain everything that you had in ubuntu.

If you are looking for a clean xubuntu then Neo_the_user's radical clean out is the way to go, but you will use all your settings.

You don't have to wipe your disk, as the partitioner in the xubuntu setup will allow you do manually select the partition you want to install xubuntu on (which will be where ubuntu is at present. But as Neo says, its worth checking and noting where your OS's are on the partition table.

A third way would be to triple boot. if you have the sapce, create a new partition, say no more than 10GB, that you can do a clean install of xubuntu on. This will mean you can retain your ubuntu install for failsafe, going back to or back up. You will need gparted (installed on ubuntu by default) to reshape your partitions. Xubuntu will set up a new grub with all your OS's listed so you can choose at boot time.

---

### Post by cc8balla on 2009-03-08
Why is every solution in this thread hard? Please OP, I hope you didnt do a reinstall. 

Here is what to do:

Either in Synaptic, search for xubuntu, and install xubuntu-desktop. Or in a terminal type

```
sudo apt-get install xubuntu-desktop
```

Then, once that is done, log out, log back in under XFCE session, then go here:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

And then go from there. Its pretty simple, really.

---

### Post by Neo_The_User on 2009-03-08
Going from Ubuntu to Xubuntu means there is no Ubuntu anymore. If the topic said "Ubuntu with an XFCE desktop" then you would be correct but since it says Ubuntu to Xubuntu, a deletion of the Ubuntu partitions would be needed (or you can have a HDD mess and have Ubuntu, Xubuntu and Windows all on different partitions but that'd be a waste and yet again, that wouldn't be what he is looking for.)

Just for the record, he says, "I'm hoping for a quick guide on how to delete ubuntu so I can use xubuntu instead."

This is why I am correct.

\\:D/ :tongue:

Oh and if you don't like the fdisk interface, cfdisk looks a bit prettier and its only launched from 1 command.

```

sudo cfdisk

```

Mr. Vandis, I think in the installation it asks you what you want to do with GRUB. Xubuntu does not necessarily have it's grub if you choose to "keep the package maintainer's version installed." ;)

---

### Post by Jose Catre-Vandis on 2009-03-08
> **Neo_The_User said:**
> Going from Ubuntu to Xubuntu means there is no Ubuntu anymore. If the topic said "Ubuntu with an XFCE desktop" then you would be correct but since it says Ubuntu to Xubuntu, a deletion of the Ubuntu partitions would be needed (or you can have a HDD mess and have Ubuntu, Xubuntu and Windows all on different partitions but that'd be a waste and yet again, that wouldn't be what he is looking for.)

Just for the record, he says, "I'm hoping for a quick guide on how to delete ubuntu so I can use xubuntu instead."

This is why I am correct.

\\:D/ :tongue:

Oh and if you don't like the fdisk interface, cfdisk looks a bit prettier and its only launched from 1 command.

```

sudo cfdisk

```

Mr. Vandis, I think in the installation it asks you what you want to do with GRUB. Xubuntu does not necessarily have it's grub if you choose to "keep the package maintainer's version installed." ;)

I go along with what you say :) You did give a nice quick and easy guide. I was simply offering another option into the mix.

With reference to grub, it's easier to let the last linux install's grub go to the mbr becasue it will pick up all the other OS's automagically, and this will save having to manually configure the existing grub to boot the last install. All depends on how comfortable you are with configurations.

Great to have all these alternatives :)

---

### Post by Neo_The_User on 2009-03-08
> **Jose Catre-Vandis said:**
> I go along with what you say :) You did give a nice quick and easy guide. I was simply offering another option into the mix.

With reference to grub, it's easier to let the last linux install's grub go to the mbr becasue it will pick up all the other OS's automagically, and this will save having to manually configure the existing grub to boot the last install. All depends on how comfortable you are with configurations.

Great to have all these alternatives :)

Thank you.

---

### Post by zvacet on 2009-03-08
Isn´t this simple enough

```
sudo apt-get remove alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support && sudo apt-get install xubuntu-desktop
```

---

### Post by Neo_The_User on 2009-03-08
Don't do the command he told you to do! Its dangerous! How did you get over 5,000 posts and aren't banned???? That will destroy linux. Not fix it. I reported your post too. Don't be tellin people to do dangerous commands.

---

### Post by cc8balla on 2009-03-09
But why go into reformatting/repartitioning/reinstalling, when Ubuntu and Xubuntu are one in the same, save for the desktop environment!

The way I said that it should be done, is the simplest way. You could even change the boot screen, and everything to an Xubuntu boot screen if you really wanted to. Add the XFCE DE, and apps that come with Xubuntu (which you get from installing the xubuntu-desktop package), remove GNOME and its apps, and you have a base Xubuntu install. Not saying you are wrong, but you are adding in a ton of time and effort, for something that will take literally 15 mins to do. 

This is why I'm correct. ;)

I know what the OP said, but this is the simpler way. Unless there is an ulterior motive for wanting to do things the hard way, i.e. he messed up a partition or something of the sort.

---

### Post by Neo_The_User on 2009-03-09
No you are not because Ubuntu would still exist on the hard drive. No matter how much you cover Ubuntu up, it's never "erased" until you remove it's partition and do a clean install of Xubuntu. Now... let's stop arguing shall we? I'm right, deal with it. Can a moderator please lock this thread now before the flame wars start?

---

### Post by cc8balla on 2009-03-09
> **Neo_The_User said:**
> No you are not because Ubuntu would still exist on the hard drive. No matter how much you cover Ubuntu up, it's never "erased" until you remove it's partition and do a clean install of Xubuntu. Now... let's stop arguing shall we? I'm right, deal with it.

They are one in the same, just a different DE. 

You are not right here, deal with it. Ubuntu and Xubuntu are literally the same OS.

Not trying to argue with you, but when there is a simpler way to do things, the OP has a right to know :D

---

### Post by Neo_The_User on 2009-03-09
It doesn't matter if they are the same OS or not. They have different names and the topic is Ubuntu to Xubuntu, not "the easy Ubuntu to Xubuntu cover up." The difference between Ubuntu and Xubuntu is by 1 letter and no they aren't the same OS. Xubuntu has less updates. Do a fresh install of Ubuntu 8.10 and then check for updates. It will be at like 200. Xubuntu has 140.

---

### Post by cc8balla on 2009-03-09
I'm struggling to see what is so hard to understand about this. The only difference between the two is the desktop environment. So you install everything that is in an Xubuntu install, and then completely remove GNOME. And there you have it, the same thing you would have if you did a fresh install. Only without the time, and hassle invested to reinstall, delete partitions, etc. 

Do I need to draw you a picture, young one?

---

### Post by macogw on 2009-03-09
Alright kids, everybody out of the pool!

Installing xubuntu-desktop while you have Ubuntu installed will let you choose at login whether you want to use GNOME or XFCE.  Xubuntu only means "Ubuntu with XFCE" as opposed to "Ubuntu with GNOME" or "Ubuntu with KDE" (Kubuntu).

If you want to ditch GNOME, however, destroying the partitions is **NOT NECESSARY!!!**  What Neo posted is highly dangerous.  

The correct (and **SAFE**) thing to do would be to simply reinstall with a Xubuntu CD and choose the partition where Ubuntu is as the install place.  It'll take care of deleting the old Ubuntu stuff and replacing it with Xubuntu for you.


*sigh* 
Neo:
Please DO NOT tell people to destroy partitions that have no need of being destroyed.  Besides that you forgot to say to do it from a live cd so they'd actually just end up with a ruined system.

---

