---
title: "jaunty jackalope broke proprietary nvidia drivers"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Miles_Prower on 2009-04-30
I upgraded to ubuntu 9.04 recently, and when I logged in, I got an error about no screen being available. After a bit, I got the machine to boot to a GUI by reverting to default x settings. This, it turned out, disables the proprietary nvidia drivers I'd been using. I noticed that desktop effects had been disabled and wanted to spiff up the new notifications, so I tried reinstalling the hardware drivers from system>administration>hardware drivers. It kept failing without an error message, so I installed the nvidia-glx-173 and linux-restricted-modules packages, then ran nvidia-xconfig, followed by pkill x. This restarted the x server and brought me the same error message: ...something about no screen being available, or a screen being available, but not having usable settings". I know that's subpar error reporting, so if someone could tell me where to look, I'd be happy to dig up some error logs. I don't know where X keeps them, though. Would my .xsession-errors help? Here, see it:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-1tDemt/socket
SSH_AUTH_SOCK=/tmp/keyring-1tDemt/socket.ssh
Window manager warning: Failed to read saved session file /home/taels/.config/metacity/sessions/108fdd0f4a2189550d124114057610069600000050950022.ms: Failed to open file '/home/taels/.config/metacity/sessions/108fdd0f4a2189550d124114057610069600000050950022.ms': No such file or directory
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/taels/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/taels/.config/tracker/tracker.cfg'
Failure: Module initalization failed
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
** (gnome-panel:5269): DEBUG: Adding applet 0.
** (gnome-panel:5269): DEBUG: Initialized Panel Applet Signaler.
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/taels/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/taels/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/taels/.local/share/tracker/trackerd.log'
** (gnome-panel:5269): DEBUG: Adding applet 1.
** (gnome-panel:5269): DEBUG: Adding applet 2.
** (nm-applet:5287): DEBUG: applet_common_device_state_changed
** (nm-applet:5287): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:5287): DEBUG: applet_common_device_state_changed
** (gnome-panel:5269): DEBUG: Adding applet 3.
** (gnome-panel:5269): DEBUG: Adding applet 4.
** (gnome-panel:5269): DEBUG: Adding applet 5.
** (gnome-panel:5269): DEBUG: Adding applet 6.
** (gnome-panel:5269): DEBUG: Adding applet 7.
** (gnome-panel:5269): DEBUG: Adding applet 8.
** (gnome-panel:5269): DEBUG: Adding applet 9.
** (gnome-panel:5269): DEBUG: Adding applet 10.

** (nautilus:5270): WARNING **: Unable to add monitor: Not supported
** (gnome-panel:5269): DEBUG: Adding applet 11.
** (gnome-panel:5269): DEBUG: Adding applet 12.
** (gnome-panel:5269): DEBUG: Adding applet 13.
** (gnome-panel:5269): DEBUG: Adding applet 14.
** (gnome-panel:5269): DEBUG: Adding applet 15.
** (gnome-panel:5269): DEBUG: Adding applet 16.

(gnome-panel:5269): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:5269): DEBUG: Adding applet 17.
** (gnome-panel:5269): DEBUG: Adding applet 18.
** (nm-applet:5287): DEBUG: applet_common_device_state_changed
** (nm-applet:5287): DEBUG: applet_common_device_state_changed
** (nm-applet:5287): DEBUG: foo_client_state_changed_cb
** (nm-applet:5287): DEBUG: applet_common_device_state_changed
** (nm-applet:5287): DEBUG: applet_common_device_state_changed
** (nm-applet:5287): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 81791 1241222400 1241140609
evolution-alarm-notify-Message:  Fri May  1 19:00:00 2009

evolution-alarm-notify-Message:  Thu Apr 30 20:16:49 2009

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a000c7 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a000c7 (Restart X )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a000c7 (Restart X )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a000c7 (Restart X )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (update-notifier:5298): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:5298): DEBUG: crashreport_check

```


I'm not sure quite what happened, but the proprietary nvidia drivers were working before I upgraded to jaunty. Is there a config file or error log I can look at somewhere?

---

### Post by Miles_Prower on 2009-05-01
So, I saw this line:

** (nautilus:5270): WARNING **: Unable to add monitor: Not supported

This suggests to me that the monitor I'm using is not supported. It's an LG 19 inch widescreen LCD. Model number W1952TQT. It's worked just fine before.... Something strange is going on with my drivers? Why hath Nvidia forsaken me?

---

### Post by tommcd on 2009-05-01
What nvidia card are you using? Perhaps you could try removing the 173 driver and installing the 180 driver as long as it supports your card.
Post your xorg.conf
Have a look at /var/log/Xorg.0.log for errors.

---

### Post by Miles_Prower on 2009-05-01
Here is my Xorg.conf file.
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
That looks very standard.


I will find out what video card I have and try the 180 drivers.

This is interesting, though....
[http://img53.imageshack.us/img53/9852/nouveaun.png](http://img53.imageshack.us/img53/9852/nouveaun.png)
Apt-get notices nouveau is poorly installed, tries to reinstall it, fails to reinstall it because the DKMS tree already has an entry for it (what the hell is a DKMS tree? Does this mean that there is delicious DKMS fruit to be found near it?)... I'd apt-get purge nouveau, but I can't find it...

BTW are the nouveau drivers any good?

---

### Post by tommcd on 2009-05-02
The Device section of your xorg.conf does not have a driver entry. It should look something like this for the nvidia driver:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```
Change "nvidia" to "nv" to use the 2D driver. Also, make sure```
Load "glx"
``` is present in the Module section of xorg.conf to use the nvidia driver.

It is probably not a good idea to have nouveau installed along with the nvidia driver. To remove nouveau, run:
```
sudo apt-get remove --purge  xserver-xorg-video-nouveau
```
The nouveau driver still has a way to go before it will be a realistic substitute for the nvidia driver:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_nouveau&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_nouveau&num=1)

---

### Post by Miles_Prower on 2009-05-02
VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Is this capable of working with nvidia-glx-173? The hardware drivers GUI suggests that it is. Speaking of said GUI, it suggests version 173 or 96, but selecting either one and clicking 'activate' (after login authentication) brings up a box with a progress bar that says "downloading and installing driver". The progress bar stays at zero, and disappears after a second or two.

Messing around with video settings has changed my xorg.conf. Here it is as of now:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by tommcd on 2009-05-02
> **Miles_Prower said:**
> VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

You should probably stick with the 173 driver for that video card.
Try this:
Make sure the 173 driver is installed.
Backup your current xorg.conf
Stop X with:
```
sudo /etc/init.d/gdm stop
```
Reconfigure the driver:
```
sudo nvidia-xconfig
```
Then reboot with sudo reboot.
 It may also help to edit /etc/default/linux-restricted-modules-common file and find the line:
> DISABLED_MODULES=""

and put nv in between the quotes like this:
> DISABLED_MODULES="nv"

You will need to remove that nv between the quotes if you ever want to use the 2D nv driver.

---

### Post by Miles_Prower on 2009-05-03
hmm.. same problem. Not too big of a deal anymore, I just bought a new motherboard/cpu/some ram/a video card, So I'll end up doing a reinstall anyways. 

That oughta fix it. with fire.

---

