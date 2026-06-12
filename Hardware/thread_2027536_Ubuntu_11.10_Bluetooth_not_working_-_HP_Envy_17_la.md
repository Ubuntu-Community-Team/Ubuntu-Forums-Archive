---
title: "Ubuntu 11.10 Bluetooth not working - HP Envy 17 laptop"
date: 2012-07-16
forum: Hardware
---

### Post by Aure217 on 2012-07-16
Hi,

---
Edit: Works in 12.04, but app has performance issues. Any suggestions? I need the hardware compatibility of 12.04 but the bluetooth functionality of 11.10.
---
   using Ubuntu 11.10 for one specific BT app.
No idea if the BT adapter in this laptop is working.
How can I verify it?

BT icon exists in the top right, next to wireless icon.
Clicking it gives
---
BT On
Turn BT Off
Prefs
---

Prefs is a screen with 
Bluetooth [     | OFF]
in it and not much else.

Directions/diagnostics?

Any help appreciated.
thanks

edit:
lsusb | grep -i bluetooth
shows empty response.
no idea what that means, but googling suggested that.

As far as I can tell, the BT is NOT DISABLED BY HARDWARE SWITCH.
I have a hardware switch, and if I press it, it says "BT Disabled by HW switch" in the Prefs window.
If I press it again, it just says "BT Disabled".

hcitool dev shows no devices
hciconfig likewise

BT device is probably working. Windows seems to detect it etc.
Can't test Bluetooth functionality itself, since the app I want to test is only for Linux.

Bluetooth device is definitely working. Just transfered a file to someone's phone on Windows.
No progress in Ubuntu though. :/

Works out of the box on 12.04, but the stuff I want to run has performance issues in 12.04.

---

### Post by Aure217 on 2012-07-17
Since it works on Ubuntu 12.04... is there anything I can do to port the fix back or something?

Perhaps something simple like copying a conf file, or replicating some settings somewhere?

---

