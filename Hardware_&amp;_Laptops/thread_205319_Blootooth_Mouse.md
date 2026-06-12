---
title: "Blootooth Mouse"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by bsleys on 2006-06-28
There has got to be a better way to get my mouse working.  I have an Acer 5672WLMI laptop with builtin bluetooth and a Logitech V270 bloothtooth mouse.  I have nearly everything working just fine with a few exceptions.

To get my mouse to work I have to do the following EVERY time I boot the computer up or after the screen saver kicks on to restore the mouse.

sudo hidd --connect 00:07:61:49:d0:43

Type in my password and hit the reset button on the bottom of the mouse.  After about 10 seconds it kick on and I'm good to go untill the next time I walk away from my computer for too long and the screen saver kicks on or I need to shutdown.

Is there some way to make this work automaticly when the mouse is on and in range of the laptop?

---

### Post by rinch on 2006-07-01
It could be that the Bluetooth mouse is now a remote device and no longer a local device. One of the command options for hidd can be changed to reflect that.  

in a terminal window do this:
```
sudo gedit /etc/default/bluez-utils

``` in that file, find the line that starts with
```
HIDD_OPTIONS="
``` 
in the comment nearby, it says that to connect to your device you can add the option "-i AA:BB:CC:DD:EE", and you probably already have this option set.  But this is no longer for you!  You must change this to: ```
HIDD_OPTIONS="--connect AA:BB:CC:DD:EE --master --server"
``` 
save and exit gedit, then
```
sudo /etc/init.d/bluez-utils restart
``` 
does it "just work"???
also try the [Bluetooth Help File]("https://help.ubuntu.com/community/BluetoothSetup")

---

### Post by willywilly on 2006-08-15
Thanks a LOT for you tutorial. Though I do have one more problem. When I turn off my mouse now for whatever reason and then turn it back on, it takes a long time until my PC re-recognizes it and makes it usable. Is there some way to speed up this delay?

---

### Post by rinch on 2006-08-15
> **willywilly said:**
> ...When I turn off my mouse now for whatever reason and then turn it back on, it takes a long time until my PC re-recognizes it and makes it usable. Is there some way to speed up this delay?
I'm not sure what you mean by "a long time".  My mouse has no power button... but when I pull the batteries out and put them back, it reconnects after about 10-15 seconds... 

If you're talking about longer than that you could try the following command:
```
sudo hidd --connect 00:11:22:33:44:55

``` and if that works for you, here's a script that you can run from a desktop button to wake the mouse up... 
```
# !/bin/sh
# This is a little script to get your bluetooth device going
#   If this works, you could try including it in /etc/default/bluez-utils
#  by editing the HIDD_OPTIONS line to look like this:  
#  HIDD_OPTIONS="--connect 00:11:22:33:44:55 --master --server"
#  where 00:11:22:33:44:55 is the mac address of your Bluetooth device

exec sudo hidd --connect 00:11:22:33:44:55

```

---

### Post by Rexbron! on 2006-08-15
Hey rinch,

You may want to consider rewriting/compiling your posts and posting it in the How-to forum.

---

### Post by howardf42 on 2006-08-26
I have not been able to get my Bluetooth mouse working at startup.  I've made all the recommended changes, but it won't start.  When I run ```
sudo hidd --connect 00:07:61:4D:43:89
``` I get this error message: > Can't get device information: Operation already in progress  After several hours the hidd --connect will work.  Also, after the screensaver starts or the laptop has gone to sleep mode, I have to run hidd --connect again.

Any or all help is appreciated.

---

