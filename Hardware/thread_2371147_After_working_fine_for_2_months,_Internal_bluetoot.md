---
title: "After working fine for 2 months, Internal bluetooth adapter stopped working"
date: 2017-09-11
forum: Hardware
---

### Post by adynaton on 2017-09-11
I was watching a video on a break, and I was having some weird issues with the syncing of the sound with my headphones. Restarted and went for coffee.
Came back to see that the bluetooth icon had disappeared from the top bar.
Open settings and it looks as if there is no bluetooth capability on this computer.
Additionally, the startup time became much longer, used to be about 10 seconds, now its more like 40 seconds.

Edit: Aspire-E5-575G

~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:57f2 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 008: ID 046d:c248 Logitech, Inc. G105 Gaming Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~$ hcitool scan
Device is not available: No such device

~$ lspci -knn | grep Net -A2
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Lite-On Communications Inc Device [11ad:08a6]
    Kernel driver in use: ath10k_pci

~$ blueman-applet
blueman-applet version 2.0.4 starting
Stale PID, overwriting
_________
Load (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:60)
['StandardItems', 'RecentConns', 'DhcpClient', 'DiscvManager', 'Menu', 'KillSwitch', 'NMPANSupport', 'AppIndicator', 'PPPSupport', 'AuthAgent', 'DBusService', 'PowerManager', 'NetUsage', 'GameControllerWakelock', 'NMDUNSupport', 'Headset', 'ExitItem', 'StatusIcon', 'SerialManager', 'TransferService', 'ShowConnected', 'Networking'] 
/usr/lib/python3/dist-packages/blueman/plugins/applet/AppIndicator.py:8: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as girAppIndicator
_________
update_menuitems (/usr/lib/python3/dist-packages/blueman/plugins/applet/DiscvManager.py:123)
warning: Adapter is None 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
Not loading PPPSupport because it's conflict has higher priority 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
Not loading DhcpClient because it's conflict has higher priority 
_________
update_menuitems (/usr/lib/python3/dist-packages/blueman/plugins/applet/DiscvManager.py:123)
warning: Adapter is None 
_________
on_registered (/usr/lib/python3/dist-packages/blueman/bluez/obex/AgentManager.py:18)
/org/blueman/obex_agent 
ERROR:dbus.proxies:Introspect error on org.bluez:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ERROR:dbus.proxies:Introspect error on org.bluez:/org/bluez: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ERROR:dbus.proxies:Introspect error on org.bluez:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out

---

### Post by jeremy31 on 2017-09-12
I suspect the bluetooth chip might be broken, the weird issues with sound may have been the first sign of it going bad, we can check the logs
```
dmesg | egrep -i 'blue|firm|0cf3'
```

---

