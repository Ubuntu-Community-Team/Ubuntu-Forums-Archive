---
title: "Blueman-manager and blueZ broken in Xubuntu 19.04 after fresh install"
date: 2019-04-27
forum: Hardware
---

### Post by fieldsofblue2 on 2019-04-27
Hey all, I installed xubuntu yesterday because I love the xfce DE. 

Today, I was trying to connect a bluetooth controller to the computer. It's worked previously in Xubuntu and other linux distros, and it works fine in Windows. There is no hardware or BIOS switch that has been changed.

The device wasn't connecting and I figured I'd cycle the bluetooth adapter to hopefully fix it. 

I disabled the bluetooth and tried re-enabling it through the panel applet, and it failed to restart.
I restart the PC and the panel applet is missing. 

I ran systemctl status bluetooth and it responded as inactive(dead)
```
bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
     Docs: man:bluetoothd(8)



```

So, I ran sudo modprobe btusb & sudo systemctl restart bluetooth

```
bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-04-27 19:21:02 CDT; 1min 49s ago
     Docs: man:bluetoothd(8)
 Main PID: 2024 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   Memory: 2.1M
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;2024 /usr/lib/bluetooth/bluetoothd

```

So now it's reporting active, but when I run blueman-manager it asks me to enable bluetooth.
I enable bluetooth through blueman-manager and it looks fine, but somehow the manager applet isn't actually communicating with the bluez daemon. It launches the devices windows but everything is grayed out, and the adapters menu opens a small window that just has a close box on it.

Here's the output from terminal when I open blueman-manager with the command.
```
blueman-manager
_________
Load (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:60)
['Services', 'PulseAudioProfile'] 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.manager.Services.Services'> 
_________
__load_plugin (/usr/lib/python3/dist-packages/blueman/main/PluginManager.py:133)
loading <class 'blueman.plugins.manager.PulseAudioProfile.PulseAudioProfile'> 
_________
pa_context_event (/usr/lib/python3/dist-packages/blueman/main/PulseAudioUtils.py:341)
1 
/usr/bin/blueman-manager:67: DeprecationWarning: Gtk.Window.get_has_resize_grip is deprecated
  if self.window.get_has_resize_grip():
blueman-manager version 2.0.5 starting
_________
pa_context_event (/usr/lib/python3/dist-packages/blueman/main/PulseAudioUtils.py:341)
2 
_________
on_bluez_name_owner_changed (/usr/bin/blueman-manager:96)
org.bluez owner changed to  :1.157 
_________
get_interface_version (/usr/lib/python3/dist-packages/blueman/bluez/BlueZInterface.py:13)
Detected BlueZ 5 
_________
SetAdapter (/usr/lib/python3/dist-packages/blueman/gui/DeviceList.py:271)
 
_________
SetAdapter (/usr/lib/python3/dist-packages/blueman/gui/DeviceList.py:271)
No such adapter 
_________
on_adapter_changed (/usr/lib/python3/dist-packages/blueman/gui/manager/ManagerToolbar.py:83)
toolbar adapter None 
_________
pa_context_event (/usr/lib/python3/dist-packages/blueman/main/PulseAudioUtils.py:341)
3 
_________
pa_context_event (/usr/lib/python3/dist-packages/blueman/main/PulseAudioUtils.py:341)
4 
_________
on_pa_ready (/usr/lib/python3/dist-packages/blueman/plugins/manager/PulseAudioProfile.py:29)
connected 
_________
<lambda> (/usr/lib/python3/dist-packages/blueman/main/PulseAudioUtils.py:353)
1 

```

So I'm open to any and all suggestions. I've tried removing and reinstalling both the software snap versions, and the official apt-get versions. I'm really scratching my head trying to figure out what's going on. I'd like to avoid reinstalling the OS at this point, but it's only been a day and I still could if necessary.

```
./+o+-       joe@TopPlug
                  yyyyy- -yyyyyy+      OS: Ubuntu 19.04 disco
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 5.0.10-050010-generic
           .++ .:/++++++/-.+sss/`      Uptime: 25m
         .:++o:  /++++++++/:--:/-      Packages: 2114
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 5.0.3
       .:+o:+o/.          `+sssoo+/    Resolution: 3640x1920
  .++/+:+oo+o:`             /sssooo.   DE: XFCE
 /+++//+:`oo+o               /::--:.   WM: Xfwm4
 \+/+o+++`o++o               ++////.   WM Theme: Greybird
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Adwaita-dark [GTK2]
       .+.o+oo:.          `oddhhhh+    Icon Theme: elementary-xfce-darker
        \+.++o+o``-````.:ohdhhhhh+     Font: Noto Sans 9
         `:o+++ `ohhhhhhhhyo++os:      CPU: AMD Ryzen 7 2700X Eight-Core @ 16x 3.7GHz [40.8°C]
           .o:`.syhhhhhhh/.oo++o`      GPU: Radeon RX Vega (VEGA10, DRM 3.27.0, 5.0.10-050010-generic, LLVM 8.0.0)
               /osyyyyyyo++ooo+++/     RAM: 1113MiB / 16033MiB
                   ````` +oo+++o\:    
                          `oo++.      

```

---

### Post by fieldsofblue2 on 2019-04-30
I've had no responses here or on reddit where I've posted links to this thread, so I've reinstalled the entire OS. This has solved the problem.

---

