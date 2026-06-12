---
title: "NIS user immediately logged out"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by cspence on 2009-11-04
NIS and automounting seem to work better now in Karmic than in Jaunty. (I'll skip the details for now.) Thanks to the people who fixed that! However when I log in as an nis user, the user's desktop background is briefly flashed on the screen, and then the user is immediately logged out. A user defined on the local machine and not in the NIS databases can log in just fine. I looked in the log files at the times of one of the NIS user log in attempts. Here are what I think are the relevant parts.

The auth log says:

Nov  4 08:19:44 cholla gdm-session-worker[10158]: pam_unix(gdm:session): session opened for user cds by (uid=0)
Nov  4 08:19:44 cholla gdm-session-worker[10158]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  4 08:19:47 cholla gdm-session-worker[10158]: pam_unix(gdm:session): session closed for user cds

messages says:

Nov  4 08:19:46 cholla kernel: [68138.357516] gvfs-gdu-volume[10273]: segfault at 84 ip 00fbec48 sp bfa8a4b0 error 4 in libdbus-1.so.3.4.0[fb2000+37000]
Nov  4 08:19:46 cholla kernel: [68138.613613] gvfs-gdu-volume[10278]: segfault at 84 ip 009a3c48 sp bf912780 error 4 in libdbus-1.so.3.4.0[997000+37000]
Nov  4 08:19:46 cholla kernel: [68139.221000] gnome-session[10211]: segfault at 8 ip 00900a8b sp bfc4e0d0 error 4 in libdevkit-power-gobject.so.1.0.1[8fe000+a000]
Nov  4 08:19:47 cholla bonobo-activation-server (cds-10306): could not associate with desktop session: Failed to connect to socket /tmp/dbus-8WEhBtrljL: Connection refused

I can post the syslog entry, if desired. Any suggestions?

---

### Post by jimicus on 2009-11-04
I have a very similar problem with an LTSP configuration I have here - though I'm using LDAP as the authentication backend.

So far I have established:


[LIST]
[*]   The problem lies with Gnome, not GDM or X.  (The problem persists if I switch XDM for GDM, it goes away if the user logs in with a TWM session rather than a gnome session).
[*]   It's nothing to do with any files in their home directory.  (This is being mounted over the network using pam_mount but the problem persists if pam_mount is disabled).
[*]  Like you, local users are unaffected.
[*] If I try to log in as an LDAP user 5 times in a row, the fifth and any subsequent tries will be successful.  This doesn't seem to be time related because if I start a client up and leave it for 10 minutes, it still takes 5 attempts to log in.
[/LIST]
It's that last point I'm having real trouble getting my head around...  I should add that I haven't found anything particularly useful despite extensive googling based on messages in the .xession-errors file.

I've pasted my .xsession-errors file here:  [http://pastebin.com/m6e87abc0](http://pastebin.com/m6e87abc0)

---

### Post by cspence on 2009-11-04
Multiple tries (eight) didn't make it work for me.

---

### Post by jimicus on 2009-11-05
I've built an entirely clean system (rather than the bastardised LTSP-based image I was booting from) and the problem remains - only I normally log in OK after the second or third attempt rather than requiring 5. 

A slight improvement, but not really what I'm looking for.

---

### Post by cspence on 2009-11-06
In case it matters, .xsession-errors in the directory of the user (cds) who can't log in says:

gnome-session[28517]: devkit-power-gobject-WARNING: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnome-settings-daemon:28531): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:28531): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/cds/.config/metacity/sessions/106bad99e2390b7049125751800172348100000285170001.ms: Failed to open file '/home/cds/.config/metacity/sessions/106bad99e2390b7049125751800172348100000285170001.ms': No such file or directory

** (gnome-settings-daemon:28531): WARNING **: Connection failed, reconnecting...

** (gnome-panel:28559): WARNING **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Unable to find a synaptics device.

(nautilus:28562): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:28559): DEBUG: Adding applet 0.
** (gnome-panel:28559): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:28559): DEBUG: Adding applet 1.
** (gnome-panel:28559): DEBUG: Adding applet 2.
Initializing nautilus-gdu extension

** (nautilus:28562): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:28562): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:28562): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(gnome-panel:28559): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11
** (gnome-panel:28559): DEBUG: Adding applet 3.
** (gnome-panel:28559): DEBUG: Adding applet 4.

(nautilus:28562): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11
** (gnome-panel:28559): DEBUG: Adding applet 5.
** (gnome-panel:28559): DEBUG: Adding applet 6.
** (gnome-panel:28559): DEBUG: Adding applet 7.
** (gnome-panel:28559): DEBUG: Adding applet 8.
** (gnome-panel:28559): DEBUG: Adding applet 9.
** (gnome-panel:28559): DEBUG: Adding applet 10.
** (gnome-panel:28559): DEBUG: Adding applet 11.
** (gnome-panel:28559): DEBUG: Adding applet 12.

** (gnome-panel:28559): WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** (gnome-panel:28559): DEBUG: Adding applet 13.
gnome-session[28517]: CRITICAL: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-panel:28559): WARNING **: Could not ask session manager if shut down is available: Message did not receive a reply (timeout by message bus)
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

(gnome-panel:28559): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed

---

### Post by korax on 2009-11-07
We have been having a similar problem with pam-ldap in karmic. I have only just started looking at pam, so I thought it must of been something I was doing wrong

It may be due to nscd starting after dbus (dbus is using upstart, nscd is init.d)

I've just written a quick upstart for nscd so that it starts before dbus and so far its working!

Here is my upstart script for nscd
/etc/init/nscd.conf
```

# nscd - Name Service Cache Daemon
#

description	"Name Service Cache Daemon"

start on (starting dbus)
stop on shutdown


pre-start script
    mkdir -m 0755 -p /var/run/nscd
    mkdir -m 0755 -p /var/db/nscd
end script

respawn
exec /usr/sbin/nscd

```

And I just disabled the old init.d script
# chmod -x /etc/init.d/nscd

After a restart, so far its working great.

---

### Post by cspence on 2009-11-09
Thanks, but that didn't work for me. Also, my computer does not have the file /etc/init.d/nscd, and did not have the file /etc/init/nscd.conf.

---

### Post by korax on 2009-11-09
Does it help if "nscd" is installed, and then the init script changed (as above)?

The problem I was having may be unrelated. It only seemed to occur for me when using cached ldap logins offline (using pam_ccreds).
It was having a very similar problem though with the users gnome session unable to connect to dbus

---

### Post by cspence on 2009-11-09
Doh!

Ok, I tried installing nscd. Now when I reboot, the nis user is no longer shown as an option, and password authentication fails for that user. ypcat shows the user, but trying to su to that user returns "Unknown id:".

---

### Post by cspence on 2009-12-14
I haven't solved this, but I am getting around it by explicitly exporting the appropriate directories so they can be seen by those machines that need to, and explicitly automounting those directories I need to see. Alas, our network of unix machines is not as extensive as it once was, so this kind of thing is adequate for now.

---

### Post by Craigacp on 2009-12-17
I have (what I think) is the same problem, as whenever you login to a 9.10 machine with NIS and the home directory automounted it immediately crashes back out to the login screen.

I've removed NetworkManager, set autofs to init after nis in all run levels. Curiously before I changed autofs it would let me log in, but then complain about my lack of home directory and not bring up the desktop.

I can ssh into the machine fine, and it automounts everything, so it must be a gdm problem.

---

### Post by Craigacp on 2010-02-15
> **Craigacp said:**
> I have (what I think) is the same problem, as whenever you login to a 9.10 machine with NIS and the home directory automounted it immediately crashes back out to the login screen.

I've removed NetworkManager, set autofs to init after nis in all run levels. Curiously before I changed autofs it would let me log in, but then complain about my lack of home directory and not bring up the desktop.

I can ssh into the machine fine, and it automounts everything, so it must be a gdm problem.

In the end deleting all the dot files made everything work. Not sure why at the moment, I'm trying to find out which dot file (or combination thereof) was causing the problem.

---

### Post by cspence on 2010-02-19
My hard disk with the OS died. Fortunately my home directory was on a different disk. I installed a new disk, installed the OS on it, and now this problem is gone. NIS and autofs are set up and everything works as it should, as far as I can tell. I don't know why.

---

### Post by jimicus on 2010-02-23
Thanks, Korax, that seems to have done the job.

---

### Post by Craigacp on 2010-02-24
> **Craigacp said:**
> In the end deleting all the dot files made everything work. Not sure why at the moment, I'm trying to find out which dot file (or combination thereof) was causing the problem.

Found the dotfile, it was an old version of .profile which my university uses to glue the linux accounts together.

After removing that all was well.

---

