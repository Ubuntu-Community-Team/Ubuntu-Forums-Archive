---
title: "Sync WM2003 with Jaunty"
date: 2009-11-18
forum: Hardware
---

### Post by rx7haze on 2009-11-18
I'm trying to set up my Axim x30 to sync with Evolution in Jaunty. At one point I was able to view the directories on the axim using synce-pls. I've tried so many different things to try and get this to work that I've now messed something up and can no longer get synce-pls to work.
I have synce-hal, libopensync0, librra-tools, librapi2-tools installed.
When I set the axim in the cradle it says connected.
When I try synce-pls I get...

```
** (process:5098): WARNING **: synce_info_from_hal: Failed to obtain property pda.pocketpc.iface_address for device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_0: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.iface_address on device with id /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_0
[rapi_context_connect:180] DCCM PID entry not found for current connection
[main:115] Failed to initialize RAPI

```

Any help would be much appreciated.

---

### Post by rx7haze on 2009-11-18
I decided to start over and went back to the instructions here...[http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html](http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html)
I'm using synce-serial and odccm.
If I type odccm I get the following error but am able to continue, sort of.
```
** ERROR **: Failed to get bus name: Connection ":1.93" is not allowed to own the service "org.synce.odccm" due to security policies in the configuration file
aborting...
Aborted

```
I have no idea what config file this is referring to.

I am able to run synce-serial-start.
Now when I run synce-pls it lists the directories on my pda but it first spits out the following error.
```
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_1 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_0 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0 not fully set in Hal, skipping

```

I am so confused at this point.

---

### Post by rx7haze on 2009-11-18
A little progress. I installed synce-hal which subsequently uninstalled synce-serial and odccm. Now after I dock my axim I see connected on its screen and can run synce-pls with no errors and can see my directories.
Now what do I use to sync with Evolution? I get confused with what should be used with wm2003 vs wm5/6.

---

### Post by rx7haze on 2009-11-18
I decided to install multisync with libmultisync-plugin-all.
I created a syncpair using synce-plugin and evolution2-sync. The details of the file are...
```
remoteclient = synce-plugin
localclient = evolution2-sync
syncinterval = 600
dwelltime = 5
manualonly = yes
reconninterval = 10
object_types = 0x7
syncsound = 
welcomesound = 
displayname = 
playsyncsound = no
playwelcomesound = no
filter = 1,1,1,"CATEGORIES","*"
filter = 1,2,1,"CATEGORIES","*"
filter = 2,1,1,"CATEGORIES","*"
filter = 2,2,1,"CATEGORIES","*"
filter = 4,1,1,"CATEGORIES","*"
filter = 4,2,1,"CATEGORIES","*"
duplicatemode = 0
```

The local settings config file looks like this...
```
<config>
&#8722;
<adress_path>
file:///home/hayes/.evolution/addressbook/local/1234742802.5968.0@hayes-desktop
</adress_path>
&#8722;
<calendar_path>
file:///home/hayes/.evolution/calendar/local/1233148396.6857.1@hayes-desktop
</calendar_path>
<tasks_path/>
</config>
```

After I save the syncpair multisync shuts down unexpectedly. Here is the output from the console...
```
plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/hayes/.multisync/1/localsettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
Segmentation fault

```

Now I can't restart multisync. Probably need a reboot.
I feel like I'm so close but not sure what to do next.

---

### Post by rx7haze on 2009-11-18
Reboot didn't work. Needed to delete the syncpair from ~/.multisync.
Now it restarts.
Now i tried to create the syncpair again and the same thing happens.
Please help.

---

