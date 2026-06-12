---
title: "Intel 8087-0a2b: 100% usage / bluetooth: No default controller available"
date: 2017-06-18
forum: Hardware
---

### Post by danielg09 on 2017-06-18
Hello all,
This is my first Ubuntu forum post, so I apologize if there is anything wrong with it. I did read the forum rules and gathered if I'm new I should post in the new section. However, I wasn't sure whether that meant new to the forum or new to Ubuntu in general. Anyhow, I have been using Ubuntu for about 4 months now and I find it a great OS. Recently, I purchased a Xiaomi Air 13 laptop and loaded Ubuntu(16.04) onto it. I am currently running gnome-shell with a few extensions and managed to get nvidia optimus working alongside laptop-mode-tools for power efficiency and getting about 5-6 hours moderate use. I also got libinput-gestures up and running with 3-4 finger gesture recognition and the proper Synaptics drivers. All in all I gotta say I am loving the overall experience.

Anyway the issue here lies on the Intel 8087-0a2b adapter. What I have gathered this far is that it is a Bluetooth adapter and that it might be a controller along with the WiFi card. When I run powertop, the device appears to be on a 100% usage, with a power estimation of 4~6W in average. Sometimes a little less sometimes a bit more. 

What I have tried to do so far to reduce the usage: 
 Blacklist the device in the laptop-mode-tools config file by getting the ID using 'lsusb', to have it be suspended when not in use. I have also tried turning off the WiFi adapter to see if it would also control the device usage, but only the network interface seems to have changed in powertop. I have tried 'rfkill' to block Bluetooth.

I have also tried to access the bluetooth controller in the terminal by doing bluetoothctl and then "power on" and the output is "No default controller available". I must point out also that Bluetooth does work through the Ubuntu/Gnome GUI, and is able to have other devices connected to it.

With the above said, my question is: How can I set the bluetooth controller if it's not properly set? And if the controller is not set, how is the gnome-shell able to power it on and off? The laptop no longer appears on Bluetooth networks once I switch it off through the GUI. Ultimately, I should point out that I'm most concerned about preserving battery life, and this device is the one using up the most.

Thanks in advance for any suggestions, and I apologize if this is in the wrong section. I'd be happy to move it where it belongs.

---

### Post by efflandt on 2017-06-18
WiFi and Bluetooth are typically combined on the same miniPCIe card of a laptop because they both use 2.4 GHz and same antenna, but Bluetooth is much lower power. What are you using to determine power use of Bluetooth. I tried using powertop in 16.04 on a laptop and it did not show power use, just things like CPU cycles or whether hardware was powered as much as 100% of the time. If you use Bluetooth for something (or WiFi) you would not want that to only operate intermittently.

According to "sudo lshw" the USB Bluetooth dongle on my desktop PC uses 100 mA maximum (0.5 watt). But that only shows power use of USB devices, not PCI devices.

---

### Post by danielg09 on 2017-06-19
> **efflandt said:**
> WiFi and Bluetooth are typically combined on  the same miniPCIe card of a laptop because they both use 2.4 GHz and  same antenna, but Bluetooth is much lower power. What are you using to  determine power use of Bluetooth. I tried using powertop in 16.04 on a  laptop and it did not show power use, just things like CPU cycles or  whether hardware was powered as much as 100% of the time. If you use  Bluetooth for something (or WiFi) you would not want that to only  operate intermittently.

According to "sudo lshw" the USB Bluetooth dongle on my desktop PC uses  100 mA maximum (0.5 watt). But that only shows power use of USB devices,  not PCI devices.

Thanks for your response.
I am using powertop to determine Bluetooth and wireless use. This particular device(Intel 8087), is the one which is at 100% usage. When turning on Bluetooth or WiFi, the devices "Radio device: btusb" and "Network interface: wlp2s0" get a 100% usage as well and like you say, with much less power drain than the Intel 8087 device sitting at 3W+. 

Through more digging around, I discovered that the only time the Intel 8087 device drops the 100% usage is when the computer is physically plugged in through the USB-C input port for the battery charger. 

Would it be possible that the Intel device is rather a USB-C port controller as opposed to the WiFi/Bt card? I tried looking up some answers on this particular laptop or other USB-C controllers in general but couldn't find much in relation to it, although seems unlikely. Any idea on this?
Thanks!

---

