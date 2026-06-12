---
title: "tried playing a game on wine, now display driver and log viewer don't work"
date: 2009-09-15
forum: Hardware
---

### Post by whydoesitburn on 2009-09-15
First of all, I am using a Nvidia GeForce 8400GS on Jaunty, and the driver for it was working just fine until last night, after attempting to play a game through wine (which promptly crashed at start). After that I got the typical distorted screen when ever an X-server issue arises. After fixing X through recovery mode, I re-installed the driver, and rebooted my computer. The login screen come up clear as it always does, but after logging in, I was greeted with the same problem. Whenever I try to view the logs, the gnome log viewer either runs really slow, or simply doesn't respond. I did manage to gather that whenever the driver is re-installed, that I get a message about X-server failing to load on those sessions. Does anyone have any suggestions on a fix, or even what file could possibly have been corrupted? I have already to rolling back the drivers, to no avail, and even after restart the log viewer still causes CPU spikes upon opening. Any help would be appreciated.

---

### Post by whydoesitburn on 2009-09-16
Maybe this information will help me get an answer to what is happening on my system:

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
GNOME_KEYRING_SOCKET=/tmp/keyring-w0q54A/socket
SSH_AUTH_SOCK=/tmp/keyring-w0q54A/socket.ssh

(gnome-settings-daemon:3525): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /home/*********/.config/metacity/sessions/10ea68f705a063ac48125308175673002800000033280024.ms: Failed to open file '/home/**********/.config/metacity/sessions/10ea68f705a063ac48125308175673002800000033280024.ms': No such file or directory
Failure: Module initalization failed
** (nm-applet:3571): DEBUG: applet_common_device_state_changed
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/*********/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/************/.config/tracker/tracker.cfg'
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
** (gnome-panel:3548): DEBUG: Adding applet 0.
** (gnome-panel:3548): DEBUG: Initialized Panel Applet Signaler.
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/***********/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/***********/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/***********/.local/share/tracker/trackerd.log'
** (gnome-panel:3548): DEBUG: Adding applet 1.
** (gnome-panel:3548): DEBUG: Adding applet 2.
** (gnome-panel:3548): DEBUG: Adding applet 3.
** (gnome-panel:3548): DEBUG: Adding applet 4.
** (gnome-panel:3548): DEBUG: Adding applet 5.
** (gnome-panel:3548): DEBUG: Adding applet 6.
** (gnome-panel:3548): DEBUG: Adding applet 7.
** (gnome-panel:3548): DEBUG: Adding applet 8.

** (nautilus:3549): WARNING **: Unable to add monitor: Not supported
** (gnome-panel:3548): DEBUG: Adding applet 9.
** (gnome-panel:3548): DEBUG: Adding applet 10.

(gnome-panel:3548): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3548): DEBUG: Adding applet 11.
** (gnome-panel:3548): DEBUG: Adding applet 12.
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG_PATH" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "IPTABLES_CUSTOM_DIR" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG_SLEEP" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "CUSTOM_DAEMON_OPTS" has not been defined and was therefore ignored 
** Warning: QVector<QString> getFileData(const QString&) Could not read from file "/etc/blockcontrol/blockcontrol.conf_back" 
** Warning: QVector<QString> getFileData(const QString&) Could not read from file "/etc/blockcontrol/blocklists.list_back" 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG_PATH" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "IPTABLES_CUSTOM_DIR" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG_SLEEP" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "CUSTOM_DAEMON_OPTS" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG_PATH" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "IPTABLES_CUSTOM_DIR" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "WATCHDOG_SLEEP" has not been defined and was therefore ignored 
** Warning: void MoblockSettings::processSettings() Setting "CUSTOM_DAEMON_OPTS" has not been defined and was therefore ignored 
evolution-alarm-notify-Message: Setting timeout for 63809 1253145600 1253081791
evolution-alarm-notify-Message:  Wed Sep 16 19:00:00 2009

evolution-alarm-notify-Message:  Wed Sep 16 01:16:31 2009

** (update-notifier:3566): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
  PID TTY          TIME CMD
 3508 ?        00:00:00 pulseaudio
3548
** (update-notifier:3566): DEBUG: crashreport_check
```

---

