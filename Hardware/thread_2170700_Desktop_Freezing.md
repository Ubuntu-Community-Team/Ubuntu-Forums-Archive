---
title: "Desktop Freezing"
date: 2013-08-27
forum: Hardware
---

### Post by ice29212 on 2013-08-27
Hello,

I am experiencing random desktop freezes. The only way I can gain access to my system again is by rebooting the computer. After looking at the system processes via an SSH session I was able to see that the Xorg process was running quite high, using lamost 100% of the CPU time. I am wondering if it has something to do with my hardware my GPU specifically. Hopefully the below information will help.

My system information is as follows: 

```
12.04.2 LTS, Precise Pangolin
```
```
Tue Aug 27 06:58:37 2013       
+------------------------------------------------------+                       
| NVIDIA-SMI 5.319.32   Driver Version: 319.32         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 680     Off  | 0000:03:00.0     N/A |                  N/A |
| 30%   35C  N/A     N/A /  N/A |      241MB /  2047MB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
```

```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux jlnx-desk 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:48:11 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-37-generic root=UUID=3fe3e03b-7502-42e8-9960-46cb0f4bf2cb ro quiet splash
Build Date: 11 April 2013  01:05:39PM
xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Aug 14 18:20:29 2013
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
```

```
Activating service name='org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:895: Starting unity-greeter 0.2.9 UID=104 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:898: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:902: Creating background surface
[+0.00s] DEBUG: unity-greeter.vala:905: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:933: Setting GTK+ settings
Successfully activated service 'org.a11y.atspi.Registry'

** (at-spi2-registryd:8953): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:8953): WARNING **: Unable to register client with session manager
[+0.02s] DEBUG: unity-greeter.vala:956: Creating Unity Greeter
[+0.02s] DEBUG: Connecting to display manager...
[+0.02s] DEBUG: Wrote 17 bytes to daemon
[+0.02s] DEBUG: Read 8 bytes from daemon
[+0.02s] DEBUG: Read 120 bytes from daemon
[+0.02s] DEBUG: Connected version=1.2.3 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0.07s] DEBUG: menubar.vala:359: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.08s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.09s] DEBUG: get entries
[+0.09s] DEBUG: menubar.vala:541: Adding indicator object 0x1944078 at position 0
[+0.09s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.09s] DEBUG: Checking against 2 possible times
[+0.09s] DEBUG: Guessing max time width: 62
[+0.09s] DEBUG: get entries
[+0.09s] DEBUG: menubar.vala:541: Adding indicator object 0x19bd1a8 at position 1
[+0.09s] WARNING: IndicatorObject class does not have an accessible description.
[+0.10s] WARNING: IndicatorObject class does not have an accessible description.
[+0.10s] DEBUG: get entries
[+0.10s] DEBUG: get entries
[+0.10s] DEBUG: menubar.vala:541: Adding indicator object 0x1a38838 at position 2
[+0.10s] DEBUG: menubar.vala:365: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-unity.desktop (Cairo-Dock (with Unity Panel), This session logs you into GNOME with Cairo-Dock and Unity-2D panel)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/gnome-shell.desktop (GNOME, This session logs you into GNOME)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock.desktop (Cairo-Dock (Gnome + Effects), This session logs you into GNOME with Cairo-Dock and with graphical effects.)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.10s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-fallback.desktop (Cairo-Dock (Gnome No effects), This session logs you into GNOME with Cairo-Dock and without any graphical effect.)
[+0.10s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.10s] DEBUG: session-chooser.vala:42: Adding session cairo-dock (Cairo-Dock (Gnome + Effects))
[+0.10s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-fallback (Cairo-Dock (Gnome No effects))
[+0.10s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-unity (Cairo-Dock (with Unity Panel))
[+0.10s] DEBUG: session-chooser.vala:42: Adding session gnome-shell (GNOME)
[+0.10s] DEBUG: session-chooser.vala:42: Adding session gnome-classic (GNOME Classic)
[+0.11s] DEBUG: session-chooser.vala:42: Adding session gnome-fallback (GNOME Classic (No effects))
[+0.11s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0.11s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0.21s] DEBUG: Setting keyboard layout to 'us'
[+0.23s] DEBUG: main-window.vala:98: Screen is 1680x1050 pixels
[+0.23s] DEBUG: main-window.vala:104: Monitor 0 is 1680x1050 pixels at 0,0
[+0.23s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.23s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.24s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.24s] DEBUG: unity-greeter.vala:332: Adding/updating user joe (joe)
[+0.24s] DEBUG: unity-greeter.vala:189: Adding guest account entry
[+0.32s] DEBUG: Starting authentication for user joe...
[+0.32s] DEBUG: Wrote 19 bytes to daemon
[+0.32s] DEBUG: unity-greeter.vala:959: Showing greeter
[+0.32s] DEBUG: unity-greeter.vala:357: Showing main window
[+0.32s] DEBUG: New style for time label
[+0.32s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.32s] DEBUG: Checking against 2 possible times
[+0.32s] DEBUG: Guessing max time width: 62
[+0.33s] DEBUG: background.vala:315: Regenerating backgrounds
[+0.33s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1680x1050
[+0.33s] DEBUG: New style for time label
[+0.33s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.33s] DEBUG: Checking against 2 possible times
[+0.33s] DEBUG: Guessing max time width: 62
[+0.34s] DEBUG: unity-greeter.vala:972: Starting main loop
[+0.34s] DEBUG: Read 8 bytes from daemon
[+0.34s] DEBUG: Read 33 bytes from daemon
[+0.34s] DEBUG: Prompt user with 1 message(s)
[+0.38s] DEBUG: Num devices: '0'

[+0.38s] MESSAGE: Couldn't find primary device
[+0.38s] DEBUG: Num devices: '0'

[+0.39s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+0.39s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+0.39s] DEBUG: should_be_visible: no
[+0.39s] DEBUG: menubar.vala:549: Removing indicator object 0x18a4de8
[+0.39s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.39s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.39s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.39s] WARNING: menubar.vala:561: Indicator object 0x18a4de8 not in menubar
[+0.40s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+0.40s] DEBUG: notify visible signal received
[+0.40s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+0.41s] DEBUG: New calendar item
[+0.41s] DEBUG: Connected to Application Indicator Service.
[+0.41s] DEBUG: unity-greeter.vala:315: starting system-ready sound
[+1.69s] DEBUG: background.vala:67: Making background /usr/share/themes/Adwaita/backgrounds/adwaita-timed.xml at 1680x1050
[+1.69s] DEBUG: background.vala:144: Error loading background: Couldn't recognize the image file format for file '/usr/share/themes/Adwaita/backgrounds/adwaita-timed.xml'
[+1.69s] DEBUG: Setting keyboard layout to 'us'
[+1.71s] DEBUG: Request current apps
[+1.71s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+1.72s] DEBUG: background.vala:116: Render of background /usr/share/themes/Adwaita/backgrounds/adwaita-timed.xml complete
[+1.72s] CRITICAL: background_loader_create_pattern: assertion `image != NULL' failed
[+1.72s] DEBUG: indicator-sound: new_volume_slider_widget
[+1.73s] DEBUG: indicator-sound: new_voip_slider_widget
[+20.23s] DEBUG: Providing response to display manager
[+20.23s] DEBUG: Wrote 27 bytes to daemon
[+20.41s] DEBUG: Read 8 bytes from daemon
[+20.41s] DEBUG: Read 15 bytes from daemon
[+20.41s] DEBUG: Authentication complete for user joe with return code 0
[+20.42s] DEBUG: Starting session cairo-dock
[+20.42s] DEBUG: Wrote 22 bytes to daemon
[+20.42s] DEBUG: Read 8 bytes from daemon
[+20.42s] DEBUG: Read 4 bytes from daemon
```

---

