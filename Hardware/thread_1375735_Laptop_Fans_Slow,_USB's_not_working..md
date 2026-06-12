---
title: "Laptop Fans Slow, USB's not working."
date: 2010-01-08
forum: Hardware
---

### Post by Sycomunkee on 2010-01-08
OK so my problem is this. Since I have installed Ubuntu My USB ports are not reading my Antec Laptop Cooler. As far as I know Ubuntu is not allowing it to recieve power. I have not tried any other USB devices but this is all I know. 

Also is there any form of fan control program? My fans do not seem to be blowing out the hot air fast enought and my laptop is getting pretty hot.

**_My Setup_**
HP dv6604nr
Ubuntu 9.10 x64
AMD Athlon 64 x 2 TK-55 CPU, 
4GB DDR2 Memory
160GB SATA
DVD+-RW Drive, 15.4" WXGA Display
GeForce Go 7150M, 
802.11g Broadcom BCM94311MCG 

I am so new to Linux it's not even funny. So far so good though, I'm really enjoying the desktop and customization. However I don't know any of the commands or how to install anything. So please take it easy on me. 

I appreciate any help that anyone can provide. :D

---

### Post by sanderd17 on 2010-01-08
Ok, fan control is a difficult topic to find information on. It's very hardware specific but I hope you can do somthing with this thread: []("http://ubuntuforums.org/showthread.php?p=8593416#post8593416")

About the USB ports: can you first try something else? like a normal flash drive. Than you can see if the usb ports are guilty or somthing else.

As for installing software in ubuntu, read this thread: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by Sycomunkee on 2010-01-08
> **sanderd17 said:**
> Ok, fan control is a difficult topic to find information on. It's very hardware specific but I hope you can do somthing with this thread: 

About the USB ports: can you first try something else? like a normal flash drive. Than you can see if the usb ports are guilty or somthing else.

As for installing software in ubuntu, read this thread: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Wow, a way to install things was right in front of my face. 
I'll try the usb situation later today

Thank you!

---

### Post by Sycomunkee on 2010-01-08
> **sanderd17 said:**
> Ok, fan control is a difficult topic to find information on. It's very hardware specific but I hope you can do somthing with this thread: 

About the USB ports: can you first try something else? like a normal flash drive. Than you can see if the usb ports are guilty or somthing else.

As for installing software in ubuntu, read this thread: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

OK a flash drive does work, but the Cooler is not receiving power still.
What should I check now?

---

### Post by sanderd17 on 2010-01-09
check this out:
[http://ubuntuforums.org/showthread.php?t=853179]("http://ubuntuforums.org/showthread.php?t=853179")

It seems pretty easy to control the power of your usb ports.

---

### Post by derekmbarnes on 2010-01-09
> **Sycomunkee said:**
> OK so my problem is this. Since I have installed Ubuntu My USB ports are not reading my Antec Laptop Cooler. As far as I know Ubuntu is not allowing it to recieve power. I have not tried any other USB devices but this is all I know. 

Also is there any form of fan control program? My fans do not seem to be blowing out the hot air fast enought and my laptop is getting pretty hot.

The fan is  a problem for just about everyone with a laptop. We're trying to get it fixed - bug report here:

[http://bugzilla.kernel.org/show_bug.cgi?id=14695](http://bugzilla.kernel.org/show_bug.cgi?id=14695)

There is a method of fan control, but it's not likely to work. So far everyone hits a roadblock at step 2. Instructions:

[http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed](http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed)

How to keep track of your CPU temperature:
-Go to System > Administrator > Synaptic Package Manager and search "acpi." If you don't have it already, install it.
-Once done, open Terminal and enter the following:
```
cat /proc/acpi/thermal_zone/*/trip_points
```
This will tell you the temperatures where the fan is supposed to kick in. If you're having the same problem we are, those temperatures will be pretty high. There's nothing you can do about this, so you might want to point a fan at the cooling vent until the bug is fixed.
-Go to Applications > Ubuntu Software Center and install GKrellM System Monitor.
-Open GKrellM and hit F1 to configure; set the program to display CPU temperature.
-Go to System > Preferences > Startup Applications. Switch to the Options tab and hit the "Remember Applications" button; every app that is open when you hit that button will open again when you log back in. This saves you the trouble of having to re-open GKrellM every time.

As I said, fixing this is a work in progress, and you are far from alone. Keep yourself posted with that bug report I linked you to for any changes.

---

