---
title: "In Ubuntu 10.04 the keyboard layout takes a longtime (approx. 10 min.) to change."
date: 2011-03-06
forum: Hardware
---

### Post by vedovatti on 2011-03-06
Hi there,

I have a problem with the layout of the keyboard. I have two layout: DEU (Germany) and  ESP (Spanish) and the shortcuts on the hotkey. I have a Dell 6400 (1505) with hotkey for the control of the sound and launch media. So basically, the system randomly, specially when the CPU is busy, or when I have two user logged in, and takes between 5-10 min. to react when I want to change layout. Unfortunately, I need to change offen as I work on both languages. The problem is that when that happens it the hotkeys doesn't work neither. In this 5-10 minutes in the Indicator applet for the icon to change the layout disappears. In this period when I go to Menu>Preference>Keyboard the system gives me this message:
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with DBus, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
So, on other Forums ([http://ubuntuforums.org/showthread.php?t=579167]("http://ubuntuforums.org/showthread.php?t=579167")) I found a solution that I tried:
> Here is a workaround. Two files are modified.
Change /etc/X11/Xsession.d/55gnome-session_gnomerc, adding two lines (identified below by comments):
```
# ADD FOLLOWING LINE
rm -f /tmp/session-is-gnome
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
        \( "$BASESTARTUP" = x-session-manager -a \
        "`readlink /etc/alternatives/x-session-manager`" = \
                /usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
  # ADD FOLLOWING LINE
  touch /tmp/session-is-gnome
fi
```

Then change /etc/X11/Xsession.d/99x11-common_start completely, to the following text:

```
if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi

```
But unfortunately, didn't work for me.

After this time, all the hotkey that I pressed (during the time it didn't work) start doing the action the supposed to do. It didn't happen on the other Ubuntu distributions.

Everytime this happens I can see on the System Monitor that Xorg restarts so I think it could be something that crashes Xorg and restarts. I checked the .Xsessions and says something about AWN (I use AWN by the way), dbus error.

Dos anybody has an idea about this? 

Thanks

---

### Post by vedovatti on 2011-03-09
Hi again,

seems that nobody can help. :(

Anyway, I got an idea about what happens. Something crashes the gnome-setting-deamon (or the ibus) and the time that doen't work is the time that takes to restart.

So any idea about this. Does anybody knows how to see the log or bug file from gnome-setting-deamon?

thanks

---

### Post by vedovatti on 2011-03-12
Hi there again,

No ideas from anybody. So I think could be a problem with dbus and gnome-settings-daemon or even a bug in LIBDBUSMENU-GLIB.

I am not an expert so I really don't know sometimes what I am doing, but it could be a problem with AWN. Anyway, I realize yesterday that I get a .xsession-error.old file really long.

I attached in case that somebody know that crashes and restart the gnome-settings-daemon or the dbus. It seems long but 90% of it is the smartcard reader (but works fine by the way...). The interesting is the beginning and the end.

Thanks

[HTML]/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_NZ.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[2210]: WARNING: Could not parse desktop file /home/carlos/.config/autostart/gshared.desktop: Key file does not have key 'Type'
gnome-session[2210]: WARNING: could not read /home/carlos/.config/autostart/gshared.desktop
GNOME_KEYRING_CONTROL=/tmp/keyring-tPv9Vh
GNOME_KEYRING_CONTROL=/tmp/keyring-tPv9Vh
GNOME_KEYRING_CONTROL=/tmp/keyring-tPv9Vh
SSH_AUTH_SOCK=/tmp/keyring-tPv9Vh/ssh
gnome-session[2210]: WARNING: Could not launch application 'wicd-tray.desktop': Unable to start application: Failed to execute child process "wicd-gtk" (No such file or directory)
** Message: adding killswitch idx 0 state 1
** Message: adding killswitch idx 2 state 1
** Message: killswitch 0 is 1
** Message: killswitch 2 is 1
** Message: killswitches state 1

(polkit-gnome-authentication-agent-1:2296): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2296): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: killswitch 0 is 1
** Message: killswitch 2 is 1
** Message: killswitches state 1

(gnome-power-manager:2297): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.28.0/gobject/gsignal.c:2275: signal `proxy-status' is invalid for instance `0x8d06440'

(gnome-settings-daemon:2271): GLib-GObject-WARNING **: g_object_notify: object class `GkbdStatus' has no property named `name'
** (avant-window-navigator:2299): DEBUG: Updating dialog colours
** (nm-applet:2298): DEBUG: old state indicates that this was not a disconnect 0

(avant-window-navigator:2299): GLib-GObject-WARNING **: value "10.000000" of type `gfloat' is invalid or out of range for property `curviness' of type `gfloat'
Screen is composited
** (avant-window-navigator:2299): DEBUG: Updating dialog colours
** (avant-window-navigator:2299): DEBUG: Updating dialog colours

(avant-window-navigator:2299): GLib-GObject-WARNING **: value "10.000000" of type `gfloat' is invalid or out of range for property `curviness' of type `gfloat'

** (gnome-screensaver:2361): WARNING **: screensaver already running in this session
** (avant-window-navigator:2299): DEBUG: Updating dialog colours

(avant-window-navigator:2299): GLib-GObject-WARNING **: value "10.000000" of type `gfloat' is invalid or out of range for property `curviness' of type `gfloat'
Screen is composited
** (avant-window-navigator:2299): DEBUG: Updating dialog colours
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
** (avant-window-navigator:2299): DEBUG: Updating dialog colours

(avant-window-navigator:2299): GLib-GObject-WARNING **: value "10.000000" of type `gfloat' is invalid or out of range for property `curviness' of type `gfloat'
I/O warning : failed to load external entity "/home/carlos/.compiz/session/10291d261915e6e5f2129988837458075900000022100037"
** (nm-applet:2298): DEBUG: foo_client_state_changed_cb
[ERROR]: Option "initiate_key" already defined
[ERROR]: Option "initiate_button" already defined
[ERROR]: Option "initiate_edge" already defined
[ERROR]: Option "initiate_all_key" already defined
[ERROR]: Option "initiate_all_button" already defined
[ERROR]: Option "initiate_all_edge" already defined
[ERROR]: Option "terminate_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "next_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "shift_speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "mouse_speed" already defined
[ERROR]: Option "click_duration" already defined
[ERROR]: Option "mode" already defined
[ERROR]: Option "size" already defined
[ERROR]: Option "background_intensity" already defined
[ERROR]: Option "hide_all" already defined
[ERROR]: Option "reflection" already defined
[ERROR]: Option "ground_color1" already defined
[ERROR]: Option "ground_color2" already defined
[ERROR]: Option "ground_size" already defined
[ERROR]: Option "intensity" already defined
[ERROR]: Option "flip_rotation" already defined
[ERROR]: Option "cover_offset" already defined
[ERROR]: Option "overlay_icon" already defined
[ERROR]: Option "mipmaps" already defined
[ERROR]: Option "multioutput_mode" already defined
[ERROR]: Option "window_title" already defined
[ERROR]: Option "title_font_bold" already defined
[ERROR]: Option "title_font_size" already defined
[ERROR]: Option "title_back_color" already defined
[ERROR]: Option "title_font_color" already defined
[ERROR]: Option "title_text_placement" already defined
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2469] for "showdesktop.desktop", UID: 1299087795, XID: 29360177
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2471] for "feeds.desktop", UID: 1299086404, XID: 29360178
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2472] for "taskmanager.desktop", UID: 1299087927, XID: 29360179
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2473] for "animal-farm.desktop", UID: 1299086506, XID: 29360180
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2474] for "shinyswitcher.desktop", UID: 1299086461, XID: 29360181
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2475] for "garbage.desktop", UID: 1299086338, XID: 29360182

** (awn-applet:2472): WARNING **: Helpers are not available...
Please make sure you have dockmanager package installed.
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2476] for "cairo-menu.desktop", UID: 1299595911, XID: 29360191
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2477] for "file-browser-launcher.desktop", UID: 1299361026, XID: 29360192
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2478] for "simple-launcher.desktop", UID: 1299360169, XID: 29360193
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2479] for "simple-launcher.desktop", UID: 1299676571, XID: 29360194
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2480] for "awnterm.desktop", UID: 1299361330, XID: 29360195
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2481] for "tomboy-applet.desktop", UID: 1299521154, XID: 29360196
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2482] for "to-do.desktop", UID: 1299360183, XID: 29360197
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2483] for "hardware-sensors.desktop", UID: 1299355602, XID: 29360198
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2484] for "awnsystemmonitor.desktop", UID: 1299356309, XID: 29360199
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2485] for "media-control.desktop", UID: 1299355627, XID: 29360200
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2486] for "volume-control.desktop", UID: 1299660745, XID: 29360201
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2487] for "indicator-applet.desktop", UID: 1299355611, XID: 29360202
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2488] for "notification-area.desktop", UID: 1299355635, XID: 29360203
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2489] for "weather.desktop", UID: 1299575107, XID: 29360204
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2490] for "cairo-clock.desktop", UID: 1299574959, XID: 29360205
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2491] for "digital-clock.desktop", UID: 1299401961, XID: 29360206
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2492] for "quit.desktop", UID: 1299355652, XID: 29360207
** (avant-window-navigator:2299): DEBUG: Spawned awn-applet[2493] for "quit-shut-down.desktop", UID: 1299355659, XID: 29360208

(awn-applet:2480): GLib-GObject-WARNING **: g_object_newv: construct property "panel-id" for object `AwnTerminalApplet' can't be set twice

** (awn-applet:2472): CRITICAL **: File not found: '/home/carlos/.config/awn/launchers/awn_launcher.desktop'
** (awn-applet:2472): DEBUG: task_manager_refresh_launcher_paths: Bad desktop file '/home/carlos/.config/awn/launchers/awn_launcher.desktop'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (awn-applet:2480): DEBUG: awn-terminal.vala:80: keybinding: 

(nm-applet:2298): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
** (awn-applet:2480): DEBUG: awn-terminal.vala:80: keybinding: 
** (nm-applet:2298): DEBUG: foo_client_state_changed_cb

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(awn-applet:2487): Indicator-Sound-DEBUG: At start-up attempting to set the image to audio-volume-muted-panel

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.sound on /org/ayatana/indicator/sound/menu: Could not get owner of name 'org.ayatana.indicator.sound': no such name

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.messages on /org/ayatana/indicator/messages/menu: Could not get owner of name 'org.ayatana.indicator.messages': no such name

(awn-applet:2487): libindicator-WARNING **: Unable to create service proxy on 'org.ayatana.indicator.session': Could not get owner of name 'org.ayatana.indicator.session': no such name

(awn-applet:2487): libindicator-WARNING **: Unable to create service proxy on 'org.ayatana.indicator.me': Could not get owner of name 'org.ayatana.indicator.me': no such name

(awn-applet:2487): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(awn-applet:2474): Gdk-WARNING **: XID collision, trouble ahead
(awn-applet:2487): Indicator-Sound-DEBUG: about to connect to the signals

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(awn-applet:2487): Indicator-Sound-DEBUG: at the indicator start up and the volume percent returned from dbus method is 24.172974
(awn-applet:2487): Indicator-Sound-DEBUG: at the indicator start up and the MUTE returned from dbus method is 0
(awn-applet:2487): Indicator-Sound-DEBUG: IndicatorSound::fetch_sink_availability_from_dbus -> AVAILABILTY returned from dbus method is 1
** (awn-applet:2487): DEBUG: Connected to Application Indicator Service.
** (awn-applet:2487): DEBUG: Setup proxy signals
** (awn-applet:2487): DEBUG: Connect to them.
** (awn-applet:2487): DEBUG: Request current apps
(awn-applet:2487): Indicator-Sound-DEBUG: slider parent changed
** (awn-applet:2487): DEBUG: Building new application entry: :1.18  with icon: ubuntuone-indicator-offline

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (awn-applet:2487): DEBUG: Building new application entry: :1.10  with icon: bluetooth-active

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (awn-applet:2487): DEBUG: Building new application entry: :1.12  with icon: gpm-battery-080

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (awn-applet:2487): DEBUG: 	Appending search path: /usr/share/gnome-power-manager/icons

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(awn-applet:2487): libindicator-DEBUG: Restarting service 'org.ayatana.indicator.session' count 1
(awn-applet:2487): libindicator-DEBUG: Restarting service 'org.ayatana.indicator.me' count 1

(awn-applet:2487): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(awn-applet:2487): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed

(awn-applet:2487): LIBDBUSMENU-GLIB-CRITICAL **: id_prop_update: assertion `priv->root != NULL' failed
** (awn-applet:2487): DEBUG: loading avatar from file /home/carlos/.face
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

** (awn-applet:2472): CRITICAL **: File not found: '/home/carlos/.config/awn/launchers/awn_launcher.desktop'
** (awn-applet:2472): DEBUG: task_manager_refresh_launcher_paths: Bad desktop file '/home/carlos/.config/awn/launchers/awn_launcher.desktop'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (awn-applet:2487): DEBUG: Updating username label

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (awn-applet:2487): DEBUG: Username width 36px
** (awn-applet:2487): DEBUG: Font size 10.000000 pt
** (awn-applet:2487): DEBUG: Screen DPI 96.000000
** (awn-applet:2487): DEBUG: Username width 2.700000em
** (awn-applet:2487): DEBUG: Using user icon for 'Dana Beitz' from file: /home/dana/.face

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.7
Initializing nautilus-image-converter extension
evolution-alarm-notify-Message: Setting timeout for 82393 1299970800 1299888407
evolution-alarm-notify-Message:  Sun Mar 13 00:00:00 2011

evolution-alarm-notify-Message:  Sat Mar 12 01:06:47 2011

Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
[opensc-pkcs11] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
[opensc-pkcs11] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
[opensc-pkcs11] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
[opensc-pkcs11] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
[opensc-pkcs11] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
directory
Error: can't open /var/run/openct/status: No such file or directory
[opensc-pkcs11] reader-pcsc.c:906:pcsc_detect_readers: SCardEstablishContext failed: 0x8010001d
[opensc-pkcs11] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
NOTE: child process received `Goodbye', closing down

(gnome-power-manager:2297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-power-manager:2297): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
** (avant-window-navigator:2299): DEBUG: Updating dialog colours
** (avant-window-navigator:2299): DEBUG: Updating dialog colours

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2487): libindicator-WARNING **: Unable to find icon in theme.
Shutting down nautilus-image-converter extension
Shutting down nautilus-gdu extension

--- Hash table keys for warning below:
--> image/jpeg
--> smb-network:
--> inode/directory
--> Carlos Vedovatti
--> l22
--> carlos
--> network:

(nautilus:2292): Eel-WARNING **: "unique eel_ref_str" hash table still has 7 elements at quit time (keys above)

(nautilus:2292): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 6 elements at quit time
** Message: NM disappeared
** Message: Active session changed

** (gnome-user-share:2669): WARNING **: Couldn't request the name: Unable to find session for cookie
PolicyKit daemon disconnected from the bus.
We are no longer a registered authentication agent.

** (polkit-gnome-authentication-agent-1:2296): WARNING **: no sender

** Message: <info>  disconnected by the system bus.


(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'

(awn-applet:2476): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.43 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(file-browser-launcher.py:2477): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.43 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(gnome-settings-daemon:2271): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.43 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(awn-applet:2487): Gtk-WARNING **: /build/buildd/gtk+2.0-2.20.1/gtk/gtkstyle.c:1788: widget class `GtkImage' has no property named `x-ayatana-indicator-dynamic'
(awn-applet:2487): libindicator-DEBUG: Restarting service 'org.ayatana.indicator.session' count 1

(awn-applet:2487): LIBDBUSMENU-GLIB-WARNING **: Unable to get dbusmenu proxy for org.ayatana.indicator.session on /org/ayatana/indicator/session/menu: Could not get owner of name 'org.ayatana.indicator.session': no such name

(awn-applet:2487): libindicator-WARNING **: Unable to create service proxy on 'org.ayatana.indicator.session': Could not get owner of name 'org.ayatana.indicator.session': no such name
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
avant-window-navigator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
ubuntuone-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Initializing Application...
Initializing Indicator...
Initializing Client...
Update quota info failed: global name 'socket' is not defined
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
ShinySwitcher Message:  viewport/compiz detected.. using existing workspace config
ShinySwitcher Message:  viewport/compiz detected.. using existing workspace config
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
feeds.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
animal-farm.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(file-browser-launcher.py:2477): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.44 of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
file-browser-launcher.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 2 (No such file or directory) on X server :0.0.
hardware-sensors.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
tomboy-applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
to-do.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
media_control.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 41849 requests (41848 known processed) with 0 events remaining.
cairo-clock.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
quit.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
volume-control.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
quit.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
weather.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (3 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (2 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (1 retries remaining) in 10 seconds
Error in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (3 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (2 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (1 retries remaining) in 10 seconds
Error in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (3 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (2 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (1 retries remaining) in 10 seconds
Error in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (3 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (2 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (1 retries remaining) in 10 seconds
Error in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (3 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (2 retries remaining) in 10 seconds
Warning in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
Reattempt (1 retries remaining) in 10 seconds
Error in Weather: error in get_weather_map: Couldn't parse weather map: Unrecognized image file format
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
(awn-applet:2487): LIBDBUSMENU-GLIB-DEBUG: Oh, that's bad.  That's really bad.  We can't get a proxy to DBus itself?  Seriously?  Here's all I know: Connection was disconnected before a reply was received
(awn-applet:2487): LIBDBUSMENU-GLIB-DEBUG: Oh, that's bad.  That's really bad.  We can't get a proxy to DBus itself?  Seriously?  Here's all I know: Connection is closed
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/HTML]

---

