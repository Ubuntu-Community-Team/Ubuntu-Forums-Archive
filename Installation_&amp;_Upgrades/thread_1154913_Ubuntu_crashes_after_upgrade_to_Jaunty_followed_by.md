---
title: "Ubuntu crashes after upgrade to Jaunty followed by partial upgrade"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by eamonireland on 2009-05-10
Hi,

I've found similar threads, and posted to them, and tried everything, but I can't get this problem sorted. I haven't been able to log in since Tuesday, and I'm now back using windows :( I'm really desperate to get this fixed. I have no more ideas what I can do.

(This problem seems similar to [http://swiss.ubuntuforums.org/showthread.php?t=1139558]("http://swiss.ubuntuforums.org/showthread.php?t=1139558"))
---
After upgrading to Jaunty everything worked perfectly for about 3 days. Then I was prompted to update via update manager, and got the message that something was missing, and prompted to do a partial upgrade. The next time I rebooted after the partial upgrade I got this problem.

Now, when I try to log on I get a black screen, followed by the login screen again. On the second log on I get a message box saying:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

It asks if I want to see the contents of .xsession-errors, which I attach below. 

If I close this box, the system shuts down. If I leave it there other windows open up. There are very limited graphics, and nautilus and firefox open at the top left. They don't have the x to close the window, and you can't move them or switch programs using tab. I can only remove them (and then access the menus) by running System Monitor using Gnome-do. 

Following other threads I have done the following
--------------------------------------
- Run CHOWN and CHMOD on the .ICEauthority file
- Renamed .ICEauthority
- Deleted .ICEauthority
--------------------------------------
- Moved .gnome to /tmp/.gnome, and .gnome2 to /tmp/.gnome2
--------------------------------------
- dpkg-reconfigure xserver.xorg
--------------------------------------
- sudo apt-get purge remove gnome-session
- sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install gnome session
- sudo apt-get install -f
--------------------------------------
- sudo dpkg-reconfigure gnome session
- sudo dpkg --configure -a
--------------------------------------
- sudo killall gdm
- sudo apt-get install -f
- sudo dpkg-reconfigure gdm
--------------------------------------
- sudo apt-get install ubuntu-desktop
--------------------------------------

contents of .xsession-errors:
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap: unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap: 1 error encountered, aborting.
Unable to create /home/eamon/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-6cRSQL/socket
SSH_AUTH_SOCK=/tmp/keyring-6cRSQL/socket.ssh
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
x-session-manager[4965]: WARNING: Could not launch application 'launchy.desktop': Unable to start application: Failed to execute child process "launchy" (No such file or directory)
** (gnome-panel:5077): DEBUG: Adding applet 0.
** (gnome-panel:5077): DEBUG: Initialized Panel Applet Signaler.
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XFree86.conf to use GSynaptics
** (gnome-panel:5077): DEBUG: Adding applet 1.
x-session-manager[4965]: WARNING: Could not launch application '106153b4ac7667863f124138984694270700000037390032. desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
x-session-manager[4965]: ******************* START ********************************
x-session-manager[4965]: Frame 0: x-session-manager [0x8061015]
x-session-manager[4965]: Frame 1: x-session-manager [0x80611c4]
x-session-manager[4965]: Frame 2: [0xb7fe9400]
x-session-manager[4965]: Frame 3: /usr/lib/libglib-2.0.so.0(g_free+0x36) [0xb7962126]
x-session-manager[4965]: Frame 4: /usr/lib/libglib-2.0.so.0(g_strfreev+0x20) [0xb797b090]
x-session-manager[4965]: Frame 5: x-session-manager [0x806eba5]
x-session-manager[4965]: Frame 6: x-session-manager [0x806f337]
x-session-manager[4965]: Frame 7: x-session-manager [0x8052b77]
x-session-manager[4965]: Frame 8: x-session-manager [0x8065606]
x-session-manager[4965]: Frame 9: /usr/lib/libglib-2.0.so.0(g_hash_table_find+0x5c) [0xb794b29c]
x-session-manager[4965]: Frame 10: x-session-manager [0x8065b47]
x-session-manager[4965]: Frame 11: x-session-manager [0x8065de6]
x-session-manager[4965]: Frame 12: /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84) [0xb79f03a4]
x-session-manager[4965]: Frame 13: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb79e2c7b]
x-session-manager[4965]: Frame 14: /usr/lib/libgobject-2.0.so.0 [0xb79f8e57]
x-session-manager[4965]: Frame 15: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9) [0xb79fa4b9]
x-session-manager[4965]: Frame 16: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb79fa936]
x-session-manager[4965]: Frame 17: x-session-manager [0x8051761]
x-session-manager[4965]: Frame 18: x-session-manager [0x8069f2e]
x-session-manager[4965]: Frame 19: x-session-manager [0x80589b6]
x-session-manager[4965]: Frame 20: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb79e2c7b]
x-session-manager[4965]: Frame 21: /usr/lib/libgobject-2.0.so.0 [0xb79f8e57]
x-session-manager[4965]: Frame 22: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f) [0xb79fa34f]
x-session-manager[4965]: Frame 23: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb79fa936]
x-session-manager[4965]: Frame 24: x-session-manager [0x805603c]
x-session-manager[4965]: Frame 25: /usr/lib/libSM.so.6(_SmsProcessMessage+0xd5a) [0xb7fcb9fa]
x-session-manager[4965]: Frame 26: /usr/lib/libICE.so.6(IceProcessMessages+0x31a) [0xb7fc09fa]
x-session-manager[4965]: Frame 27: x-session-manager [0x8056c11]
x-session-manager[4965]: Frame 28: /usr/lib/libglib-2.0.so.0 [0xb7990dad]
x-session-manager[4965]: Frame 29: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e [0xb7959b88]
x-session-manager[4965]: Frame 30: /usr/lib/libglib-2.0.so.0 [0xb795d0eb]
x-session-manager[4965]: Frame 31: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca) [0xb795d5ba]
x-session-manager[4965]: Frame 32: /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb7cac7d9]
x-session-manager[4965]: Frame 33: x-session-manager [0x8062a09]
x-session-manager[4965]: Frame 34: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb76ba775]
x-session-manager[4965]: Frame 35: x-session-manager [0x80511e1]
x-session-manager[4965]: ******************* END **********************************

(update-notifier:5083): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(firefox:5084): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:5093): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:5110): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:5115): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(nautilus:5079): EggSMClient-WARNING **: Failed to connect to the session manager: IO error occured opening connection

---

### Post by eamonireland on 2009-05-12
I'm a week without Ubuntu at this stage. Can anyone give me any pointers? I'm completely stuck. There has to be a way, surely?

---

### Post by eamonireland on 2009-05-13
OK. Got this sorted here [http://swiss.ubuntuforums.org/showthread.php?t=1139558]("http://swiss.ubuntuforums.org/showthread.php?t=1139558")

---

