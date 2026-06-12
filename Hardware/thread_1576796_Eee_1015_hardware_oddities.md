---
title: "Eee 1015 hardware oddities"
date: 2010-09-17
forum: Hardware
---

### Post by ThatBum on 2010-09-17
Hello. I removed Windows 7 Starter and put Ubuntu on my ASUS Eee 1015PE netbook a while ago. It runs fine and is very power efficient, and much better than 7 in actually doing things. However, I seem to have a couple of odd hardware problems with it.

1. Brightness. I found through     combing the forum, that I could enable the Function keys (the useful     ones anyway) by putting “acpi_osi=Linux” in my kernel parameters     in Grub. This, though, seems to make Ubuntu unaware of the     brightness keys. The little notify-osd thing that comes up when I     change the brightness isn't there anymore. It has 11 states of     brightness, when before it went in about 5.

I also learned that putting     “acpi_backlight=vendor” will bring the control of the brightness     from the BIOS (I think) to Linux. This kind of works, but it's very     buggy. The notify-osd thing comes up, but the bar won't go up all     the way. It seems to think it goes in the fewer amount of steps, but     it still going in the BIOS-controlled ones, so it gets out of sync.

Also, possibly unrelated, the     brightness applet for gnome-panel, if I right click it to bring down     the slider and then try to move the slider, it just disappears. It     will only work if I left click it to bring down the menu, and then     click the slider behind it. This happens with acpi_backlight on or     off.

    2. Bluetooth, the main problem     seeming to be that bluetoothd is randomly terminating. I used     gnome-bluetooth for awhile, the default indicator applet thing, but     that gave me too much guff, so I got blueman, which seems to be more     flexible. I noticed that it worked just after I installed it, but if     I rebooted it, the applet was nowhere to be seen in the panel. After     some digging, I found it needed the 'bluez daemon' to start, which     is just bluetoothd. The rc0.d script K74bluetooth didn't seem to be     working, so I put /usr/sbin/bluetoothd in the sudoers, put 'sudo     bluetoothd' in rc.local, and rebooted. THAT worked, but after a few     hours, bluetoothd seemed to go down again. The time it takes for it     to go down is totally random. Also, 'sudo service bluetooth     start/stop' and 'sudo /etc/init.d/bluetooth stop/start' both work it     controlling the daemon. I would post some logs if I could, but     bluetoothd doesn't give any output.

The reason I discovered it was     bluetoothd, is that gnome-bluetooth was having spotty control over     the bluetooth adapter. It seems when you turn off bluetooth in     gnome-bluetooth, it actually kills the daemon, but in blueman, this     is not so, and, in fact, it is required to be running for the applet     to work. So when I rebooted after getting blueman and tried to run     the manager, it said it needed bluez to be running, which, again, is     bluetoothd.

    The contents of K74 bluetooth:```
#! /bin/sh 
 ### BEGIN INIT INFO 
 # Provides: bluetooth 
 # Required-Start:    $local_fs $syslog $remote_fs dbus 
 # Required-Stop:     $local_fs $syslog $remote_fs 
 # Default-Start:     2 3 4 5 
 # Default-Stop:      0 1 6 
 # Short-Description: Start bluetoothd 
 ### END INIT INFO 
  
 . /lib/lsb/init-functions 
  
 set -e 
  
 case "$1" in 
   start) 
     #currently this init script exists only because of what appears to be 
     #an egg and chicken problem 
     #  bluetoothd normally starts up by udev rules.  it needs dbus to function, 
     #  but dbus doesn't start up until after udev finishes triggering 
     # 
     if [ ! -f /sbin/udevadm.upgrade ]; then 
       udevadm trigger --subsystem-match=bluetooth 
     fi 
     ;; 
   stop) 
     pkill -TERM bluetoothd || true 
     ;; 
   restart|force-reload) 
     $0 stop 
     $0 start 
     ;; 
   status) 
     status_of_proc "bluetoothd" "bluetooth" && exit 0 || exit $? 
     ;; 
   *) 
     N=/etc/init.d/bluetooth 
     # echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2 
     echo "Usage: $N {start|stop|restart|force-reload|status}" >&2 
     exit 1 
     ;; 
 esac 
  
   exit 0
```I think that's it. If I can uncover anything else, I'll put it here. If I get more solid information I'll try a bug report.
 
 Thanks all.

Edit: Ah, I stand corrected. I looked at my daemon.log, and found a ton of stuff.

```
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1368]: Bluetooth daemon 4.60
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1369]: Starting SDP server
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1369]: Starting experimental netlink support
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1369]: Failed to find Bluetooth netlink family
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1369]: Failed to init netlink plugin
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1369]: bridge pan0 created
Sep 17 10:48:24 NetbookOfAwesomeness bluetoothd[1369]: HCI dev 0 registered
Sep 17 10:48:25 NetbookOfAwesomeness bluetoothd[1369]: HCI dev 0 up
Sep 17 10:48:25 NetbookOfAwesomeness bluetoothd[1369]: Starting security manager 0
Sep 17 10:48:25 NetbookOfAwesomeness bluetoothd[1369]: Adapter /org/bluez/1368/hci0 has been enabled
Sep 17 10:48:25 NetbookOfAwesomeness bluetoothd[1369]: HCI dev 0 registered
Sep 17 10:48:25 NetbookOfAwesomeness bluetoothd[1369]: Unable to register adapter: hci0 already exist
Sep 17 10:48:29 NetbookOfAwesomeness bluetoothd[1369]: HCI dev 0 down
Sep 17 10:48:29 NetbookOfAwesomeness bluetoothd[1369]: Adapter /org/bluez/1368/hci0 has been disabled
Sep 17 10:48:29 NetbookOfAwesomeness bluetoothd[1369]: Stopping security manager 0
Sep 17 10:48:29 NetbookOfAwesomeness bluetoothd[1369]: HCI dev 0 unregistered
Sep 17 10:48:29 NetbookOfAwesomeness bluetoothd[1369]: Unregister path: /org/bluez/1368/hci0
Sep 17 10:49:00 NetbookOfAwesomeness bluetoothd[1369]: bridge pan0 removed
Sep 17 10:49:00 NetbookOfAwesomeness bluetoothd[1369]: Stopping SDP server
Sep 17 10:49:00 NetbookOfAwesomeness bluetoothd[1369]: Exit
Sep 17 10:51:24 NetbookOfAwesomeness bluetoothd[1449]: Bluetooth daemon 4.60
Sep 17 10:51:24 NetbookOfAwesomeness bluetoothd[1449]: Unable to get on D-Bus
Sep 17 10:51:31 NetbookOfAwesomeness bluetoothd[1453]: Bluetooth daemon 4.60
Sep 17 10:51:31 NetbookOfAwesomeness bluetoothd[1453]: Starting SDP server
Sep 17 10:51:31 NetbookOfAwesomeness bluetoothd[1453]: Starting experimental netlink support
Sep 17 10:51:31 NetbookOfAwesomeness bluetoothd[1453]: Failed to find Bluetooth netlink family
Sep 17 10:51:31 NetbookOfAwesomeness bluetoothd[1453]: Failed to init netlink plugin
Sep 17 10:51:31 NetbookOfAwesomeness bluetoothd[1453]: bridge pan0 created
Sep 17 10:57:37 NetbookOfAwesomeness bluetoothd[1681]: Bluetooth daemon 4.60
Sep 17 10:57:37 NetbookOfAwesomeness bluetoothd[1681]: Unable to get on D-Bus
Sep 17 10:57:47 NetbookOfAwesomeness bluetoothd[1453]: bridge pan0 removed
Sep 17 10:57:47 NetbookOfAwesomeness bluetoothd[1453]: Stopping SDP server
Sep 17 10:57:47 NetbookOfAwesomeness bluetoothd[1453]: Exit
Sep 17 10:57:49 NetbookOfAwesomeness bluetoothd[1685]: Bluetooth daemon 4.60
Sep 17 10:57:49 NetbookOfAwesomeness bluetoothd[1685]: Starting SDP server
Sep 17 10:57:49 NetbookOfAwesomeness bluetoothd[1685]: Starting experimental netlink support
Sep 17 10:57:49 NetbookOfAwesomeness bluetoothd[1685]: Failed to find Bluetooth netlink family
Sep 17 10:57:49 NetbookOfAwesomeness bluetoothd[1685]: Failed to init netlink plugin
Sep 17 10:57:49 NetbookOfAwesomeness bluetoothd[1685]: bridge pan0 created
Sep 17 11:01:05 NetbookOfAwesomeness bluetoothd[1056]: Bluetooth daemon 4.60
Sep 17 11:01:05 NetbookOfAwesomeness bluetoothd[1056]: Starting SDP server
Sep 17 11:01:05 NetbookOfAwesomeness bluetoothd[1056]: Starting experimental netlink support
Sep 17 11:01:05 NetbookOfAwesomeness bluetoothd[1056]: Failed to find Bluetooth netlink family
Sep 17 11:01:05 NetbookOfAwesomeness bluetoothd[1056]: Failed to init netlink plugin
Sep 17 11:01:05 NetbookOfAwesomeness bluetoothd[1056]: bridge pan0 created
Sep 17 11:02:53 NetbookOfAwesomeness bluetoothd[1056]: HCI dev 0 registered
Sep 17 11:02:53 NetbookOfAwesomeness bluetoothd[1056]: HCI dev 0 up
Sep 17 11:02:53 NetbookOfAwesomeness bluetoothd[1056]: Starting security manager 0
Sep 17 11:02:58 NetbookOfAwesomeness bluetoothd[1056]: Can't read address for hci0: Connection timed out (110)
Sep 17 11:03:10 NetbookOfAwesomeness bluetoothd[1056]: HCI dev 0 down
Sep 17 11:03:10 NetbookOfAwesomeness bluetoothd[1056]: Adapter /org/bluez/1056/hci0 has been disabled
Sep 17 11:03:10 NetbookOfAwesomeness bluetoothd[1056]: Stopping security manager 0
Sep 17 11:03:11 NetbookOfAwesomeness bluetoothd[1056]: HCI dev 0 unregistered
Sep 17 11:03:11 NetbookOfAwesomeness bluetoothd[1056]: Unregister path: /org/bluez/1056/hci0
Sep 17 11:03:14 NetbookOfAwesomeness bluetoothd[1056]: HCI dev 0 registered
Sep 17 11:03:14 NetbookOfAwesomeness bluetoothd[1056]: HCI dev 0 up
Sep 17 11:03:14 NetbookOfAwesomeness bluetoothd[1056]: Starting security manager 0
Sep 17 11:03:14 NetbookOfAwesomeness bluetoothd[1056]: Adapter /org/bluez/1056/hci0 has been enabled
Sep 17 11:03:19 NetbookOfAwesomeness bluetoothd[1056]: Discovery session 0x20ed3ab8 with :1.77 activated
Sep 17 11:03:38 NetbookOfAwesomeness bluetoothd[1056]: Stopping discovery
Sep 17 11:09:21 NetbookOfAwesomeness bluetoothd[1056]: Discovery session 0x20ed0bf0 with :1.85 activated
Sep 17 11:09:37 NetbookOfAwesomeness bluetoothd[1056]: Stopping discovery
Sep 17 11:13:54 NetbookOfAwesomeness bluetoothd[1056]: Discovery session 0x20ed0a48 with :1.87 activated
Sep 17 11:14:12 NetbookOfAwesomeness bluetoothd[1056]: Stopping discovery
Sep 17 11:25:20 NetbookOfAwesomeness bluetoothd[811]: Bluetooth daemon 4.60
Sep 17 11:25:20 NetbookOfAwesomeness bluetoothd[845]: Starting SDP server
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: Starting experimental netlink support
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: Failed to find Bluetooth netlink family
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: Failed to init netlink plugin
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: bridge pan0 created
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: HCI dev 0 registered
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: HCI dev 0 up
Sep 17 11:25:21 NetbookOfAwesomeness bluetoothd[845]: Starting security manager 0
Sep 17 11:25:22 NetbookOfAwesomeness bluetoothd[845]: Adapter /org/bluez/811/hci0 has been enabled
Sep 17 11:25:22 NetbookOfAwesomeness bluetoothd[1109]: Bluetooth daemon 4.60
Sep 17 11:25:22 NetbookOfAwesomeness bluetoothd[1109]: Unable to get on D-Bus
Sep 17 11:55:16 NetbookOfAwesomeness bluetoothd[1114]: Bluetooth daemon 4.60
Sep 17 11:55:16 NetbookOfAwesomeness bluetoothd[1118]: Starting SDP server
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: Starting experimental netlink support
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: Failed to find Bluetooth netlink family
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: Failed to init netlink plugin
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: bridge pan0 created
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: HCI dev 0 registered
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: HCI dev 0 up
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: Starting security manager 0
Sep 17 11:55:17 NetbookOfAwesomeness bluetoothd[1118]: Adapter /org/bluez/1114/hci0 has been enabled
Sep 17 11:55:20 NetbookOfAwesomeness bluetoothd[1274]: Bluetooth daemon 4.60
Sep 17 11:55:20 NetbookOfAwesomeness bluetoothd[1274]: Unable to get on D-Bus
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: Stopping security manager 0
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: HCI dev 0 down
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: Adapter /org/bluez/1114/hci0 has been disabled
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: HCI dev 0 unregistered
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: Unregister path: /org/bluez/1114/hci0
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: HCI dev 0 registered
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: HCI dev 0 up
Sep 17 12:03:25 NetbookOfAwesomeness bluetoothd[1118]: Starting security manager 0
Sep 17 12:03:30 NetbookOfAwesomeness bluetoothd[1118]: Can't read address for hci0: Connection timed out (110)
Sep 17 12:03:35 NetbookOfAwesomeness bluetoothd[1939]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 12:03:56 NetbookOfAwesomeness bluetoothd[1118]: bridge pan0 removed
Sep 17 12:03:56 NetbookOfAwesomeness bluetoothd[1118]: Stopping SDP server
Sep 17 12:03:56 NetbookOfAwesomeness bluetoothd[1118]: Exit
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[993]: Bluetooth daemon 4.60
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: Starting SDP server
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: Starting experimental netlink support
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: Failed to find Bluetooth netlink family
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: Failed to init netlink plugin
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: bridge pan0 created
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 registered
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 up
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: Starting security manager 0
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[995]: Adapter /org/bluez/993/hci0 has been enabled
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[1129]: Bluetooth daemon 4.60
Sep 17 12:05:47 NetbookOfAwesomeness bluetoothd[1129]: Unable to get on D-Bus
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: Stopping security manager 0
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 down
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: Adapter /org/bluez/993/hci0 has been disabled
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 unregistered
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: Unregister path: /org/bluez/993/hci0
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 registered
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 up
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: Starting security manager 0
Sep 17 12:14:24 NetbookOfAwesomeness bluetoothd[995]: Adapter /org/bluez/993/hci0 has been enabled
Sep 17 12:17:23 NetbookOfAwesomeness bluetoothd[995]: Discovery session 0x22a0ff90 with :1.72 activated
Sep 17 12:17:34 NetbookOfAwesomeness bluetoothd[995]: Stopping discovery
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: Stopping security manager 0
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 down
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: Adapter /org/bluez/993/hci0 has been disabled
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 unregistered
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: Unregister path: /org/bluez/993/hci0
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 registered
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: HCI dev 0 up
Sep 17 12:28:53 NetbookOfAwesomeness bluetoothd[995]: Starting security manager 0
Sep 17 12:28:59 NetbookOfAwesomeness bluetoothd[995]: Can't read address for hci0: Connection timed out (110)
Sep 17 12:29:04 NetbookOfAwesomeness bluetoothd[2278]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 12:29:24 NetbookOfAwesomeness bluetoothd[995]: bridge pan0 removed
Sep 17 12:29:24 NetbookOfAwesomeness bluetoothd[995]: Stopping SDP server
Sep 17 12:29:24 NetbookOfAwesomeness bluetoothd[995]: Exit
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Bluetooth daemon 4.60
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Starting SDP server
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Starting experimental netlink support
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Failed to find Bluetooth netlink family
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Failed to init netlink plugin
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: bridge pan0 created
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 registered
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 up
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Starting security manager 0
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been enabled
Sep 17 12:39:51 NetbookOfAwesomeness bluetoothd[2542]: Inquiry Failed with status 0x12
Sep 17 12:39:57 NetbookOfAwesomeness bluetoothd[2542]: Discovery session 0x219e1fa0 with :1.94 activated
Sep 17 12:40:08 NetbookOfAwesomeness bluetoothd[2542]: Stopping discovery
Sep 17 13:07:49 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 down
Sep 17 13:07:49 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been disabled
Sep 17 13:07:49 NetbookOfAwesomeness bluetoothd[2542]: Stopping security manager 0
Sep 17 13:07:49 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 unregistered
Sep 17 13:07:49 NetbookOfAwesomeness bluetoothd[2542]: Unregister path: /org/bluez/2542/hci0
Sep 17 13:07:52 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 registered
Sep 17 13:07:52 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 up
Sep 17 13:07:52 NetbookOfAwesomeness bluetoothd[2542]: Starting security manager 0
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been enabled
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: Stopping security manager 0
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 down
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been disabled
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 up
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: Starting security manager 0
Sep 17 13:07:53 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been enabled
Sep 17 13:08:00 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 down
Sep 17 13:08:00 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been disabled
Sep 17 13:08:00 NetbookOfAwesomeness bluetoothd[2542]: Stopping security manager 0
Sep 17 13:08:00 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 unregistered
Sep 17 13:08:00 NetbookOfAwesomeness bluetoothd[2542]: Unregister path: /org/bluez/2542/hci0
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 registered
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 up
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: Starting security manager 0
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been enabled
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: Stopping security manager 0
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 down
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been disabled
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: HCI dev 0 up
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: Starting security manager 0
Sep 17 13:17:10 NetbookOfAwesomeness bluetoothd[2542]: Adapter /org/bluez/2542/hci0 has been enabled
Sep 17 13:18:11 NetbookOfAwesomeness bluetoothd[2542]: Discovery session 0x219e18e0 with :1.117 activated
Sep 17 13:18:26 NetbookOfAwesomeness bluetoothd[2542]: Stopping discovery
Sep 17 13:19:24 NetbookOfAwesomeness bluetoothd[2542]: Discovery session 0x219e34e8 with :1.118 activated
Sep 17 13:19:39 NetbookOfAwesomeness bluetoothd[2542]: Stopping discovery
Sep 17 13:19:40 NetbookOfAwesomeness bluetoothd[2542]: Discovery session 0x219e34e8 with :1.118 activated
Sep 17 13:19:50 NetbookOfAwesomeness bluetoothd[2542]: Stopping discovery
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[911]: Bluetooth daemon 4.60
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: Starting SDP server
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: Starting experimental netlink support
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: Failed to find Bluetooth netlink family
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: Failed to init netlink plugin
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: bridge pan0 created
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 registered
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 up
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: Starting security manager 0
Sep 17 13:44:22 NetbookOfAwesomeness bluetoothd[921]: Adapter /org/bluez/911/hci0 has been enabled
Sep 17 13:44:23 NetbookOfAwesomeness bluetoothd[1128]: Bluetooth daemon 4.60
Sep 17 13:44:23 NetbookOfAwesomeness bluetoothd[1128]: Unable to get on D-Bus
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: Stopping security manager 0
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 down
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: Adapter /org/bluez/911/hci0 has been disabled
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 unregistered
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: Unregister path: /org/bluez/911/hci0
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 registered
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 up
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: Starting security manager 0
Sep 17 14:15:00 NetbookOfAwesomeness bluetoothd[921]: Adapter /org/bluez/911/hci0 has been enabled
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: Stopping security manager 0
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 down
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: Adapter /org/bluez/911/hci0 has been disabled
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 unregistered
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: Unregister path: /org/bluez/911/hci0
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 registered
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: HCI dev 0 up
Sep 17 14:42:07 NetbookOfAwesomeness bluetoothd[921]: Starting security manager 0
Sep 17 14:42:12 NetbookOfAwesomeness bluetoothd[921]: Can't read address for hci0: Connection timed out (110)
Sep 17 14:42:17 NetbookOfAwesomeness bluetoothd[2869]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 14:42:37 NetbookOfAwesomeness bluetoothd[921]: Can't remove GN bridge
Sep 17 14:42:37 NetbookOfAwesomeness bluetoothd[921]: Stopping SDP server
Sep 17 14:42:37 NetbookOfAwesomeness bluetoothd[921]: Exit
Sep 17 14:51:42 NetbookOfAwesomeness bluetoothd[4758]: Bluetooth daemon 4.60
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Starting SDP server
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Starting experimental netlink support
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Failed to find Bluetooth netlink family
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Failed to init netlink plugin
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Can't create GN bridge
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: HCI dev 0 registered
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: HCI dev 0 up
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Starting security manager 0
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Adapter /org/bluez/4758/hci0 has been enabled
Sep 17 14:51:43 NetbookOfAwesomeness bluetoothd[4758]: Inquiry Failed with status 0x12
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: Stopping security manager 0
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: HCI dev 0 down
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: Adapter /org/bluez/4758/hci0 has been disabled
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: HCI dev 0 unregistered
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: Unregister path: /org/bluez/4758/hci0
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: HCI dev 0 registered
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: HCI dev 0 up
Sep 17 15:00:32 NetbookOfAwesomeness bluetoothd[4758]: Starting security manager 0
Sep 17 15:00:37 NetbookOfAwesomeness bluetoothd[4758]: Can't read address for hci0: Connection timed out (110)
Sep 17 15:00:42 NetbookOfAwesomeness bluetoothd[6106]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[925]: Bluetooth daemon 4.60
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: Starting SDP server
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: Starting experimental netlink support
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: Failed to find Bluetooth netlink family
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: Failed to init netlink plugin
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: bridge pan0 created
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: HCI dev 0 registered
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: HCI dev 0 up
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: Starting security manager 0
Sep 17 15:01:28 NetbookOfAwesomeness bluetoothd[932]: Adapter /org/bluez/925/hci0 has been enabled
Sep 17 15:01:30 NetbookOfAwesomeness bluetoothd[1125]: Bluetooth daemon 4.60
Sep 17 15:01:30 NetbookOfAwesomeness bluetoothd[1125]: Unable to get on D-Bus
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1027]: Bluetooth daemon 4.60
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: Starting SDP server
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: Starting experimental netlink support
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: Failed to find Bluetooth netlink family
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: Failed to init netlink plugin
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: bridge pan0 created
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: HCI dev 0 registered
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: HCI dev 0 up
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: Starting security manager 0
Sep 17 16:24:41 NetbookOfAwesomeness bluetoothd[1030]: Adapter /org/bluez/1027/hci0 has been enabled
Sep 17 16:24:42 NetbookOfAwesomeness bluetoothd[1179]: Bluetooth daemon 4.60
Sep 17 16:24:42 NetbookOfAwesomeness bluetoothd[1179]: Unable to get on D-Bus
Sep 17 16:25:36 NetbookOfAwesomeness bluetoothd[1030]: Discovery session 0x21a1b5c8 with :1.56 activated
Sep 17 16:25:46 NetbookOfAwesomeness bluetoothd[1030]: Stopping discovery
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[946]: Bluetooth daemon 4.60
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: Starting SDP server
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: Starting experimental netlink support
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: Failed to find Bluetooth netlink family
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: Failed to init netlink plugin
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: bridge pan0 created
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: HCI dev 0 registered
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: HCI dev 0 up
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: Starting security manager 0
Sep 17 17:19:32 NetbookOfAwesomeness bluetoothd[951]: Adapter /org/bluez/946/hci0 has been enabled
Sep 17 17:19:33 NetbookOfAwesomeness bluetoothd[1137]: Bluetooth daemon 4.60
Sep 17 17:19:33 NetbookOfAwesomeness bluetoothd[1137]: Unable to get on D-Bus
Sep 17 17:23:01 NetbookOfAwesomeness bluetoothd[951]: HCI dev 0 down
Sep 17 17:23:01 NetbookOfAwesomeness bluetoothd[951]: Adapter /org/bluez/946/hci0 has been disabled
Sep 17 17:23:01 NetbookOfAwesomeness bluetoothd[951]: Stopping security manager 0
Sep 17 17:23:02 NetbookOfAwesomeness bluetoothd[951]: HCI dev 0 unregistered
Sep 17 17:23:02 NetbookOfAwesomeness bluetoothd[951]: Unregister path: /org/bluez/946/hci0
Sep 17 17:23:33 NetbookOfAwesomeness bluetoothd[951]: Can't remove GN bridge
Sep 17 17:23:33 NetbookOfAwesomeness bluetoothd[951]: Stopping SDP server
Sep 17 17:23:33 NetbookOfAwesomeness bluetoothd[951]: Exit
Sep 17 17:23:55 NetbookOfAwesomeness bluetoothd[1925]: Bluetooth daemon 4.60
Sep 17 17:23:55 NetbookOfAwesomeness bluetoothd[1925]: Starting SDP server
Sep 17 17:23:55 NetbookOfAwesomeness bluetoothd[1925]: Starting experimental netlink support
Sep 17 17:23:55 NetbookOfAwesomeness bluetoothd[1925]: Failed to find Bluetooth netlink family
Sep 17 17:23:55 NetbookOfAwesomeness bluetoothd[1925]: Failed to init netlink plugin
Sep 17 17:23:55 NetbookOfAwesomeness bluetoothd[1925]: Can't create GN bridge
Sep 17 17:24:12 NetbookOfAwesomeness bluetoothd[1925]: Can't remove GN bridge
Sep 17 17:24:12 NetbookOfAwesomeness bluetoothd[1925]: Stopping SDP server
Sep 17 17:24:12 NetbookOfAwesomeness bluetoothd[1925]: Exit
Sep 17 17:24:20 NetbookOfAwesomeness bluetoothd[1939]: Bluetooth daemon 4.60
Sep 17 17:24:20 NetbookOfAwesomeness bluetoothd[1939]: Starting SDP server
Sep 17 17:24:20 NetbookOfAwesomeness bluetoothd[1939]: Starting experimental netlink support
Sep 17 17:24:20 NetbookOfAwesomeness bluetoothd[1939]: Failed to find Bluetooth netlink family
Sep 17 17:24:20 NetbookOfAwesomeness bluetoothd[1939]: Failed to init netlink plugin
Sep 17 17:24:20 NetbookOfAwesomeness bluetoothd[1939]: Can't create GN bridge
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: HCI dev 0 registered
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: HCI dev 0 up
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: Starting security manager 0
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: Adapter /org/bluez/1939/hci0 has been enabled
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: Stopping security manager 0
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: HCI dev 0 down
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: Adapter /org/bluez/1939/hci0 has been disabled
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: HCI dev 0 up
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: Starting security manager 0
Sep 17 17:24:30 NetbookOfAwesomeness bluetoothd[1939]: Adapter /org/bluez/1939/hci0 has been enabled
Sep 17 17:49:27 NetbookOfAwesomeness bluetoothd[1939]: Can't remove GN bridge
Sep 17 17:49:27 NetbookOfAwesomeness bluetoothd[1939]: Stopping SDP server
Sep 17 17:49:27 NetbookOfAwesomeness bluetoothd[1939]: Exit
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2654]: Bluetooth daemon 4.60
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Starting SDP server
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Starting experimental netlink support
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Failed to find Bluetooth netlink family
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Failed to init netlink plugin
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Can't create GN bridge
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: HCI dev 0 registered
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: HCI dev 0 up
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Starting security manager 0
Sep 17 17:49:31 NetbookOfAwesomeness bluetoothd[2655]: Adapter /org/bluez/2654/hci0 has been enabled
Sep 17 17:49:34 NetbookOfAwesomeness bluetoothd[2655]: Can't remove GN bridge
Sep 17 17:49:34 NetbookOfAwesomeness bluetoothd[2655]: Stopping SDP server
Sep 17 17:49:34 NetbookOfAwesomeness bluetoothd[2655]: Exit
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2665]: Bluetooth daemon 4.60
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Starting SDP server
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Starting experimental netlink support
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Failed to find Bluetooth netlink family
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Failed to init netlink plugin
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Can't create GN bridge
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 registered
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 up
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Starting security manager 0
Sep 17 17:49:35 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been enabled
Sep 17 17:49:36 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 down
Sep 17 17:49:36 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been disabled
Sep 17 17:49:36 NetbookOfAwesomeness bluetoothd[2666]: Stopping security manager 0
Sep 17 17:49:36 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 unregistered
Sep 17 17:49:36 NetbookOfAwesomeness bluetoothd[2666]: Unregister path: /org/bluez/2665/hci0
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 registered
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 up
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Starting security manager 0
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been enabled
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Stopping security manager 0
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 down
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been disabled
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 up
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Starting security manager 0
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been enabled
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 down
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been disabled
Sep 17 17:49:37 NetbookOfAwesomeness bluetoothd[2666]: Stopping security manager 0
Sep 17 17:49:38 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 unregistered
Sep 17 17:49:38 NetbookOfAwesomeness bluetoothd[2666]: Unregister path: /org/bluez/2665/hci0
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 registered
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 up
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Starting security manager 0
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been enabled
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Stopping security manager 0
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 down
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been disabled
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 up
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Starting security manager 0
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been enabled
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 down
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Adapter /org/bluez/2665/hci0 has been disabled
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Stopping security manager 0
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: HCI dev 0 unregistered
Sep 17 17:49:39 NetbookOfAwesomeness bluetoothd[2666]: Unregister path: /org/bluez/2665/hci0
Sep 17 17:49:40 NetbookOfAwesomeness bluetoothd[2666]: Can't remove GN bridge
Sep 17 17:49:40 NetbookOfAwesomeness bluetoothd[2666]: Stopping SDP server
Sep 17 17:49:40 NetbookOfAwesomeness bluetoothd[2666]: Exit
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2695]: Bluetooth daemon 4.60
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Starting SDP server
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Starting experimental netlink support
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Failed to find Bluetooth netlink family
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Failed to init netlink plugin
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Can't create GN bridge
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: HCI dev 0 registered
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: HCI dev 0 up
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Starting security manager 0
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Adapter /org/bluez/2695/hci0 has been enabled
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Stopping security manager 0
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: HCI dev 0 down
Sep 17 17:50:05 NetbookOfAwesomeness bluetoothd[2696]: Adapter /org/bluez/2695/hci0 has been disabled
Sep 17 17:50:06 NetbookOfAwesomeness bluetoothd[2696]: HCI dev 0 up
Sep 17 17:50:06 NetbookOfAwesomeness bluetoothd[2696]: Starting security manager 0
Sep 17 17:50:06 NetbookOfAwesomeness bluetoothd[2696]: Adapter /org/bluez/2695/hci0 has been enabled
Sep 17 17:50:10 NetbookOfAwesomeness bluetoothd[2696]: Can't remove GN bridge
Sep 17 17:50:10 NetbookOfAwesomeness bluetoothd[2696]: Stopping SDP server
Sep 17 17:50:10 NetbookOfAwesomeness bluetoothd[2696]: Exit
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2705]: Bluetooth daemon 4.60
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Starting SDP server
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Starting experimental netlink support
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Failed to find Bluetooth netlink family
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Failed to init netlink plugin
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Can't create GN bridge
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: HCI dev 0 registered
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: HCI dev 0 up
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Starting security manager 0
Sep 17 17:50:19 NetbookOfAwesomeness bluetoothd[2706]: Adapter /org/bluez/2705/hci0 has been enabled
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: Stopping security manager 0
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: HCI dev 0 down
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: Adapter /org/bluez/2705/hci0 has been disabled
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: HCI dev 0 unregistered
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: Unregister path: /org/bluez/2705/hci0
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: HCI dev 0 registered
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: HCI dev 0 up
Sep 17 18:08:11 NetbookOfAwesomeness bluetoothd[2706]: Starting security manager 0
Sep 17 18:08:16 NetbookOfAwesomeness bluetoothd[2706]: Can't read address for hci0: Connection timed out (110)
Sep 17 18:08:21 NetbookOfAwesomeness bluetoothd[3121]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 18:08:42 NetbookOfAwesomeness bluetoothd[2706]: Can't remove GN bridge
Sep 17 18:08:42 NetbookOfAwesomeness bluetoothd[2706]: Stopping SDP server
Sep 17 18:08:42 NetbookOfAwesomeness bluetoothd[2706]: Exit
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Bluetooth daemon 4.60
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Starting SDP server
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Starting experimental netlink support
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Failed to find Bluetooth netlink family
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Failed to init netlink plugin
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Can't create GN bridge
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: HCI dev 0 registered
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: HCI dev 0 up
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Starting security manager 0
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Adapter /org/bluez/3494/hci0 has been enabled
Sep 17 18:11:42 NetbookOfAwesomeness bluetoothd[3494]: Inquiry Failed with status 0x12
Sep 17 18:20:39 NetbookOfAwesomeness bluetoothd[3494]: Discovery session 0x214b34c0 with :1.112 activated
Sep 17 18:20:49 NetbookOfAwesomeness bluetoothd[3494]: Stopping discovery
Sep 17 18:36:45 NetbookOfAwesomeness bluetoothd[3902]: Bluetooth daemon 4.60
Sep 17 18:36:45 NetbookOfAwesomeness bluetoothd[3902]: Unable to get on D-Bus
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: Stopping security manager 0
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: HCI dev 0 down
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: Adapter /org/bluez/3494/hci0 has been disabled
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: HCI dev 0 unregistered
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: Unregister path: /org/bluez/3494/hci0
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: HCI dev 0 registered
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: HCI dev 0 up
Sep 17 19:10:05 NetbookOfAwesomeness bluetoothd[3494]: Starting security manager 0
Sep 17 19:10:10 NetbookOfAwesomeness bluetoothd[3494]: Can't read address for hci0: Connection timed out (110)
Sep 17 19:10:15 NetbookOfAwesomeness bluetoothd[4481]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[3494]: Can't remove GN bridge
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[3494]: Stopping SDP server
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[3494]: Exit
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4747]: Bluetooth daemon 4.60
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: Starting SDP server
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: Starting experimental netlink support
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: Failed to find Bluetooth netlink family
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: Failed to init netlink plugin
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: Can't create GN bridge
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: HCI dev 0 registered
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: HCI dev 0 up
Sep 17 19:10:59 NetbookOfAwesomeness bluetoothd[4748]: Starting security manager 0
Sep 17 19:11:00 NetbookOfAwesomeness bluetoothd[4748]: Adapter /org/bluez/4747/hci0 has been enabled
Sep 17 19:11:00 NetbookOfAwesomeness bluetoothd[4748]: Inquiry Failed with status 0x12
Sep 17 19:11:11 NetbookOfAwesomeness bluetoothd[4748]: Discovery session 0x2286d040 with :1.148 activated
Sep 17 19:11:21 NetbookOfAwesomeness bluetoothd[4748]: Stopping discovery
Sep 17 19:11:26 NetbookOfAwesomeness bluetoothd[4748]: Discovery session 0x2286d040 with :1.148 activated
Sep 17 19:11:37 NetbookOfAwesomeness bluetoothd[4748]: Stopping discovery
Sep 17 19:21:10 NetbookOfAwesomeness bluetoothd[4748]: Discovery session 0x22873f28 with :1.158 activated
Sep 17 19:21:25 NetbookOfAwesomeness bluetoothd[4748]: Stopping discovery
Sep 17 19:21:31 NetbookOfAwesomeness bluetoothd[4748]: Discovery session 0x22873f28 with :1.158 activated
Sep 17 19:21:41 NetbookOfAwesomeness bluetoothd[4748]: Stopping discovery
Sep 17 19:21:53 NetbookOfAwesomeness bluetoothd[4748]: link_key_request (sba=74:F0:6D:A0:4F:41, dba=60:FB:42:76:00:25)
Sep 17 19:21:53 NetbookOfAwesomeness bluetoothd[4748]: io_capa_request (sba=74:F0:6D:A0:4F:41, dba=60:FB:42:76:00:25)
Sep 17 19:21:54 NetbookOfAwesomeness bluetoothd[4748]: io_capa_response (sba=74:F0:6D:A0:4F:41, dba=60:FB:42:76:00:25)
Sep 17 19:22:22 NetbookOfAwesomeness bluetoothd[4748]: /org/bluez/4747/hci0/dev_60_FB_42_76_00_25: error updating services: Permission denied (13)
Sep 17 19:23:29 NetbookOfAwesomeness bluetoothd[4748]: Can't remove GN bridge
Sep 17 19:23:29 NetbookOfAwesomeness bluetoothd[4748]: Stopping SDP server
Sep 17 19:23:29 NetbookOfAwesomeness bluetoothd[4748]: Exit
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[888]: Bluetooth daemon 4.60
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: Starting SDP server
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: Starting experimental netlink support
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: Failed to find Bluetooth netlink family
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: Failed to init netlink plugin
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: bridge pan0 created
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: HCI dev 0 registered
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: HCI dev 0 up
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: Starting security manager 0
Sep 17 19:24:49 NetbookOfAwesomeness bluetoothd[897]: Adapter /org/bluez/888/hci0 has been enabled
Sep 17 19:24:50 NetbookOfAwesomeness bluetoothd[1098]: Bluetooth daemon 4.60
Sep 17 19:24:50 NetbookOfAwesomeness bluetoothd[1098]: Unable to get on D-Bus
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: Stopping security manager 0
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: HCI dev 0 down
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: Adapter /org/bluez/888/hci0 has been disabled
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: HCI dev 0 unregistered
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: Unregister path: /org/bluez/888/hci0
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: HCI dev 0 registered
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: HCI dev 0 up
Sep 17 20:03:22 NetbookOfAwesomeness bluetoothd[897]: Starting security manager 0
Sep 17 20:03:27 NetbookOfAwesomeness bluetoothd[897]: Can't read address for hci0: Connection timed out (110)
Sep 17 20:03:32 NetbookOfAwesomeness bluetoothd[2186]: Can't set link policy on hci0: Connection timed out (110)
Sep 17 20:03:53 NetbookOfAwesomeness bluetoothd[897]: Can't remove GN bridge
Sep 17 20:03:53 NetbookOfAwesomeness bluetoothd[897]: Stopping SDP server
Sep 17 20:03:53 NetbookOfAwesomeness bluetoothd[897]: Exit
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Bluetooth daemon 4.60
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Starting SDP server
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Starting experimental netlink support
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Failed to find Bluetooth netlink family
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Failed to init netlink plugin
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Can't create GN bridge
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: HCI dev 0 registered
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: HCI dev 0 up
Sep 17 20:53:35 NetbookOfAwesomeness bluetoothd[3215]: Starting security manager 0
Sep 17 20:53:36 NetbookOfAwesomeness bluetoothd[3215]: Adapter /org/bluez/3215/hci0 has been enabled
Sep 17 20:53:36 NetbookOfAwesomeness bluetoothd[3215]: Inquiry Failed with status 0x12
Sep 17 20:53:42 NetbookOfAwesomeness bluetoothd[3215]: Discovery session 0x2242d9d0 with :1.94 activated
Sep 17 20:53:53 NetbookOfAwesomeness bluetoothd[3215]: Stopping discovery
Sep 17 20:54:40 NetbookOfAwesomeness bluetoothd[3215]: Discovery session 0x2242d640 with :1.96 activated
Sep 17 20:54:55 NetbookOfAwesomeness bluetoothd[3215]: Stopping discovery
Sep 17 20:54:58 NetbookOfAwesomeness bluetoothd[3215]: Discovery session 0x2242d640 with :1.96 activated
Sep 17 20:55:08 NetbookOfAwesomeness bluetoothd[3215]: Stopping discovery
```

---

