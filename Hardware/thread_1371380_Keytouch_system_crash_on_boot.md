---
title: "Keytouch: system crash on boot"
date: 2010-01-03
forum: Hardware
---

### Post by Fitch on 2010-01-03
I installed keytouch & keytouch editor on my system as I have a Microsoft Natural Multimedia keyboard 1.0A.

Everything went well, except that pressing the web/home button caused the home directory to show instead of the home internet page.  O.K., so I did a reboot just in case that was the problem.

All I now get is
init: Failed to spawn mountall_shell main process: unable to execute permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn mountall_shell post-stop process: unable to execute permission denied

If I do a control alt delete, I get
init: Failed to spawn control-alt-delete main process: unable to execute permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied

I get the same in recovery mode

I can put the live CD in, but don't know what to do with it as most of the time I'm not allowed in anywhere.  I can get the CD's Firefox web browser up, but I can't, of course, retrieve the mail from the computer's Thunderbird directory, so I've lost all my bookings.

This would happen now, just as I've done most of the accounts, which are stuck on the hard drive.
I am at my wits end with this..

I really do need help getting my computer back fast.

What file do I delete to get it to run, How do I tell the CD that I'm the owner of this computer and really need it back?

Or can I call up the synaptic manager on the computer to uninstall keytouch, and if so ,how?

---

### Post by Fitch on 2010-01-04
I have downloaded a rescue cd and booted it up.

Have not got a clue what to do now.

I now have a terminal:
root@sysreccd /root %

I need to:

tell the computer that I am brafferton , group brafferton, or root, group brafferton so I can move files,

I can then hopefully copy the home directory to the second drive,

Then format and re-install Linux, I presume

Then copy the home directory back.

Will this work? Will I still have my emails? and if so, how do I do it?

Or can I copy some files across from either the Karmic CD or rescue CD to get my keyboard and mouse (& screen) working again?

---

### Post by Fitch on 2010-01-04
The story so far...

I went to the library and borrowed a Linux book...

I found out about useradd and did:
sudo useradd -m brafferton
sudo passwd brafferton
put the password in twice

I went to System>Administration>Users and groups to make sure I was added
and then clicked on the Live session user on the top right of the screen and switched to brafferton.

I was then able to copy most of the home directory somewhere safe. (A lot of funny number files which apparently were in a trash directory somewhere would not go)

This is all very well, but I really don't want to format the hard drive as There is quite a bit, like having an icon at the top of the screen (next to the firefox icon) that automatically mounts the server on startup, and the directory needed to do that, and I can't remember how I set it up, etc.

Is there not a directory or two that I can just wipe over with the associated live cd directory? 
Presumably one would need to know more about the errors.
I would be quite happy to take a photograph of the screen with my SLR and post the image, if I knew someone was going to actually reply..

---

### Post by Fitch on 2010-01-04
I did find this file (.xsession-errors) in the /home/brafferton directory, is this any help?

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-R3gEP8/socket
SSH_AUTH_SOCK=/tmp/keyring-R3gEP8/socket.ssh
GNOME_KEYRING_PID=1709

(gnome-settings-daemon:1706): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Unable to find a synaptics device.
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).

(nautilus:1808): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1807): DEBUG: Adding applet 0.
** (gnome-panel:1807): DEBUG: Initialized Panel Applet Signaler.
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
** (gnome-panel:1807): DEBUG: Adding applet 1.
** (gnome-panel:1807): DEBUG: Adding applet 2.

(polkit-gnome-authentication-agent-1:1844): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1844): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Starting gtk-window-decorator
Initializing nautilus-gdu extension

** (nautilus:1808): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1808): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1808): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:1807): DEBUG: Adding applet 3.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/brafferton/.compiz/session/10b75b6ce34aa1e07126251139078055900000015730025"
** (gnome-panel:1807): DEBUG: Adding applet 4.
** (gnome-panel:1807): DEBUG: Adding applet 5.
** (gnome-panel:1807): DEBUG: Adding applet 6.
** (gnome-panel:1807): DEBUG: Adding applet 7.
** (gnome-panel:1807): DEBUG: Adding applet 8.
** (gnome-panel:1807): DEBUG: Adding applet 9.
** (gnome-panel:1807): DEBUG: Adding applet 10.
** (gnome-panel:1807): DEBUG: Adding applet 11.
** (gnome-panel:1807): DEBUG: Adding applet 12.
** (gnome-panel:1807): DEBUG: Adding applet 13.
** (gnome-panel:1807): DEBUG: Adding applet 14.
** (gnome-panel:1807): DEBUG: Adding applet 15.
** (gnome-panel:1807): DEBUG: Adding applet 16.
** (gnome-panel:1807): DEBUG: Adding applet 17.
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
evolution-alarm-notify-Message: Setting timeout for 51786 1262563200 1262511414
evolution-alarm-notify-Message:  Mon Jan  4 00:00:00 2010

evolution-alarm-notify-Message:  Sun Jan  3 09:36:54 2010

Invalid rate plugin version 10002
Invalid rate plugin version 10002

(nautilus:2864): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3313): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:3332): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


(nautilus:4641): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(synaptic:8645): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:8645): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
Another synaptic is running. Trying to bring it to the foreground

** (yelp:12884): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (yelp:12884): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.
I/O error : Is a directory
I/O error : Is a directory
I/O error : Is a directory
I/O error : Is a directory
Warning: Not all keys can be grabbed by this program. This
         can be caused by another program which is already
         grabbing these keys.
Warning: Not all keys can be grabbed by this program. This
         can be caused by another program which is already
         grabbing these keys.

[01mHP Linux Imaging and Printing System (ver. 3.9.10)[0m
[01mSystem Tray Status Service ver. 2.0[0m

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

** (gnome-panel:1807): DEBUG: Removing applet 17.
** (gnome-panel:1807): DEBUG: Removing applet 16.
** (gnome-panel:1807): DEBUG: Removing applet 15.
** (gnome-panel:1807): DEBUG: Removing applet 14.
** (gnome-panel:1807): DEBUG: Removing applet 13.
** (gnome-panel:1807): DEBUG: Removing applet 12.
** (gnome-panel:1807): DEBUG: Removing applet 11.
** (gnome-panel:1807): DEBUG: Removing applet 10.
** (gnome-panel:1807): DEBUG: Removing applet 9.
** (gnome-panel:1807): DEBUG: Removing applet 8.
** (gnome-panel:1807): DEBUG: Removing applet 7.
** (gnome-panel:1807): DEBUG: Removing applet 6.

(gnome-panel:1807): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(gnome-panel:1807): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:1807): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:1807): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(gnome-panel:1807): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:1807): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Shutting down nautilus-gdu extension

--- Hash table keys for warning below:
--> Brafferton
--> l2065
--> inode/directory
--> brafferton
--> l2049

(nautilus:1808): Eel-WARNING **: "unique eel_ref_str" hash table still has 5 elements at quit time (keys above)

(nautilus:1808): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 15 elements at quit time
** (gnome-panel:1807): DEBUG: Removing applet 5.
** (gnome-panel:1807): DEBUG: Removing applet 4.
** (gnome-panel:1807): DEBUG: Removing applet 3.
** (gnome-panel:1807): DEBUG: Removing applet 2.
** (gnome-panel:1807): DEBUG: Removing applet 1.
** (gnome-panel:1807): DEBUG: Removing applet 0.

(polkit-gnome-authentication-agent-1:1844): polkit-gnome-1-WARNING **: Error enumerating temporary authorizations: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.EnumerateTemporaryAuthorizations() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: Cannot determine session the caller is in
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-volume-control-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0" 
      after 64 requests (59 known processed) with 0 events remaining. 
Warning: Not all keys can be grabbed by this program. This
         can be caused by another program which is already
         grabbing these keys.
The application 'firefox' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

[01mHP Linux Imaging and Printing System (ver. 3.9.10)[0m
[01mSystem Tray Status Service ver. 2.0[0m

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

P.S. Happy New Year.

---

### Post by Fitch on 2010-01-05
I managed to find out about  ALT SysReq REISUB and tried that. 

[ 1093.511789] SysRq : Keyboard mode set to system default
[ 1102.094953] SysRq : Terminate All Tasks
init: udev-finish main process (492) killed by TERM signal
init: udev-finish main process ended, respawning
init: upstart-udev-bridge main process ended, respawning
init: Failed to spawn udev main process:unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn upstart-udev-bridge main process:unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
[ 1121.145941] SysRq : Kill All Tasks
[ 1124.337421] SysRq : Emergency Sync
[ 1124.337829] Emergency Sync complete
[ 1133.247809] SysRq : Emergency Remount R/O
[ 1133.253993] Emergency Remount complete

It rebooted and gave me:

init: Failed to spawn mountall-shell main process:unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn mountall_shell post-stop process: unable to execute: Permission denied
init: ufw pre-start process (685) terminated with status 126
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn ufw post-stop process: unable to execute: Permission denied
init: Failed to spawn networking main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn udev-finish main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
udevd-work[810]: exec of program '/sbin/modprobe' failed

udevd-work[811]: exec of program '/lib/udev/path-id' failed

udevd-work[812]: exec of program '/lib/udev/path-id' failed

Hopefully there are no spelling mistakes as I'm copy typing it into another computer to post.

Please, Please help!!!

---

### Post by Fitch on 2010-01-06
Any takers?

---

