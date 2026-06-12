---
title: "kde-guidance-powermanager didn't start"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by chodus on 2006-12-02
Hi 
I'm new with kubuntu. :) 

I have a problem with kde-guidance-powermanager. Everything was fine it starts automaticly with kde and work good. I was able to suspend my laptop and hibernate it. Afeter few day of using kubuntu kde-guidance-powermanager didn't start with kde. When I wont to stort it in console i have 

chodus@chodus-laptop:~$ guidance-power-manager
chodus@chodus-laptop:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Introspect error: The name org.freedesktop.Hal was not provided by any .service files
Traceback (most recent call last):
  File "/usr/share/python-support/kde-guidance/guidance-power-manager.py", line 740, in ?
    mainWindow = PowermanagerApp(None, "main window")
  File "/usr/share/python-support/kde-guidance/guidance-power-manager.py", line 688, in __init__
    self.pmwidget = PowerManager(self,name)
  File "/usr/share/python-support/kde-guidance/guidance-power-manager.py", line 95, in __init__
    self.powermanager = PowerManage()
  File "/usr/share/python-support/kde-guidance/powermanage.py", line 85, in __init__
    self._initBrightness()
  File "/usr/share/python-support/kde-guidance/powermanage.py", line 233, in _initBrightness
    brightnessDevice = self.hal_manager.FindDeviceByCapability("laptop_panel")
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.freedesktop.Hal was not provided by any .service files
power-manager: ERROR: Communication problem with power-manager, it probably crashed.


What's wrong ? have you any ideas. I was serching on forum but i didn't found a solution.

Sorry for my english :) 

Thanks for any ideas chodus

---

