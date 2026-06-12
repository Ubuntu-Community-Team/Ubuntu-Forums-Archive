---
title: "Eee 1015 hardware oddities"
date: 2010-09-17
forum: Hardware
---

### Post by ThatBum on 2010-09-17
Hello. I removed Windows 7 Starter put Ubuntu on my ASUS Eee 1015PE netbook a while ago. It runs fine and is very power efficient, and much better than 7 in actually doing things. However, I seem to have a couple of odd hardware problems with it. 
  
1. Brightness. I found through     combing the forum, that I could enable the Function keys (the useful     ones anyway) by putting &#8220;acpi_osi=Linux&#8221; in my kernel parameters     in Grub. This, though, seems to make Ubuntu unaware of the     brightness keys. The little notify-osd thing that comes up when I     change the brightness isn't there anymore. It has 11 states of     brightness, when before it went in about 5.

I also learned that putting     &#8220;acpi_backlight=vendor&#8221; will bring the control of the brightness     from the BIOS (I think) to Linux. This kind of works, but it's very     buggy. The notify-osd thing comes up, but the bar won't go up all     the way. It seems to think it goes in the fewer amount of steps, but     it still going in the BIOS-controlled ones, so it gets out of sync.

Also, possibly unrelated, the     brightness applet for gnome-panel, if I right click it to bring down     the slider and then try to move the slider, it just disappears. It     will only work if I left click it to bring down the menu, and then     click the slider behind it. This happens with acpi_backlight on or     off. 

2. Bluetooth, the main problem     seeming to be that bluetoothd is randomly terminating. I used     gnome-bluetooth for awhile, the default indicator applet thing, but     that gave me too much guff, so I got blueman, which seems to be more     flexible. I noticed that it worked just after I installed it, but if     I rebooted it, the applet was nowhere to be seen in the panel. After     some digging, I found it needed the 'bluez daemon' to start, which     is just bluetoothd. The rc0.d script K74bluetooth didn't seem to be     working, so I put /usr/sbin/bluetoothd in the sudoers, put 'sudo     bluetoothd' in rc.local, and rebooted. THAT worked, but after a while, bluetoothd went down again (because the blueman applet disappeared), and I have to run 'sudo bluetoothd' again to start it. The time it takes for it     to go down is totally random; it could be minutes, it could be hours. Also, 'sudo service bluetooth     start/stop' and 'sudo /etc/init.d/bluetooth stop/start' both work it     controlling the daemon. I would post some logs if I could, but     bluetoothd doesn't give any output. 

The reason I discovered it was     bluetoothd, is that gnome-bluetooth was having spotty control over     the bluetooth adapter. It seems when you turn off bluetooth in     gnome-bluetooth, it actually kills the daemon, but in blueman, this     is not so, and, in fact, it is required to be running for the applet     to work. So when I rebooted after getting blueman and tried to run     the manager, it said it needed bluez to be running, which, again, is     bluetoothd. 

The contents of K74 bluetooth:

```
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

EDIT: Whoops, I posted this thread twice, didn't I? Blasted public WiFi. Someone come and delete this one please.

---

