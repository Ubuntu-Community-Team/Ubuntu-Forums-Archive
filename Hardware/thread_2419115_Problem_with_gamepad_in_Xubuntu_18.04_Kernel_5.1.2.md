---
title: "Problem with gamepad in Xubuntu 18.04 Kernel 5.1.2"
date: 2019-05-16
forum: Hardware
---

### Post by extrads on 2019-05-16
Hello, i can use my PS3 Gamepad in my Xubuntu 18.04.2
The kernel is upgrade with Ukku, i installed the last version 5.1.2

This is the log of blueman-applet

----
blueman-applet version 2.0.5 starting
Stale PID, overwriting
_________
Load (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:60)
['GameControllerWakelock', 'DhcpClient', 'SerialManager', 'StatusIcon', 'StandardItems', 'NMDUNSupport', 'NetUsage', 'DiscvManager', 'NMPANSupport', 'ShowConnected', 'TransferService', 'Headset', 'ExitItem', 'Menu', 'PPPSupport', 'AppIndicator', 'RecentConns', 'PowerManager', 'KillSwitch', 'AuthAgent', 'DBusService', 'Networking'] 
/usr/lib/python3/dist-packages/blueman/plugins/applet/AppIndicator.py:8: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as girAppIndicator
_________
get_interface_version (/usr/lib/python3/dist-packages/blueman/bluez/BlueZInterface.py:13)
Detected BlueZ 5 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.GameControllerWakelock.GameControllerWakelock'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.SerialManager.SerialManager'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.StatusIcon.StatusIcon'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.Menu.Menu'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.StandardItems.StandardItems'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.DBusService.DBusService'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.NMDUNSupport.NMDUNSupport'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.DiscvManager.DiscvManager'> 
_________
update_menuitems (/usr/lib/python3/dist-packages/blueman/plugins/applet/DiscvManager.py:123)
warning: Adapter is None 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.NMPANSupport.NMPANSupport'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.ShowConnected.ShowConnected'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.TransferService.TransferService'> 
_________
get_interface_version (/usr/lib/python3/dist-packages/blueman/bluez/obex/Base.py:20)
Detected BlueZ integrated obexd 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.Headset.Headset'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.ExitItem.ExitItem'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.AppIndicator.AppIndicator'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.RecentConns.RecentConns'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.PowerManager.PowerManager'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.KillSwitch.KillSwitch'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.AuthAgent.AuthAgent'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.Networking.Networking'> 
_________
load_nap_settings (/usr/lib/python3/dist-packages/blueman/plugins/applet/Networking.py:36)
Loading NAP settings 
_________
io_event (/usr/lib/python3/dist-packages/blueman/plugins/applet/KillSwitch.py:71)
killswitch registered 1 
_________
io_event (/usr/lib/python3/dist-packages/blueman/plugins/applet/KillSwitch.py:71)
State: True 
_________
UpdatePowerState (/usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py:159)
off False 
foff False 
on True 
current state True 
new state True 
_________
_on_obex_owner_changed (/usr/lib/python3/dist-packages/blueman/plugins/applet/TransferService.py:172)
obex owner changed: :1.66 
_________
on_dbus_name_owner_change (/usr/bin/blueman-applet:95)
org.bluez owner changed to :1.101 
_________
__init__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:26)
caching initial properties 
_________
initialize (/usr/lib/python3/dist-packages/blueman/plugins/applet/RecentConns.py:144)
rebuilding menu 
_________
register_agent (/usr/lib/python3/dist-packages/blueman/plugins/applet/AuthAgent.py:63)
Registering agent 
_________
set_nap (/usr/lib/python3/dist-packages/blueman/plugins/applet/Networking.py:65)
set nap False 
_________
enumerate_connections (/usr/lib/python3/dist-packages/blueman/plugins/applet/ShowConnected.py:53)
Found 0 existing connections 
_________
on_registered (/usr/lib/python3/dist-packages/blueman/bluez/obex/AgentManager.py:18)
/org/blueman/obex_agent 

(blueman-applet:14879): Gdk-CRITICAL **: 23:16:49.575: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed
_________
RequestPowerState (/usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py:131)
Requesting True 
_________
on_power_state_change_requested (/usr/lib/python3/dist-packages/blueman/plugins/applet/KillSwitch.py:118)
True 
_________
UpdatePowerState (/usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py:159)
off False 
foff False 
on True 
current state True 
new state True 
_________
check (/usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py:119)
callbacks done 
_________
set_adapter_state (/usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py:90)
True 
_________
__init__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:26)
caching initial properties 
_________
__del__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:72)
deleting device /org/bluez/hci0/dev_[MAC HIDDEN]
_________
Destroy (/usr/lib/python3/dist-packages/blueman/main/Device.py:94)
invalidating device /org/bluez/hci0/dev_[MAC HIDDEN]
_________
__init__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:26)
caching initial properties 
_________
__del__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:72)
deleting device /org/bluez/hci0/dev_[MAC HIDDEN]
_________
Destroy (/usr/lib/python3/dist-packages/blueman/main/Device.py:94)
invalidating device /org/bluez/hci0/dev_[MAC HIDDEN]
_________
__init__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:26)
caching initial properties 
_________
__del__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:72)
deleting device /org/bluez/hci0/dev_[MAC HIDDEN]
_________
Destroy (/usr/lib/python3/dist-packages/blueman/main/Device.py:94)
invalidating device /org/bluez/hci0/dev_[MAC HIDDEN]
----

The problem is in the "invalidating device"
The PS3 gamepad is connected to the computer (the indicator appears with a padlock) but after a few minutes it disconnects itself (the led of the control flashes all the lights when in reality only the number 1 should be illuminated). 

Bluez (5.50) and Blueman (2.05)

Which solution is recommended?

---

