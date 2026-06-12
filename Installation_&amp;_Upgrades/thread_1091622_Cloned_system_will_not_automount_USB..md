---
title: "Cloned system will not automount USB."
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by viordiasko on 2009-03-09
I recently cloned a Hardy i386 laptop to a desktop. After changing UUID's in fstab & a few details in grub's menu.lst as seems to be well (I'm currently typing this on the new box).

However, any USBkeys or hdd 's inserted are not automounted. An error message pops up:
> Cannot mount volume.

Error org.freedesktop.DBus.Error.AccessDenied

Details
A security policy in place prevents this sender from sending this message to the recipient, see the message bus configuration file(rejected message had interfae"org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")

But I can manually mount them as root.

Also, the network-manager applet has disappeared from the systray & I cannot run network-admin as root or user:
```
root@laptop:/etc/network# network-admin 

** (network-admin:9293): CRITICAL **: Cannot create session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(network-admin:9293): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:9293): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```



Any help would be much appreciated, thanks.

---

