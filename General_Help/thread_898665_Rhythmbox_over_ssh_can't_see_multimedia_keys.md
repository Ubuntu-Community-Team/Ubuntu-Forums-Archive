---
title: "Rhythmbox over ssh can't see multimedia keys"
date: 2008-08-23
forum: General Help
---

### Post by Endolith on 2008-08-23
I can run Rhythmbox from my other computer through ssh -X and play music through the other computer's speakers, but it won't recognize my multimedia keys.

> Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

These are apparently handled by dbus, and other people have other problems with features that are dbus-only, so maybe that's related:

[http://ubuntuforums.org/showthread.php?t=395163](http://ubuntuforums.org/showthread.php?t=395163)

---

### Post by Nepherte on 2008-08-23
I know it's not an answer to your question, but mpd is designed to do what you want: control the music on a computer remotely.

---

### Post by Endolith on 2008-08-24
Someone said dbus-launch is the key.  Does anyone know how to use this?  The manual is not very meaningful to me.

---

### Post by Endolith on 2008-08-25
From dbus-launch manual:

       > There  are  two  common reasons for autolaunch. One is ssh to a remote machine. The ideal fix for that would be forwarding of DBUS_SESSION_BUS_ADDRESS in
       the same way that DISPLAY is forwarded.  In the meantime, you can edit the session.conf config file to have your session bus listen on TCP, and  manually
       set DBUS_SESSION_BUS_ADDRESS, if you like.

       The  second  common  reason for autolaunch is an su to another user, and display of X applications running as the second user on the display belonging to
       the first user. Perhaps the ideal fix in this case would be to allow the second user to connect to the session bus of the first user, just  as  they  can
       connect to the first user’s display.  However, a mechanism for that has not been coded.

       You  can  always  avoid  autolaunch by manually setting DBUS_SESSION_BUS_ADDRESS. Autolaunch happens because the default address if none is set is "auto&#8208;
       launch:", so if any other address is set there will be no autolaunch. You can however include autolaunch in an explicit session bus address  as  a  fall&#8208;
       back, for example DBUS_SESSION_BUS_ADDRESS="something:,autolaunch:" - in that case if the first address doesn’t work, processes will autolaunch. (The bus
       address variable contains a comma-separated list of addresses to try.)

So it looks like this is not implemented yet?  But is it possible to forward all dbus things from my server to my laptop?  Would that then show me errors and notifications that my server generated on my laptop's screen?  That would be very useful.

---

### Post by Endolith on 2008-08-25
The command

```
dbus-monitor "interface='org.gnome.SettingsDaemon.MediaKeys'"

```

monitors the multimedia keys sent by d-bus:

```
signal sender=org.freedesktop.DBus -> dest=:1.50 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.50"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string "Rhythmbox"
   string "Stop"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string "Rhythmbox"
   string "Play"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string "Rhythmbox"
   string "Previous"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string "Rhythmbox"
   string "Next"

```

If I close the local Rhythmbox they apparently go nowhere:

```
method call sender=:1.47 -> dest=:1.1 path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=ReleaseMediaPlayerKeys
   string "Rhythmbox"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string ""
   string "Next"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string ""
   string "Previous"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string ""
   string "Stop"
signal sender=:1.1 -> dest=(null destination) path=/org/gnome/SettingsDaemon/MediaKeys; interface=org.gnome.SettingsDaemon.MediaKeys; member=MediaPlayerKeyPressed
   string ""
   string "Play"

```

If I open a remote Rhythmbox, nothing happens to this monitor, so they apparently aren't connecting.  Remote Rhythmbox gives this error, which local Rhythmbox does not:

> Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name


Somehow I need to redirect the remote Rhythmbox to think that "org.gnome.SettingsDaemon" is on my local machine hostname?  I'm in over my head.

---

### Post by Endolith on 2008-08-25
"D-Bus is an inter-process communication mechanism—a medium for local communication between processes running on the same host. (Inter-host connects may be added in the future, but that is not what D-Bus is meant for)."

---

