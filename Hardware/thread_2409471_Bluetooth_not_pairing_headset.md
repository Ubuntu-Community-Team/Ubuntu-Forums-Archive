---
title: "Bluetooth not pairing headset"
date: 2019-01-02
forum: Hardware
---

### Post by gabo.cr on 2019-01-02
Hi,

I am trying to pair my Bluetooth headset, but I can only see the device for a second and then it disappears, so I cannot click on it to pair it.
I was able to pair a few times before, but this time it just won't connect. 
The headphones are Sony MDR-ZX220BT and I have a Dell Inspiron 5521 with Ubuntu 18.04.
I have Kernel 4.15.0-43-generic.
The wireless controller is Intel Corporation Wireless 3160 (rev 83) with Bluetooth included.

Here is what I get from the following command:

```
:~$ blueman-applet --loglevel debug
blueman-applet version 2.0.5 starting
Stale PID, overwriting
_________
Load (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:60)
['KillSwitch', 'PPPSupport', 'NMDUNSupport', 'DBusService', 'SerialManager', 'StandardItems', 'PowerManager', 'ExitItem', 'NetUsage', 'AppIndicator', 'StatusIcon', 'RecentConns', 'TransferService', 'Menu', 'DiscvManager', 'Headset', 'GameControllerWakelock', 'ShowConnected', 'DhcpClient', 'Networking', 'AuthAgent', 'NMPANSupport'] 
_________
get_interface_version (/usr/lib/python3/dist-packages/blueman/bluez/BlueZInterface.py:13)
Detected BlueZ 5 
/usr/lib/python3/dist-packages/blueman/plugins/applet/AppIndicator.py:8: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as girAppIndicator
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.StatusIcon.StatusIcon'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.Menu.Menu'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.PowerManager.PowerManager'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.KillSwitch.KillSwitch'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.DBusService.DBusService'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
Not loading PPPSupport because it's conflict has higher priority 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.NMDUNSupport.NMDUNSupport'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.SerialManager.SerialManager'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.StandardItems.StandardItems'> 
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
loading <class 'blueman.plugins.applet.TransferService.TransferService'> 
_________
get_interface_version (/usr/lib/python3/dist-packages/blueman/bluez/obex/Base.py:20)
Detected BlueZ integrated obexd 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.DiscvManager.DiscvManager'> 
_________
update_menuitems (/usr/lib/python3/dist-packages/blueman/plugins/applet/DiscvManager.py:123)
warning: Adapter is None 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.Headset.Headset'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.GameControllerWakelock.GameControllerWakelock'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.ShowConnected.ShowConnected'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.Networking.Networking'> 
_________
load_nap_settings (/usr/lib/python3/dist-packages/blueman/plugins/applet/Networking.py:36)
Loading NAP settings 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.AuthAgent.AuthAgent'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.applet.NMPANSupport.NMPANSupport'> 
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
obex owner changed: :1.65 
_________
on_dbus_name_owner_change (/usr/bin/blueman-applet:95)
org.bluez owner changed to :1.3 
_________
__del__ (/usr/lib/python3/dist-packages/blueman/main/Device.py:72)
deleting device None 
_________
Destroy (/usr/lib/python3/dist-packages/blueman/main/Device.py:94)
invalidating device None 
Exception ignored in: <bound method Device.__del__ of <Device.Device object at 0x7f0c9413c3f0 (blueman+main+Device+Device at 0x2940460)>>
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/blueman/main/Device.py", line 74, in __del__
    self.Destroy()
  File "/usr/lib/python3/dist-packages/blueman/main/Device.py", line 98, in Destroy
    self.Signals.DisconnectAll()
  File "/usr/lib/python3/dist-packages/blueman/main/Device.py", line 116, in __getattr__
    return getattr(self.Device, name)
AttributeError: 'NoneType' object has no attribute 'Signals'
_________
initialize (/usr/lib/python3/dist-packages/blueman/plugins/applet/RecentConns.py:144)
rebuilding menu 
_________
set_nap (/usr/lib/python3/dist-packages/blueman/plugins/applet/Networking.py:65)
set nap False 
_________
register_agent (/usr/lib/python3/dist-packages/blueman/plugins/applet/AuthAgent.py:63)
Registering agent 
_________
enumerate_connections (/usr/lib/python3/dist-packages/blueman/plugins/applet/ShowConnected.py:53)
Found 0 existing connections 
_________
on_registered (/usr/lib/python3/dist-packages/blueman/bluez/obex/AgentManager.py:18)
/org/blueman/obex_agent 
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

```

Thank you for your help !

---

### Post by jeremy31 on 2019-01-02
Try with bluetoothctl in terminal
```
bluetoothctl
power on
scan on
```
Hopefully then it will show your headphones, replace MAC in the following commands with the MAC address shown by bluetoothctl
```
pair MAC
trust MAC
connect MAC
```

---

### Post by gabo.cr on 2019-01-04
Wow, that was pretty cool. 
Thank you so much !
:popcorn:

---

### Post by gabo.cr on 2019-01-09
Hi, I'm back again, Bluetooth stopped working again. So tried to pair it again.
Now I get the following: 

```
[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.InProgress
Failed to start discovery: org.freedesktop.DBus.Error.NoReply

```

Not sure what to do now.

---

### Post by gabo.cr on 2019-01-10
My audio jack broke in my laptop, that's why I had to buy this Bluetooth headset.
I have been searching for solutions, but I get even more concerned when I find people asking similar questions in other Forums with no replies. :confused:

Here is more info:

```
:~$ systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2019-01-10 09:38:21 GMT; 1h 36min ago
     Docs: man:bluetoothd(8)
 Main PID: 1864 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1864 /usr/lib/bluetooth/bluetoothd

ene 10 09:38:21 gabo bluetoothd[1864]: Starting SDP server
ene 10 09:38:21 gabo bluetoothd[1864]: Bluetooth management interface 1.14 initialized
ene 10 09:38:21 gabo systemd[1]: Started Bluetooth service.
ene 10 09:38:43 gabo bluetoothd[1864]: Endpoint registered: sender=:1.137 path=/MediaEndpoint/A2DPSource
ene 10 09:38:43 gabo bluetoothd[1864]: Endpoint registered: sender=:1.137 path=/MediaEndpoint/A2DPSink
ene 10 10:42:55 gabo bluetoothd[1864]: Failed to set mode: Failed (0x03)
ene 10 10:48:46 gabo bluetoothd[1864]: Failed to set mode: Failed (0x03)

```

```
:~$ rfkill
ID TYPE      DEVICE      SOFT      HARD
 0 wlan      phy0   unblocked unblocked
 1 bluetooth hci0   unblocked unblocked

```

```
:~$ rfkill list bluetooth
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by jeremy31 on 2019-01-10
What does this show ```
pactl list short | grep blue
```

You may have to do a complete shutdown rather than reboot or suspend with some bluetooth devices

---

### Post by gabo.cr on 2019-01-10
Hi, this is what I get:


```
:~$ pactl list short | grep blue
8	module-bluetooth-policy		
9	module-bluetooth-discover		
10	module-bluez5-discover	
```

I shutdown the computer, powered on and the problems persists. #-o

---

### Post by gabo.cr on 2019-01-25
So, I forgot to mention that I'm dual booting this computer with Windows 7.
I had to use Windows today, and while I was on it, I decided to connect my Bluetooth headset, to my surprise it wouldn't connect either.
So I figured the problem was my headset. However, I decided to check the drivers and I saw there was a driver update released this month by Intel.
So I installed the new drivers, and now the Bluetooth headset is working flawlessly. I wonder if an update needs to be made with Linux too. :confused:

---

### Post by gabo.cr on 2019-01-25
Should I try installing the firmware provided by Intel?
Here: [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html?productId=75442&localeCode=us_en](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html?productId=75442&localeCode=us_en)
My wireless card is Intel Dual Band Wireless-AC 3160

---

### Post by jeremy31 on 2019-01-26
If you switch between Ubuntu and Windows on the same computer, you will have to pair the device again in each OS

It might help to install blueman in Ubuntu, connect to the headset, right click on the headset in blueman, go to audio setting and set to off.  Disconnect from the headset in blueman, reconnect and change audio setting to A2DP

---

