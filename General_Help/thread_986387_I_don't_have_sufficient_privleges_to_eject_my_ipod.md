---
title: "I don't have sufficient privleges to eject my ipod?"
date: 2008-11-18
forum: General Help
---

### Post by fINTiP on 2008-11-18
When I try to eject my ipod 6G, it tells me I When I try and unmount it, it says "You are not privleged to eject the volume IPOD". When I try to unmount it, it says there's a program accessing it... I don't know what that would be, as I have closed floola, and no nautilus open has it in view.

However, while it doesn't look unmounted, if I then right-click on it, it has the option to either eject, or mount... which almost makes it look unmounted?

My ipod still says it is connected the whole time. :\

Here's a cp of my pstree output, if that helps...

```
init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-autoipd&#9472;&#9472;&#9472;avahi-autoipd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;baobab
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;61*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dd
     &#9500;&#9472;dhclient
     &#9500;&#9472;dhclient3
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data-}]
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;8*[{firefox}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;compiz&#9472;&#9472;&#9472;compiz.real&#9472;&#9516;&#9472;sh&#9472;&#9472;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                             &#9474;                      &#9474;                     &#9500;&#9472;gnome-pty-helpe
     &#9474;                             &#9474;                      &#9474;                     &#9492;&#9472;{gnome-terminal}
     &#9474;                             &#9474;                      &#9500;&#9472;sh&#9472;&#9472;&#9472;compiz-decorato&#9472;&#9472;&#9472;gtk-window-deco
     &#9474;                             &#9474;                      &#9492;&#9472;sh&#9472;&#9472;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;top
     &#9474;                             &#9474;                                            &#9500;&#9472;gnome-pty-helpe
     &#9474;                             &#9474;                                            &#9492;&#9472;{gnome-terminal}
     &#9474;                             &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;{evolution-alarm}
     &#9474;                             &#9500;&#9472;gnome-panel&#9472;&#9472;&#9472;{gnome-panel}
     &#9474;                             &#9500;&#9472;gnome-settings-&#9472;&#9516;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;                             &#9474;                 &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9474;                             &#9474;                 &#9492;&#9472;{gnome-settings-}
     &#9474;                             &#9500;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9474;                             &#9500;&#9472;python
     &#9474;                             &#9500;&#9472;scim
     &#9474;                             &#9500;&#9472;seahorse-agent
     &#9474;                             &#9500;&#9472;ssh-agent
     &#9474;                             &#9500;&#9472;update-notifier
     &#9474;                             &#9492;&#9472;{x-session-manag}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-computer&#9472;&#9472;&#9472;{gvfsd-computer}
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-cpuf
     &#9474;                    &#9500;&#9472;hald-addon-dell
     &#9474;                    &#9500;&#9472;hald-addon-inpu
     &#9474;                    &#9492;&#9472;2*[hald-addon-stor]
     &#9500;&#9472;hcid&#9472;&#9472;&#9472;2*[bluetoothd-serv]
     &#9500;&#9472;klogd
     &#9500;&#9472;mixer_applet2&#9472;&#9472;&#9472;{mixer_applet2}
     &#9500;&#9472;notification-da
     &#9500;&#9472;padevchooser
     &#9500;&#9472;pidgin&#9472;&#9472;&#9472;2*[{pidgin}]
     &#9500;&#9472;scim-bridge
     &#9500;&#9472;scim-helper-man
     &#9500;&#9472;2*[scim-launcher]
     &#9500;&#9472;scim-panel-gtk&#9472;&#9472;&#9472;{scim-panel-gtk}
     &#9500;&#9472;skype&#9472;&#9472;&#9472;7*[{skype}]
     &#9500;&#9472;sshd
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;timidity
     &#9500;&#9472;transmission&#9472;&#9472;&#9472;{transmission}
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd
     &#9492;&#9472;xinetd

```

Any other ideas as to what is going on?:confused:

L

---

### Post by Cracauer on 2008-11-18
Bump.

This is some kind of 8.04 LTS issue.

I use commandline tools and a "user" mount entry in fstab to mount and unmount on the commandline without becoming root.

Since the upgrade to 8.04 and no other changes that still works, except that "eject /dev/sdi" no longer works.

---

### Post by Cracauer on 2008-11-18
After some snooping I found what changed in newer Ubuntu:

The group that udev sets on the device is now "disk". In older version it seems to have been "floppy". Permissions are 660, so you need to be in the group.

Ubuntu seems to put mortal users into group "floppy" by default but (obviously) not into group "disk".

This looks like a straight regression from older versions. Clearly the device of things that are getting mounted automatically to the user's desktop should be group "floppy", user mount should equal user eject. 

Apparently that got fatfingered somewhere in some package upgrade or another. i think the place to fix is udev's defaults which now either seem to misidentify iPods or reclassified iPods.

---

