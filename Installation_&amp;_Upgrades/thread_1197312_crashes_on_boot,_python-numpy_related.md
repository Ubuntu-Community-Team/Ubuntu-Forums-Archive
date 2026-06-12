---
title: "crashes on boot, python-numpy related?"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by pdizzle on 2009-06-26
i have recently purchased an msi wind 123 and i must say i enjoy linux on it very much.  this isn't my first attempt at using linux but i guess i would say it is my first serious attempt as i am planning to rely entirely on this computer in the near future.

as part of my customization i am just trying to get music applet to work on jaunty.  i have been upgrading and installing many aspects of python in order to get this to work. i was having a problem getting it to load, i can't get the exact message because i'm booting off a live sd card right now :).  it was something: like oafiid:gnome_music_applet. i read elsewhere that this error appears because i am lacking the package python-numpy, so i sudo aptitude install python-numpy.

now i reboot and as soon as i login i crash, within seconds.  and error window pops up telling me i can view error logs and that i should reboot in a failsafe profile but unfortunately i have no touchpand, keyboard or usb mouse function at this point. now that i have booted from a live sd card i am able to post the error log in hopes that someone can dig me out of this mess.

.xsession-errors:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: polkit.c: Cannot connect to system bus: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: No such file or directory
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Daemon startup failed.
x-session-manager[2778]: WARNING: Could not connect to ConsoleKit: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: No such file or directory
x-session-manager[2778]: CRITICAL: dbus_g_connection_get_connection: assertion `gconnection' failed
process 2778: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3298.
This is normally a bug in some application using the D-Bus library.
  D-Bus not built with -rdynamic so unable to print a backtrace
x-session-manager[2778]: ******************* START ********************************
x-session-manager[2778]: Frame 0: x-session-manager [0x8061015]
x-session-manager[2778]: Frame 1: x-session-manager [0x80611c4]
x-session-manager[2778]: Frame 2: [0xb7f50400]
x-session-manager[2778]: Frame 3: /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb763b098]
x-session-manager[2778]: Frame 4: /usr/local/lib/libdbus-1.so.3 [0xb7ada745]
x-session-manager[2778]: Frame 5: /usr/local/lib/libdbus-1.so.3 [0xb7ad60e9]
x-session-manager[2778]: Frame 6: /usr/local/lib/libdbus-1.so.3(dbus_connection_send_with_reply_and_block+0x12e) [0xb7abd8fe]
x-session-manager[2778]: Frame 7: x-session-manager [0x8058a65]
x-session-manager[2778]: Frame 8: x-session-manager [0x8058b40]
x-session-manager[2778]: Frame 9: x-session-manager [0x8062517]
x-session-manager[2778]: Frame 10: x-session-manager [0x8062af6]
x-session-manager[2778]: Frame 11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7624775]
x-session-manager[2778]: Frame 12: x-session-manager [0x80511e1]
x-session-manager[2778]: ******************* END **********************************
```thanks in advance for any advice and help, sorry if this is a repeat, i did search, promise!

---

