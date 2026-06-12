---
title: "Bluetooth - Connection failed: br-connection-create-socket"
date: 2023-07-08
forum: Hardware
---

### Post by peyre on 2023-07-08
I'm trying to connect a wireless keyboard to my desktop, but just can't get it to work right.  This is an Anker Compact Wireless Keyboard model Y2640 ([manual]("https://support.anker.com/s/article/A7726-Anker-Bluetooth-Ultra-Slim-Keyboard-User-Manual")), and my desktop has no built-in bluetooth so I have an adapter plugged in, an ASUS Bluetooth 4.0 MSI063002406.  I'm running Xubuntu 22.04.

When I first paired it, it connected fine and I was able to type successfully.  Then I turned it off and back on (this is supposed to be a substitute for when the cat decides to lie on top of my regular wired keyboard), but I couldn't type any more.  I fiddled with it a bit, and when I told Blueman to connect it did so and I could type with it again.  However since then I haven't been able to get it to connect successfully.  I've tried over and over but nothing seems to work.  When I turn on the keyboard, I get two notifications: Connected and Disconnected, then again, then it just sits there.  Sometimes it shows in Blueman, sometimes not.  At one point I got the message "Connects and disconnects several times, then stays disconnected" in Blueman, but not any more.  Here are the results of **blueman-applet --loglevel** debug after yet another failed connection:

```
blueman-applet 10.11.13 INFO     PluginManager:85 load_plugin: ['Networking', 'StatusIcon', 'NetUsage', 'StandardItems', 'ShowConnected', 'NMPANSupport', 'TransferService', 'DisconnectItems', 'DiscvManager', 'PowerManager', 'GameControllerWakelock', 'PPPSupport', 'AutoConnect', 'AuthAgent', 'KillSwitch', 'Battery', 'Menu', 'ExitItem', 'SerialManager', 'NMDUNSupport', 'AppIndicator', 'DBusService', 'ConnectionNotifier', 'RecentConns', 'DhcpClient']
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.Networking.Networking'>
blueman-applet 10.11.14 INFO     Networking:35 load_nap_settings: Loading NAP settings
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.Menu.Menu'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.StatusIcon.StatusIcon'>
blueman-applet 10.11.14 DEBUG    Base:60 do_g_properties_changed: /org/bluez/hci0 {'Address': '5C:F3:70:A6:9E:AA', 'AddressType': 'public', 'Name': 'peyre', 'Alias': 'peyre', 'Class': 8126724, 'Powered': True, 'Discoverable': True, 'DiscoverableTimeout': 0, 'Pairable': True, 'PairableTimeout': 0, 'Discovering': True, 'UUIDs': ['00001133-0000-1000-8000-00805f9b34fb', '0000110e-0000-1000-8000-00805f9b34fb', '00001105-0000-1000-8000-00805f9b34fb', '00001132-0000-1000-8000-00805f9b34fb', '00001200-0000-1000-8000-00805f9b34fb', '00001104-0000-1000-8000-00805f9b34fb', '00005005-0000-1000-8000-0002ee000001', '00001108-0000-1000-8000-00805f9b34fb', '0000110c-0000-1000-8000-00805f9b34fb', '00001801-0000-1000-8000-00805f9b34fb', '0000112f-0000-1000-8000-00805f9b34fb', '0000180a-0000-1000-8000-00805f9b34fb', '0000110b-0000-1000-8000-00805f9b34fb', '00001800-0000-1000-8000-00805f9b34fb', '0000111f-0000-1000-8000-00805f9b34fb', '0000110a-0000-1000-8000-00805f9b34fb', '00001106-0000-1000-8000-00805f9b34fb'], 'Modalias': 'usb:v1D6Bp0246d0540', 'Roles': ['central', 'peripheral']}
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.DBusService.DBusService'>
blueman-applet 10.11.14 WARNING  PluginManager:147 __load_plugin: Not loading PPPSupport because its conflict has higher priority
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.PowerManager.PowerManager'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.StandardItems.StandardItems'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.ShowConnected.ShowConnected'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.NMPANSupport.NMPANSupport'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.TransferService.TransferService'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.DisconnectItems.DisconnectItems'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.DiscvManager.DiscvManager'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.GameControllerWakelock.GameControllerWakelock'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.AutoConnect.AutoConnect'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.AuthAgent.AuthAgent'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.KillSwitch.KillSwitch'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.Battery.Battery'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.ExitItem.ExitItem'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.SerialManager.SerialManager'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.NMDUNSupport.NMDUNSupport'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.AppIndicator.AppIndicator'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.ConnectionNotifier.ConnectionNotifier'>
blueman-applet 10.11.14 INFO     PluginManager:156 __load_plugin: loading <class 'blueman.plugins.applet.RecentConns.RecentConns'>
blueman-applet 10.11.14 WARNING  PluginManager:147 __load_plugin: Not loading DhcpClient because its conflict has higher priority
blueman-applet 10.11.14 INFO     KillSwitch:106 io_event  : killswitch registered 3
blueman-applet 10.11.14 INFO     KillSwitch:122 io_event  : State: True
blueman-applet 10.11.14 INFO     PowerManager:178 update_power_state: off False | foff False | on True | current state True | new state True
blueman-applet 10.11.14 INFO     KillSwitch:85 _on_connman_vanished: net.connman vanished
blueman-applet 10.11.14 INFO     TransferService:234 _on_dbus_name_appeared: org.bluez.obex :1.60
blueman-applet 10.11.14 INFO     Applet:54 _on_dbus_name_appeared: org.bluez :1.15
blueman-applet 10.11.14 INFO     Networking:71 set_nap   : set nap False
blueman-applet 10.11.14 INFO     Functions:114 launch    : Gtk eventtime is 0, not using LaunchContext
blueman-applet 10.11.14 DEBUG    Base:60 do_g_properties_changed: /org/bluez/hci0/dev_F8_AB_E5_2A_0E_9F {'Address': 'F8:AB:E5:2A:0E:9F', 'AddressType': 'public', 'Name': 'JBL TUNE510BT', 'Alias': 'JBL TUNE510BT', 'Class': 2360344, 'Icon': 'audio-headphones', 'Paired': True, 'Trusted': True, 'Blocked': False, 'LegacyPairing': False, 'Connected': False, 'UUIDs': ['00001101-0000-1000-8000-00805f9b34fb', '00001108-0000-1000-8000-00805f9b34fb', '0000110b-0000-1000-8000-00805f9b34fb', '0000110c-0000-1000-8000-00805f9b34fb', '0000110e-0000-1000-8000-00805f9b34fb', '0000111e-0000-1000-8000-00805f9b34fb', '00001200-0000-1000-8000-00805f9b34fb'], 'Modalias': 'bluetooth:v005Dp223Bd0100', 'Adapter': '/org/bluez/hci0', 'ServicesResolved': False}
blueman-applet 10.11.14 INFO     BluezAgent:56 register_agent: Register Agent
blueman-applet 10.11.15 INFO     RecentConns:107 initialize: rebuilding menu
blueman-applet 10.11.15 ERROR    AgentManager:20 on_register_failed: /org/bluez/obex/agent/blueman org.bluez.obex.Error.AlreadyExists Agent already exists
blueman-applet 10.11.15 INFO     ShowConnected:50 enumerate_connections: Found 0 existing connections
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.RecentConns.RecentConns object at 0x7f5e38ef9330>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.ConnectionNotifier.ConnectionNotifier object at 0x7f5e38ef9750>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.AppIndicator.AppIndicator object at 0x7f5e38ef9300>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.NMDUNSupport.NMDUNSupport object at 0x7f5e38ef96c0>
blueman-applet 10.11.15 DEBUG    SerialManager:50 on_delete : Terminating any running scripts
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.SerialManager.SerialManager object at 0x7f5e38ef96f0>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.ExitItem.ExitItem object at 0x7f5e38ef95a0>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.Battery.Battery object at 0x7f5e38ef9210>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.KillSwitch.KillSwitch object at 0x7f5e38ef9480>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.AuthAgent.AuthAgent object at 0x7f5e38ef9510>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.AutoConnect.AutoConnect object at 0x7f5e38ef9120>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.GameControllerWakelock.GameControllerWakelock object at 0x7f5e38ef94b0>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.DiscvManager.DiscvManager object at 0x7f5e38ef8dc0>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.DisconnectItems.DisconnectItems object at 0x7f5e38ef9150>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.TransferService.TransferService object at 0x7f5e38ef9360>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.NMPANSupport.NMPANSupport object at 0x7f5e38ef8f70>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.ShowConnected.ShowConnected object at 0x7f5e38ef8f40>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.StandardItems.StandardItems object at 0x7f5e38ef8cd0>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.PowerManager.PowerManager object at 0x7f5e38ef8ca0>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.DBusService.DBusService object at 0x7f5e3b2d8d00>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <StatusIcon.StatusIcon object at 0x7f5e3c6d6c40 (blueman+plugins+applet+StatusIcon+StatusIcon at 0x5621ff57b840)>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.Menu.Menu object at 0x7f5e38ef8970>
blueman-applet 10.11.15 DEBUG    BasePlugin:63 _on_plugin_delete: Deleting plugin instance <blueman.plugins.applet.Networking.Networking object at 0x7f5e3b29dd20>

```

It's odd.  This keyboard will pair to my other two devices.  It pairs to my phone, no problem.  It pairs to my Fire tablet, no problem - in fact I just spent two weeks traveling in Europe without a laptop, and with this keyboard the tablet made a decent substitute for a real computer.  It connects successfully every time I turn it on.  I have a pair of JBL bluetooth headphones, and they connect to this same bluetooth adapter on my desktop every time I turn them on.  (They're off right now.)  But this keyboard...not so much.  When I turn it on at my desktop, the #3 connected light never turns on.  If I press the key combo to pair it, the indicator turns on very briefly then off, and I get the Connected/Disconnected notifications.

---

### Post by smokingwheels on 2024-03-24
Try 
[COLOR=var(--black-600)][FONT=var(--ff-mono)]sudo apt install libspa-0.2-bluetooth
reboot

[/FONT][/COLOR]

---

### Post by peyre on 2024-03-24
Thanks smokingwheels!  I hadn't found a solution, so great to hear there's something to try.  I'm on the road right now but I'll try it when I get home.

So what file do I edit to add this [COLOR] section (or add the above to the [COLOR] section?

---

