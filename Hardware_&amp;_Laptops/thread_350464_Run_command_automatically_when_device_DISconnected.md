---
title: "Run command automatically when device DISconnected?"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by tweedledee on 2007-01-31
How does one trigger a command to automatically execute when you UNplug a USB device?

Gnome provides a handy interface (removable drives & media) for triggering events upon connecting a device - however, it can't be used to trigger a program when the event occurs before the user has logged in.  Presumably these commands are passed to gnome-volume-manager, though I'm not sure of that.  What I would like is something (anything) that allows for executing a similar, arbitrary command when a device is disconnected.

I have experimented with udev, and believe this exceeds what it can do.  udev seems to only execute programs that directly act on the device being added/removed; it cannot execute an arbitrary command.

Specifically, what I would like to do is execute an xmodmap command in response to whether or not my external mouse is plugged in (I use my external mouse left-handed, but my laptop's built-in mouse works improperly with the buttons remapped) - this is just a matter of executing xmodmap at the appropriate time.  udev simply refuses to execute xmodmap (I can a variety of other things, but programs not directly related to the device itself won't run).  The Gnome approach works okay for plugging in the mouse as long as I log in first, but means I still have to manually run xmodmap if I remove it.

I would prefer not to run a daemon in that background that simply checks the status of the mouse every so often, as that seems like a major waste of resources, but I'd consider it at this point.

Any ideas?

---

### Post by tweedledee on 2007-02-07
So I have solution, in the event anyone is interested.  It makes use of dbus & python.  Use the first python script to identify connected devices; the simplest way to figure out which one of the initial list is the device you are interested in is to connect and/or disconnect it.  If you get multiple paths output, you need only choose one (my trackball generates 4 events, I just chose the shortest name).  Use the bit after the last "/" in your output (i.e., the name specific to each device) as the DeviceName in second script; change the AddAction and RemoveAction as desired (modify the three lines immediately after the "global" line).  The second script is currently configured for my trackball as an example.  Note that it is currently set so that if the device is connected when the script starts, it performs the AddAction as if you'd just connected it.

To actually use these, copy them into a text file, save them, make them executable.  Run the first script on a command line long enough to identify your device, then stop it with Ctrl+C.  The second script is designed to be added to your session startup programs.

First script (to identify devices):
```
#!/usr/bin/python

import dbus # needed to do anything
import dbus.decorators # needed to receive messages
import dbus.glib # needed to receive messages
import gobject # needed to loop & monitor

@dbus.decorators.explicitly_pass_message
def add_device(*args, **keywords):
    print 'Device Added:', ' '.join([arg for arg in args])

@dbus.decorators.explicitly_pass_message
def remove_device(*args, **keywords):
    print 'Device Removed:', ' '.join([arg for arg in args])

bus = dbus.SystemBus()  # connect to system bus
hal_manager_obj = bus.get_object('org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
hal_manager = dbus.Interface(hal_manager_obj, 'org.freedesktop.Hal.Manager')

# Add listeners for all devices being added or removed
bus.add_signal_receiver(add_device, 'DeviceAdded', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
bus.add_signal_receiver(remove_device, 'DeviceRemoved', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')

# output list of all currently connected devices
device_names = hal_manager.GetAllDevices()
for name in device_names:
    print name

# monitor
loop = gobject.MainLoop()
loop.run()
```

Second script, to execute commands upon connect & disconnect:
```
#!/usr/bin/python

global DeviceName, AddAction, RemoveAction
DeviceName = 'usb_device_46d_c408_noserial' # Logitech Trackball
AddAction = 'xmodmap -e "pointer = 3 2 1 4 5 6 7 9 8"'
RemoveAction = 'xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"'

import dbus # needed to do anything
import dbus.decorators # needed to receive messages
import dbus.glib # needed to receive messages
import gobject # needed to loop & monitor
import os # needed to 

@dbus.decorators.explicitly_pass_message
def add_device(*args, **keywords):
    Path = args[0].split('/')
    if Path[-1] == DeviceName: # Device found
        os.system(AddAction)
        
@dbus.decorators.explicitly_pass_message
def remove_device(*args, **keywords):
    Path = args[0].split('/')
    if Path[-1] == DeviceName: # Device found
        os.system(RemoveAction)

bus = dbus.SystemBus()  # connect to system bus
hal_manager_obj = bus.get_object('org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
hal_manager = dbus.Interface(hal_manager_obj, 'org.freedesktop.Hal.Manager')

# Add listeners for all devices being added or removed
bus.add_signal_receiver(add_device, 'DeviceAdded', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
bus.add_signal_receiver(remove_device, 'DeviceRemoved', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')

# get list of all devices, determine if device is connected
device_names = hal_manager.GetAllDevices()
for name in device_names:
    Path = name.split('/')
    if Path[-1] == DeviceName: # Device found
        os.system(AddAction)
        break # no need to keep looking

# monitor
loop = gobject.MainLoop()
loop.run()
```

---

### Post by aventrax on 2007-02-21
Thank you very much, It been very useful for me and my usb "dongle" :popcorn:

---

### Post by isaacklinger on 2007-02-23
Thanks! Very useful!

---

### Post by tweedledee on 2007-04-27
In case others are using these and have encountered problems upon upgrading to Feisty, the API for python-dbus has changed, rendering these scripts useless.  Here are the revised version that will work with python-dbus 0.80rc2 (no promises of much higher, the API for python-dbus has changed several times!).  The above versions will work with python-dbus ~0.7x, maybe a little ealier (i.e., Dapper & Edgy).  Use the replacements exactly as described above.

```
#!/usr/bin/python

import dbus # needed to do anything
import gobject # needed to loop & monitor

def add_device(*args, **keywords):
    print 'Device Added:', ' '.join([arg for arg in args])

def remove_device(*args, **keywords):
    print 'Device Removed:', ' '.join([arg for arg in args])

# necessary to connect to bus
from dbus.mainloop.glib import DBusGMainLoop
DBusGMainLoop(set_as_default=True)

bus = dbus.SystemBus()  # connect to system bus
hal_manager_obj = bus.get_object('org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
hal_manager = dbus.Interface(hal_manager_obj, 'org.freedesktop.Hal.Manager')

# Add listeners for all devices being added or removed
bus.add_signal_receiver(add_device, 'DeviceAdded', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
bus.add_signal_receiver(remove_device, 'DeviceRemoved', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')

# output list of all currently connected devices
device_names = hal_manager.GetAllDevices()
for name in device_names:
    print name

# monitor
loop = gobject.MainLoop()
loop.run()
```
And
```
#!/usr/bin/python

global DeviceName, AddAction, RemoveAction
DeviceName = 'usb_device_46d_c408_noserial' # Logitech Trackball
AddAction = 'xmodmap -e "pointer = 3 2 1 4 5 6 7 9 8"'
RemoveAction = 'xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"'

import dbus # needed to do anything
import gobject # needed to loop & monitor
import os # needed to 

def add_device(*args, **keywords):
    Path = args[0].split('/')
    if Path[-1] == DeviceName: # Device found
        os.system(AddAction)
        
def remove_device(*args, **keywords):
    Path = args[0].split('/')
    if Path[-1] == DeviceName: # Device found
        os.system(RemoveAction)

# necessary to connect to bus
from dbus.mainloop.glib import DBusGMainLoop
DBusGMainLoop(set_as_default=True)

bus = dbus.SystemBus()  # connect to system bus
hal_manager_obj = bus.get_object('org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
hal_manager = dbus.Interface(hal_manager_obj, 'org.freedesktop.Hal.Manager')

# Add listeners for all devices being added or removed
bus.add_signal_receiver(add_device, 'DeviceAdded', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')
bus.add_signal_receiver(remove_device, 'DeviceRemoved', 'org.freedesktop.Hal.Manager',
                        'org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')

# get list of all devices, determine if device is connected
device_names = hal_manager.GetAllDevices()
for name in device_names:
    Path = name.split('/')
    if Path[-1] == DeviceName: # Device found
        os.system(AddAction)
        break # no need to keep looking

# monitor
loop = gobject.MainLoop()
loop.run()
```

---

### Post by Manslen on 2008-06-13
Wouldn't [hotplug]("http://linux-hotplug.sourceforge.net/") do exactly what you are looking for?

---

### Post by tweedledee on 2008-06-13
> **Manslen said:**
> Wouldn't [hotplug]("http://linux-hotplug.sourceforge.net/") do exactly what you are looking for?

Hotplug has been replaced by udev.  I haven't messed around with udev since I found a workable solution, so it's possible that it would work now, but as of a year+ ago it was too simple to handle what I need.  For what it's worth, I am making use of udev indirectly, in that udev is ultimately what generates the dbus event I am monitoring.

---

### Post by Manslen on 2008-06-13
> Hotplug has been replaced by udev. I haven't messed around with udev since I found a workable solution, so it's possible that it would work now, but as of a year+ ago it was too simple to handle what I need. For what it's worth, I am making use of udev indirectly, in that udev is ultimately what generates the dbus event I am monitoring.

You are correct, of course. I've been out of the loop for too long. :-)
[Upstart]("http://upstart.ubuntu.com/getting-started.html") looks like it can do the trick.

---

### Post by tweedledee on 2008-06-13
> **Manslen said:**
> [Upstart]("http://upstart.ubuntu.com/getting-started.html") looks like it can do the trick.

Probably.  When I was last looking at this, upstart was still brand-new and I didn't have the patience to wade through it to figure everything out.  It now appears it might be actually usable and moderately well documented.  However, as Hardy nearly fried (literally) one of my computers and seriously broke two more, I gave up and moved to Debian (testing), which is not using upstart.  (In all fairness, the huge number of patches released for Hardy since release probably make it useable again, but I'm more interested in a distro that releases stable packages than one that hits a release date, especially for a "long term support" release.)

---

### Post by Manslen on 2008-06-15
Update: It seems Upstart doesn't emit usb connect/disconnect events out of the box. You have to use udev for that. And while you're at it, you can use udev in itself to trigger an action on disconnect.

In Hardy there are some issues in udev: [http://ubuntuforums.org/showthread.php?t=168221&page=5](http://ubuntuforums.org/showthread.php?t=168221&page=5)
However earlier versions probably work.

---

