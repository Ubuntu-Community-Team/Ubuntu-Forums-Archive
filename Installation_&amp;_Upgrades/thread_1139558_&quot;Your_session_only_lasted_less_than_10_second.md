---
title: "&quot;Your session only lasted less than 10 seconds&quot; after upgrade to 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ZioNemo on 2009-04-27
Hi,
I had a fairly standard 8.10 installation on an acer Aspire 8930 laptop.
After upgrade I consistently get the following error:

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

Logging in failsafe GNOME does *not* work either.

Content of ~/.xsessions-errors file is:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
GNOME_KEYRING_SOCKET=/tmp/keyring-oi13E1/socket
SSH_AUTH_SOCK=/tmp/keyring-oi13E1/socket.ssh
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/mauro/.config/metacity/sessions/108c8cd349e183e8fd124081738471193800000037830024.ms: Failed to open file '/home/mauro/.config/metacity/sessions/108c8cd349e183e8fd124081738471193800000037830024.ms': No such file or directory
Failure: Module initalization failed
gnome-session[3783]: WARNING: Unable to parse command '(null)': Key file contains key 'Terminal' which has value that cannot be interpreted.
gnome-session[3783]: ******************* START ********************************
gnome-session[3783]: Frame 0: /usr/bin/gnome-session [0x8061015]
gnome-session[3783]: Frame 1: /usr/bin/gnome-session [0x80611c4]
gnome-session[3783]: Frame 2: [0xb7fc9400]
gnome-session[3783]: Frame 3: /usr/lib/libglib-2.0.so.0(g_free+0x36) [0xb7944126]
gnome-session[3783]: Frame 4: /usr/lib/libglib-2.0.so.0(g_strfreev+0x20) [0xb795d090]
gnome-session[3783]: Frame 5: /usr/bin/gnome-session [0x806eba5]
gnome-session[3783]: Frame 6: /usr/bin/gnome-session [0x806f337]
gnome-session[3783]: Frame 7: /usr/bin/gnome-session [0x8052b77]
gnome-session[3783]: Frame 8: /usr/bin/gnome-session [0x8065606]
gnome-session[3783]: Frame 9: /usr/lib/libglib-2.0.so.0(g_hash_table_find+0x5c) [0xb792d29c]
gnome-session[3783]: Frame 10: /usr/bin/gnome-session [0x8065b47]
gnome-session[3783]: Frame 11: /usr/bin/gnome-session [0x8065de6]
gnome-session[3783]: Frame 12: /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84) [0xb79d23a4]
gnome-session[3783]: Frame 13: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb79c4c7b]
gnome-session[3783]: Frame 14: /usr/lib/libgobject-2.0.so.0 [0xb79dae57]
gnome-session[3783]: Frame 15: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9) [0xb79dc4b9]
gnome-session[3783]: Frame 16: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb79dc936]
gnome-session[3783]: Frame 17: /usr/bin/gnome-session [0x8051761]
gnome-session[3783]: Frame 18: /usr/bin/gnome-session [0x8069f2e]
gnome-session[3783]: Frame 19: /usr/bin/gnome-session [0x80589b6]
gnome-session[3783]: Frame 20: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb79c4c7b]
gnome-session[3783]: Frame 21: /usr/lib/libgobject-2.0.so.0 [0xb79dae57]
gnome-session[3783]: Frame 22: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f) [0xb79dc34f]
gnome-session[3783]: Frame 23: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb79dc936]
gnome-session[3783]: Frame 24: /usr/bin/gnome-session [0x805603c]
gnome-session[3783]: Frame 25: /usr/lib/libSM.so.6(_SmsProcessMessage+0xd5a) [0xb7fad9fa]
gnome-session[3783]: Frame 26: /usr/lib/libICE.so.6(IceProcessMessages+0x31a) [0xb7fa29fa]
gnome-session[3783]: Frame 27: /usr/bin/gnome-session [0x8056c11]
gnome-session[3783]: Frame 28: /usr/lib/libglib-2.0.so.0 [0xb7972dad]
gnome-session[3783]: Frame 29: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb793bb88]
gnome-session[3783]: Frame 30: /usr/lib/libglib-2.0.so.0 [0xb793f0eb]
gnome-session[3783]: Frame 31: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca) [0xb793f5ba]
gnome-session[3783]: Frame 32: /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb7c8e7d9]
gnome-session[3783]: Frame 33: /usr/bin/gnome-session [0x8062a09]
gnome-session[3783]: Frame 34: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb769c775]
gnome-session[3783]: Frame 35: /usr/bin/gnome-session [0x80511e1]
gnome-session[3783]: ******************* END **********************************

(nautilus:3907): EggSMClient-WARNING **: Failed to connect to the session manager: IO error occured opening connection

The cited file "/home/mauro/.config/metacity/sessions/108c8cd349e183e8fd124081738471193800000037830024.ms" does not exist, but its directory (/home/mauro/.config/metacity/sessions/) does exist and is writable.

I have been unable to find the "Key file contains key 'Terminal'" anywhere in my home dir.

If I *do not* close the messagebox the system is somewhat working (I'm using it to write this and I'm currently using synaptic to install KDE to see if that works), but not fully: some programs (e.g.: terminal) do not start at all.

When I close the message box the session is terminated and I must re-log.

I tried several things before yelling for help:

I checked permissions in my home dir.
I checked available space on my filesystems.
I tried dpkg-reconfigure xserver-xorg.
I moved out of the way all gnome related configuration dirs in my home:
  .gconf
  .gconfd
  .gnome
  .gnome-private

No change.
HEEEEELLLPPPP!!!!

TiA
ZioNemo

---

### Post by sourchier on 2009-04-27
Have you tried
code:
mv ~.config ~.config-old
then logging out and logging back in?

---

### Post by ZioNemo on 2009-04-27
> **sourchier said:**
> Have you tried
code:
mv ~.config ~.config-old
then logging out and logging back in?

Thanks.
I forgot that.
Now I'm logged in Gnome without the "less than 10 seconds" error, but I was greeted by another error.
Apparently the user switcher applet does not like to be loaded... end it isn't the only one.

I will try to understand what's wrong and how to re-enable my customizations.

In the meantime I had tried installing KDE and I found what I believe it is a real bug (perhaps two):

Installing KDE installs a ton of programs, from PIM to games, but *does NOT* install knetworkmanager. This means that I have no net under KDE (I am using WiFi to connect this laptop).

I went back to Gnome, installed knetworkmanager and then returned to KDE.
There seems to be no way (I admit I do not know KDE well, but I searched carefully) to start this applet automatically; I had to launch it by hand (and will not be launched next time I login!).

Did anyone experience this?
To whom should I notify?

TiA
ZioNemo

---

### Post by phantom3113 on 2009-04-27
I remember hearing that there was a bug with that. If I recall correctly, adding the manager applet to the tray was the fix for it. I'll look around to see if I can find the page/article/thread that covered that.

---

### Post by ZioNemo on 2009-04-28
> **phantom3113 said:**
> I remember hearing that there was a bug with that. If I recall correctly, adding the manager applet to the tray was the fix for it. I'll look around to see if I can find the page/article/thread that covered that.

AAAARRRRGGGGHHHHH!!!

The error is back!
Apparently I didn't do anything "strange" (actually I removed KDE from my setup, if that matters), but, after a reboot I have the error back.

I can work "normally" by starting a "terminal" session and then doing a ```
gnome-session
``` by hand.

Additional info:
Problem seems to be with gdm. I installed kdm and it can start a gnome session almost without errors.
I will try to understand what's going on, but I would really appreciate help.

I do not want to reinstall everything.
Can someone help me?
Pretty please!

TiA
ZioNemo

---

### Post by jsonder on 2009-04-28
I use wicd instead of network manager.  Try here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

The less than 10 seconds error used to be a video card/monitor problem; recent versions of linux have gone to a default setting and recognition of old hardware is less than excellent.  You may need to install in a video failsafe mode.

---

### Post by sourchier on 2009-04-29
Could you try creating a new user then logging into that account?
Code:
sudo adduser somename
If that works, you can migrate your account to the new one.

---

### Post by ZioNemo on 2009-04-29
> **sourchier said:**
> Could you try creating a new user then logging into that account?
Code:
sudo adduser somename
If that works, you can migrate your account to the new one.

I tried that.
I created a new account via System->Administration->Users&Groups (I can somewhat work if I do not close the error-box; I'm doing it now).

The first time I tried to login it said something like "new user created" and then the session was closed.
The second time I was logged in normally.
The third time the "Your session only lasted less than 10 seconds" error appeared again.

In /usr/log/messages I see:

Apr 29 12:45:39 wiki3A -- MARK --
Apr 29 12:46:44 wiki3A kernel: [50485.420626] __ratelimit: 3 callbacks suppressed
Apr 29 12:46:44 wiki3A kernel: [50485.420630] gdm[19144]: segfault at 8c ip 0805e013 sp bfcbbdb0 error 4 in gdm[8048000+4d000]
Apr 29 12:47:40 wiki3A bonobo-activation-server (test-20319): could not associate with desktop session: Failed to connect to socket /tmp/dbus-DHx65ptAm4: Connection refused
Apr 29 12:47:58 wiki3A pulseaudio[20486]: pid.c: Stale PID file, overwriting.
Apr 29 12:48:21 wiki3A pulseaudio[20774]: pid.c: Stale PID file, overwriting.
Apr 29 12:50:18 wiki3A kernel: [50699.525323] gdm[21201]: segfault at 8c ip 0805e013 sp bfcbbdb0 error 4 in gdm[8048000+4d000]
Apr 29 12:50:18 wiki3A kernel: [50699.771578] gdm[21414]: segfault at 8c ip 0805e013 sp bfcbbb90 error 4 in gdm[8048000+4d000]
Apr 29 12:50:18 wiki3A kernel: [50699.919647] gdm[21415]: segfault at 8c ip 0805e013 sp bfcbb960 error 4 in gdm[8048000+4d000]
Apr 29 12:52:12 wiki3A pulseaudio[21785]: pid.c: Stale PID file, overwriting.
Apr 29 12:52:19 wiki3A bonobo-activation-server (test-21919): could not associate with desktop session: Failed to connect to socket /tmp/dbus-CoalD03jaF: Connection refused
Apr 29 12:52:31 wiki3A pulseaudio[22075]: pid.c: Stale PID file, overwriting.
Apr 29 12:52:49 wiki3A pulseaudio[22353]: pid.c: Stale PID file, overwriting.
Apr 29 12:52:52 wiki3A bonobo-activation-server (test-22463): could not associate with desktop session: Failed to connect to socket /tmp/dbus-JRsQwSMcMJ: Connection refused
Apr 29 12:53:05 wiki3A pulseaudio[22590]: pid.c: Stale PID file, overwriting.

The times are approximately those where I did my user tests.
Any idea of what does it mean?
TiA
ZioNemo

P.S.:
I tried to install kdm, but no session will start (X crashes):
Apr 29 13:09:14 wiki3A kernel: [   35.008845] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 29 13:09:16 wiki3A kernel: [   36.593421] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 29 13:09:45 wiki3A bonobo-activation-server (mauro-3951): could not associate with desktop session: Failed to connect to socket /tmp/dbus-GbSUdpzFHY: Connection refused
Apr 29 13:09:48 wiki3A pulseaudio[4000]: pid.c: Stale PID file, overwriting.
Apr 29 13:11:58 wiki3A kernel: [  198.576247] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 29 13:14:37 wiki3A pulseaudio[4719]: pid.c: Stale PID file, overwriting.
Apr 29 13:15:31 wiki3A pulseaudio[5037]: pid.c: Stale PID file, overwriting.
Apr 29 13:16:02 wiki3A kernel: [  442.592082] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 29 13:16:02 wiki3A kernel: [  442.592180] CE: hpet increasing min_delta_ns to 22500 nsec
Apr 29 13:16:14 wiki3A kernel: [  454.565369] nfsd: last server has exited, flushing export cache
Apr 29 13:16:14 wiki3A exiting on signal 15
Apr 29 13:17:19 wiki3A syslogd 1.5.0#5ubuntu3: restart.
Apr 29 13:17:19 wiki3A kernel: Inspecting /boot/System.map-2.6.28-11-generic
Apr 29 13:17:20 wiki3A kernel: Cannot find map file.
Apr 29 13:17:20 wiki3A kernel: Loaded 59134 symbols from 49 modules.

Then I switched back to gdm and I discovered I apparently have just "one life" for each user. I mean: after reboot I can log normally, but, if I logout I cannot login again.
I can log to another user, but also that only once.
I did only a few tries, so I cannot be sure this pattern really holds, but it seems so.
This is really weird.
Can someone suggest what to try?

TiA
ZioNemo

---

### Post by sourchier on 2009-04-30
Could you try using
code:

sudo chown root:user /home/someuser/.ICEauthority
sudo chmod 600 /home/someuser/.ICEauthority

then logging out and logging back in? Or trying
code:
sudo chown someuser:someuser /home/someuser/.ICEauthority

Or if that does not work
code:
sudo mv /home/someuser/.ICEauthority /home/someuser/.ICEauthority-old

---

### Post by eamonireland on 2009-05-05
I have this same problem. I had Jaunty running for about 3 days, but now I get this error. First time I try to log on I get back to the Logon screen, and when I do it a second time get the less than 10 seconds message. Some applications load up, but a small Firefox window is in the top left, and I can't close it or move it, so I can't get anything running. No menu options, and no terminal application, so I can't run anything.

Help. I've been on Ubuntu since Feisty or Gutsy and this is the worst problem I've faced. I just can't work out how to proceed. I'm completely stuck with lots of work to do. Help.

---

### Post by eamonireland on 2009-05-05
OK, managed to change .ICEauthority to .ICEauthorityold, but a new one was just set up. I tried to change the CHOWN and CHMOD commands, the gave me no message to say if they'd worked or not, and i'm pretty unsure about the syntax, so I don't think they did. Either way, they didn't fix the problem.

Completely flummoxed. Back in Windows :(

---

### Post by juje on 2009-05-05
Same problem here...i've been using jaunty for 3 days now i'm have that 10 seconds session problem...i'll try the .ICEauthority thing and post how it works...if i have the chance to restart my box...if not, hope somebody post an answer...

---

### Post by eamonireland on 2009-05-05
Still no luck. It took me ages to even copy the .xsessions-errors file because I can't get text editor to work. Managed to open it through Firefox in the end.

Does this give anyone any clues to the problem?
---
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Unable to create /home/eamon/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-U3ihOd/socket
SSH_AUTH_SOCK=/tmp/keyring-U3ihOd/socket.ssh
x-session-manager[4117]: WARNING: Could not launch application 'launchy.desktop': Unable to start application: Failed to execute child process "launchy" (No such file or directory)
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XFree86.conf to use GSynaptics
x-session-manager[4117]: WARNING: Could not launch application '106153b4ac7667863f124138984694270700000037390032.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
x-session-manager[4117]: ******************* START ********************************
x-session-manager[4117]: Frame 0: x-session-manager [0x8061015]
x-session-manager[4117]: Frame 1: x-session-manager [0x80611c4]
x-session-manager[4117]: Frame 2: [0xb8073400]
x-session-manager[4117]: Frame 3: /usr/lib/libglib-2.0.so.0(g_free+0x36) [0xb79ec126]
x-session-manager[4117]: Frame 4: /usr/lib/libglib-2.0.so.0(g_strfreev+0x20) [0xb7a05090]
x-session-manager[4117]: Frame 5: x-session-manager [0x806eba5]
x-session-manager[4117]: Frame 6: x-session-manager [0x806f337]
x-session-manager[4117]: Frame 7: x-session-manager [0x8052b77]
x-session-manager[4117]: Frame 8: x-session-manager [0x8065606]
x-session-manager[4117]: Frame 9: /usr/lib/libglib-2.0.so.0(g_hash_table_find+0x5c) [0xb79d529c]
x-session-manager[4117]: Frame 10: x-session-manager [0x8065b47]
x-session-manager[4117]: Frame 11: x-session-manager [0x8065de6]
x-session-manager[4117]: Frame 12: /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84) [0xb7a7a3a4]
x-session-manager[4117]: Frame 13: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb7a6cc7b]
x-session-manager[4117]: Frame 14: /usr/lib/libgobject-2.0.so.0 [0xb7a82e57]
x-session-manager[4117]: Frame 15: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9) [0xb7a844b9]
x-session-manager[4117]: Frame 16: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb7a84936]
x-session-manager[4117]: Frame 17: x-session-manager [0x8051761]
x-session-manager[4117]: Frame 18: x-session-manager [0x8069f2e]
x-session-manager[4117]: Frame 19: x-session-manager [0x80589b6]
x-session-manager[4117]: Frame 20: /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb7a6cc7b]
x-session-manager[4117]: Frame 21: /usr/lib/libgobject-2.0.so.0 [0xb7a82e57]
x-session-manager[4117]: Frame 22: /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f) [0xb7a8434f]
x-session-manager[4117]: Frame 23: /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb7a84936]
x-session-manager[4117]: Frame 24: x-session-manager [0x805603c]
x-session-manager[4117]: Frame 25: /usr/lib/libSM.so.6(_SmsProcessMessage+0xd5a) [0xb80559fa]
x-session-manager[4117]: Frame 26: /usr/lib/libICE.so.6(IceProcessMessages+0x31a) [0xb804a9fa]
x-session-manager[4117]: Frame 27: x-session-manager [0x8056c11]
x-session-manager[4117]: Frame 28: /usr/lib/libglib-2.0.so.0 [0xb7a1adad]
x-session-manager[4117]: Frame 29: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb79e3b88]
x-session-manager[4117]: Frame 30: /usr/lib/libglib-2.0.so.0 [0xb79e70eb]
x-session-manager[4117]: Frame 31: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca) [0xb79e75ba]
x-session-manager[4117]: Frame 32: /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb7d367d9]
x-session-manager[4117]: Frame 33: x-session-manager [0x8062a09]
x-session-manager[4117]: Frame 34: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7744775]
x-session-manager[4117]: Frame 35: x-session-manager [0x80511e1]
x-session-manager[4117]: ******************* END **********************************

(update-notifier:4235): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(firefox:4236): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:4261): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:4244): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:4256): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(nautilus:4231): EggSMClient-WARNING **: Failed to connect to the session manager: IO error occured opening connection

---

### Post by sourchier on 2009-05-06
Could someone who is affected by this issue please run
code:
sudo apt-get install gnome-session --reinstall

then do a
code:
gnome-session &

and report if it helps or there is no change.
Thanks :)

---

### Post by eamonireland on 2009-05-06
Thanks for trying to help. I feel so stuck here. 

Yesterday, following another thread I tried 

dpkg-reconfigure xserver-xorg

which didn't help.

Now I've tried your commands above, and got the message in terminal:

**(gnome-session: 4621) warning **: cannot open display

I paste the .xsession-errors below, which now has additional GLX and compiz errors.

Without access to my files since Tuesday, I'm totally stumped and disillusioned. Would really appreciate help.
----
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Unable to create /home/eamon/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-6cRSQL/socket
SSH_AUTH_SOCK=/tmp/keyring-6cRSQL/socket.ssh
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
x-session-manager[4965]: WARNING: Could not launch application 'launchy.desktop': Unable to start application: Failed to execute child process "launchy" (No such file or directory)
** (gnome-panel:5077): DEBUG: Adding applet 0.
** (gnome-panel:5077): DEBUG: Initialized Panel Applet Signaler.
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XFree86.conf to use GSynaptics
** (gnome-panel:5077): DEBUG: Adding applet 1.
x-session-manager[4965]: WARNING: Could not launch application '106153b4ac7667863f124138984694270700000037390032.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
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
x-session-manager[4965]: Frame 29: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb7959b88]
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

### Post by sourchier on 2009-05-07
You can get hep for enabling your nvidia drivers here:
[http://ubuntuforums.org/showthread.php?t=1139101&highlight=jaunty+nvidia](http://ubuntuforums.org/showthread.php?t=1139101&highlight=jaunty+nvidia)

and it should fix your "Xlib: extension "GLX" missing on display ":0.0" errors.

Regarding these errors "/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed"; there is a helpfull script here:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Lastly regarding your "You have to set 'SHMConfig' 'true' in xorg.conf or XFree86.conf to use GSynaptics" you can add/modify the following to your xorg.conf

code:
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizEdgeScroll" "0"
        Option "SHMConfig" "true"
EndSection

don't forget to make a backup of this file before editing. Like this

code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

---

### Post by eamonireland on 2009-05-07
OK, I'll fix these. But I presume none of this fixes the underlying problem?

---

### Post by aidan.dixon on 2009-05-08
I too got this problem over the last two days since upgrading from Intrepid to Jaunty last weekend.  WIth KDM running, my login would bomb out immediately; with GDM, I could continue working until clicking OK on that dialog box (the one saying "your session lasted 10 seconds".  I could get a browser (and found this thread) but not a terminal emulator of any kind.

This was fixed for me last night by simply deleting $HOME/.ICEauthority and letting the session manager (or something else) recreate it at the following login.  Tried logging in and out a couple more times since then and it hasn't come back.

---

### Post by eamonireland on 2009-05-10
Thanks, Aidan.

I tried this, but it didn't work. .ICEauthority is set up again, and the problem remains.

---

### Post by aidan.dixon on 2009-05-10
Indeed, Eamonn - I spoke well to soon!  It came back for me again last night but disappeared again.  So, still don't know what's going on :-(

---

### Post by George007 on 2009-05-12
Alright I had the same problem and well the way i fixed after a looong time with fiddling and googling and stuff, and couldn't find the solution, so I ended up improvising, here's what I did to make it work:


go to: {HOME}/{user}/.config/

and removed those two folders:

session-state
gnome-session

I am unsure which one of them fixed the problem, but I removed both of them...

I hope this helps.

Regards,
George

---

### Post by eamonireland on 2009-05-13
George! 

Thanks a million. This has got me back on for the first time in 8 days. Thanks.

I seem to be running a bit slowly now, but perhaps that's something else to be investigated. 

Thank you!

Éamon

---

### Post by George007 on 2009-05-13
You're welcome :)

I don't think the slowness is caused by that. Ubuntu 9.04 runs slow when ran on an intel gcard. You might wanna check out: [Performance regressions on Intel graphics cards - Ubuntu 9.04 releasenotes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards")

---

### Post by aidan.dixon on 2009-06-19
Hi George and Eamonn, this works for me too.  Strange however that it happens every time I log in on my work laptop (ancient celeron, 512MB RAM, ATI M4 graphics) but only occasionally on my home desktop (P4 2.8GHz, 2.5GB RAM, Nvidia FX5200 graphics).

Maybe graphics-card related but maybe not.

---

### Post by arshia on 2009-06-29
Thanks,

I stuck with that for 3 days! Appreciate it.

---

### Post by toryt on 2009-07-13
Another possible solution.
Delete .Xclients
I believe switchdesk inserts this file, which evidently causes problems later. RH has switchdesk, not sure if Ubuntu does. 
-toryt

---

### Post by sairam15 on 2009-07-25
Ubuntu 9.04 Jaunty Jackalope
I have been having this same problem "Your session only lasted less than 10 seconds" after upgrade to 9.04. Jaunty was running fine for about 3 days, but now I get this error. I have tried the following
1, Logged in as root and other users and the problem persists
2. checked if the home directory was not pointing ok and it is pointing to the right location
3. installed xfce and tried changing the session to xfce or KDE but  results in the same error
4. I have an nVidia card and checked to see if the drivers of those were creating the problem and that is not the case
4. Tried applying the ICEauthority workaround suggested and sadly that doesnt work
5. chmod my permissions as suggested still no avail

The only thing that works is me manually changing the session to a failsafe GNOME everytime I login. As this server is in the data center it requires me to go down there everytime I bootup. COuld somebody please help
The contents of the .xsession-errors file for both root and the other users is 
/etc/gdm/Xsession: Beginning session setup...
export: 29: : bad variable name

will greatly appreciate if you could help me out

---

### Post by burstmode on 2009-07-27
I had an issue with my /tmp partition, then started seeing this same problem ("Your session only lasted less than 10 seconds"). 

As it turns out, while working around the /tmp partition issue, I ended up with some files/folders in /tmp for which my userid no longer had write permissions.   I granted write access to everything under /tmp recursively, and it fixed the issue, e.g. : 

```

   sudo chmod -R a+w /tmp

```

---

### Post by gar1t on 2009-07-28
The problem I'm seeing is related to ~/.xsession. Whenever this file exists, I get the problem described in this thread.

You need to delete ~/.xsession and also clear ~/.config/gnome-session.

This appeared to start happening when I upgraded to Hardy.

---

### Post by sairam15 on 2009-07-30
Thanks for recommendation. After I performed the steps the session lasted for less than 10 seconds has gone away but am presented with a different error. What I have now is "No exec line in the session file : xfce. Running the GNOME failsafe session insted"

I tried to change the session but I dont get the GNOME and KDE session options, I am presuming that this is due to the change I made. Could you advice how I can restore this to the default GNOME session ?

---

### Post by InkyDinky on 2009-10-28
I just recently ran into this problem after updating my machine with some packages. I think all you need to delete is the gnome_session folder.  That should do it.  It did it for me.  I think if you delete the session_state you just delete the database file of the open windows when you exit. I think the problem in the gnome_session folder is the apps it tries to startup when logging in.

---

### Post by xeffer on 2010-11-21
i have this same problem... how do i delete the gnome session folder-if anyone can help please...

---

