---
title: "Disabling Synaptics TouchPad"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by JackDog on 2006-11-08
Is there an easy way to disable/enable the synaptics touchpad on my laptop? My older HP has a button, but this one does not. Is there an applet or command I can run to toggle the touchpad? ](*,)

---

### Post by mssever on 2006-11-08
Try this: Add ```
Option "SHMConfig" "true"
``` to the touchpad section of /etc/X11/xorg.conf and restart X.

Then, to disable the touchpad, run ```
synclient TouchpadOff=1
``` To turn it back on, do ```
synclient TouchpadOff=0
```I'm sure it wouldn't be difficult to write a script to automate this and make a panel button.

---

### Post by mssever on 2006-11-08
Here's a quick and dirty script to do it (note that this probably isn't the best way, but it should work): ```
#!/bin/bash

touchpadFile="/tmp/touchpadState"
if [ -f $touchpadFile -a ! -n "$(cat $touchpadFile 2> /dev/null)" ]; then state=$(cat $touchpadFile)
else state=0; fi

if [ "$state" == "0" ]; then state=1
else state=0; fi

synclient TouchpadOff=${state} && echo $state > $touchpadFile
```Save this somewhere and make it executable. Then make a button that runs this script.

---

