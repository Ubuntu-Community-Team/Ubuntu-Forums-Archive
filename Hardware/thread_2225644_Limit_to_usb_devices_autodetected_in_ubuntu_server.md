---
title: "Limit to usb devices autodetected in ubuntu server 14.04 LTS?"
date: 2014-05-22
forum: Hardware
---

### Post by praetoriancode on 2014-05-22
I setup a small server running server 14.04 lts that has many usb to serial devices for monitoring a process system.  I seem to be running into a problem where only like the first 31 usb devices in the system are auto detected.  I can see more devices in lsusb, but they never get added to /dev.  I guessing this is a udev issue?  Some of the devices that are not getting added are the exact same device that are getting added.  If I move the devices around into different hubs and move the hubs around I can get each one to auto detect if I keep the total under 31.  So its not a specific hub or device, it just more seems like a limit to how many usb devices in total it will detect.  I have googled for a few hours and did add the kern.sysv.semume=100 to the system sysctl.conf and rebooted.  That did not help.  Any ideas on how I can get it to auto detect more devices on startup?
 
Thanks

Praetorian

---

### Post by praetoriancode on 2014-05-23
I figured this out.  I had to disable Xhci in my bios so that the system would fall back to using the ehci for my usb 2.0 ports and disabled my usb 3.0 ports.  This seems like something that should be fixed by now, but isn't.  The initial issue looked like it was limiting me to 32 usb devices on the root hub including other hubs and devices.  The actual limit was after 10 or so devices I was getting "[COLOR=#000000][FONT=Consolas]can't set config #1, error -12" which I found this solution at the following link.

[/FONT][/COLOR]http://superuser.com/questions/731751/not-enough-host-controller-resources-for-new-device-state
[COLOR=#000000][FONT=Consolas]
Hopefully someone else can use this info if they run into this same problem.

[/FONT][/COLOR]

---

### Post by higginse on 2014-11-19
Is there a bug report anywhere that captures this issue?

---

