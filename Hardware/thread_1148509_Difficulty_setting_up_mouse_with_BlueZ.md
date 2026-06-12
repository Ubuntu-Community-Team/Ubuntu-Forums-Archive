---
title: "Difficulty setting up mouse with BlueZ"
date: 2009-05-04
forum: Hardware
---

### Post by pillbug22 on 2009-05-04
Ubuntu 9.04, using the BlueZ 1.8 that comes with it.
 
I've read several other threads that people were sucessful in getting MS Notebook Presenter 8000 Pro connected to the previous version(s) of Ubuntu, but I'm having difficulty on Jaunty...
[LIST=1]
[*]Put the mouse in discoverable mode
[*]Open BlueZ preferences
[*]Click the "+" to add
[*]It does find the mouse and put it in the list
[*]I select the Microsoft entry in the list, and the passcode of '0000' (per MS documentation since there isn't a "no passcode" option.
[/LIST]BlueZ says sucessfuly configured device, and it's now in my list of devices. However, since there aren't any tooltips, it's hard to troubleshoot form here...
 
The mouse stays in discoverable mode (unless I turn it off/on), and the Microsoft device in the list has a blue "i".
 
Do I need to hit the icon below that looks like a plug (nothing happens if I try)? How about the icon with the blue "i" (takes away the icon next to the device in the list, but nothing else happens from what I can tell)?
 
Just a thought that I'm sure it wouldn't be too difficult if I could find some documentation somewhere - I tried the BlueZ site, and it's all developer/terminal commands, nothing on the GUI.
 
Thanks in advance-

---

### Post by seanzone on 2009-05-10
I'm having the exact same issue with a Microsoft Bluetooth Notebook Mouse 5000.  The LED still indicates that it's in discovery mode, and it doesn't work.  I was able to test the bluetooth radio by pairing it with my PDA, which worked fine.

---

### Post by sandor.nemes on 2009-05-23
The same issue here with Microsoft Mobile Memory Mouse 8000.

---

### Post by PatrickVogeli on 2009-05-25
maybe you could try [blueman]("http://blueman-project.org")

---

### Post by pillbug22 on 2009-06-28
Ok, so it's been a while since I've messed with this, but it **does** work using the USB dongle that the mouse came with, but still no luck using built-in bluetooth receiver and bluez. Guess I'll try blueman and see what happens with that - sure would be nice to not need the dongle...

---

### Post by pmfabri on 2009-10-15
Same exact broblem with microsoft mobile memory mouse and Ubuntu netbook remix. (9.04) Doesn't even detect mouse, or for that matter any bluetooth device.

Specs:
Asus EEE 1000HA
Custom-installed dell truemobile 360
Custom installed Intel 5300


I'm gonna try blueman later.

---

