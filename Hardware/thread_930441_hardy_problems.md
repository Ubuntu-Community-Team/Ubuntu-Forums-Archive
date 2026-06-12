---
title: "hardy problems"
date: 2008-09-26
forum: Hardware
---

### Post by CorntoeGoblin on 2008-09-26
monski@LinMon:~$ sudo network-admin
[sudo] password for monski: 

(network-admin:6523): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(network-admin:6523): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject
process 6523: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3280.
This is normally a bug in some application using the D-Bus library.

(network-admin:6523): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

** (network-admin:6523): CRITICAL **: Cannot create system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(network-admin:6523): Gtk-WARNING **: Unknown property: GtkComboBox.items


(network-admin:6523): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed
monski@LinMon:~$ sudo -s
root@LinMon:~# network-admin

(network-admin:6551): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(network-admin:6551): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject
process 6551: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3280.
This is normally a bug in some application using the D-Bus library.

(network-admin:6551): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

** (network-admin:6551): CRITICAL **: Cannot create system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(network-admin:6551): Gtk-WARNING **: Unknown property: GtkComboBox.items


(network-admin:6551): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed




///////////////////////////////////////////////////////////
/*                                                   //////
*/                                                   //////
///////////////////////////////////////////////////////////




that above is the console output when i try to start the network admin i also get a could not load configuration due to access with both root and user access. i was messing with the services to speed up my boot time and i think i disabled something necessary as my memory card slot doesnt mount anymore neither do usb drives. the windows partition loads fine and mounts automatically. also when i start the x server i got a hal failed to initialize. everything works fine and the boot speed did reduce but at the cost of networking, usb drives and memory stick! help me out here i tried everything even recovery mode and reset the x configuration.

---

### Post by chemical0815 on 2008-09-26
:-$

---

