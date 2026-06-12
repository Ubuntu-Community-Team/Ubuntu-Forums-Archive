---
title: "bluetooth/wireless hotkey's not working"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by wedderburn on 2007-05-24
ok i recently got a new laptop.
acer travelmate 5625WSMi 
all the hardware works(with some searching)
loaded up the acer_acpi drivers and my bluetooth functions.
with this command 
```
sudo echo "enabled: 1" >/proc/acpi/acer/bluetooth
``` 
my only issue is that this laptop is that it has two hot key's.
one is for the wireless and when pressed the commands should be like this
on: ```
echo "enabled: 1" >/proc/acpi/acer/wireless
```
off: ```
echo "enabled: 0" >/proc/acpi/acer/wireless
```
but when pressed nothing happens(naturally because the key's haven't been setup yet)

its the same with the bluetooth
when pressed the commands should be like this
on: ```
echo "enabled: 1" >/proc/acpi/acer/bluetooth
```
off: ```
echo "enabled: 0" >/proc/acpi/acer/bluetooth
```

So my question is how do i assign these commands to the hotkey's(turning on and off the service) also how do i find the key code for these two buttons so i can assign them.
**Edit**
found the scancodes for the 2 buttons
bluetooth: 215
wifi: 213
and im using keytouch to configure the extra function keys.
i just need a script now to easierly turn on the wireless and off if its on.  

thanks
andrew

---

### Post by thayerw on 2007-05-24
I'm not sure if this will help or not, but have a look at the [FONT="Courier New"]hotkey-setup[/FONT] package in the repos.  Assuming it's already installed on your laptop, I believe you can find the config files for it here:

[FONT="Courier New"]/usr/share/hotkey-setup[/FONT]

and the actual init script here:

[FONT="Courier New"]/etc/init.d/hotkey-setup[/FONT]

Perhaps there is something that needs to be tweaked for your specific model... good luck.

---

### Post by koshari on 2007-08-15
wedderburn have tou got this sorted yet, as i have a script that turns my BT and WiFi off using the acerhk module.

here it is if you wish to use it.

# Switching Bluetooth radio on/off

The bluetooth radio and wifi radio buttons dont work. However there are commands in acerhk that turn the BT radio on/off.
these are:
echo on > /proc/driver/acerhk/blueled
echo off > /proc/driver/acerhk/blueled

however i wrote a simple bash script and thats activated with a launcher to toggle the radio off and on
```
#!/bin/bash
blueon=`cat /home/holto/bin/.ledstate`
if [ $blueon = "0" ]; then
echo on > /proc/driver/acerhk/blueled
echo 1 > /home/holto/bin/.ledstate
else
echo off > /proc/driver/acerhk/blueled
echo 0 > /home/holto/bin/.ledstate
fi
```

---

