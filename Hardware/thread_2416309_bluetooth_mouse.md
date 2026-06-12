---
title: "bluetooth mouse"
date: 2019-04-08
forum: Hardware
---

### Post by kilowatt5 on 2019-04-08
I have a bluetooth mouse working wonderfully on Thinkpad X250, but will not remember mouse when I reboot,
 so I have to set it up again each time I reboot

---

### Post by #&amp;thj^% on 2019-04-08
That happens a bit with 'bluetooth mice'
the way I set mine up, and your mileage may vary here.
[list]
[*]Press the bluetooth mouse's discovery mode.
[*]Open a terminal and type the command "hcitool scan"
```
hcitool scan
```
[*]Then paste the first half of your bluetooth address as the OUI.
So if your bluetooth mouse's address is AB:CD:EF:GH:IJ:KL

It would look like this:
```

<device oui="AB:CD:EF:" type="mouse" name="Microsoft Sculpt Comfort Mouse" pin="0000"/>
```

[*]Insert that line with the rest of the entries in "/usr/share/gnome-bluetooth/pin-code-database.xml"[/list]

This helps to reconnect mice that may require a pin to pair.

This should solve most reconnection issues because Ubuntu doesn't know the PIN when it reconnects. You need to provide it with one (if it needs it default is 0000).

---

