---
title: "Toshiba 300D Laptop"
date: 2012-09-01
forum: Hardware
---

### Post by Sigma1 on 2012-09-01
Hello,
I've had all sorts of problems getting the fan(s) to behave on a Toshiba Satellite 300D Laptop. The temperature was regularly rising to 100°C + after which the machine would shut down without further warning.
I've flashed the BIOS and tried a variety of GRUB boot options, but with no success. The only thing that appears to work to some degree is suspending, with Fn + F3 (and no other method), then resuming just after. Oddly enough, this gets the fans behaving as they should.
Now I'd like to know what, exactly, happens to the fans on Fn + F3, so that I can put a start-up script in /etc/rc.local. I've tried things like:
echo -n “0” > /sys/devices/virtual/thermal/cooling_device0/cur_state &&
echo -n “1” > /sys/devices/virtual/thermal/cooling_device0/cur_state 
on all three fans, but again, no luck.
Any help would be appreciated... if not I'll just stick with Fn + F3!

---

### Post by Sigma1 on 2012-09-02
Update: Fn + F3 was fine on the Toshiba with Lucid, but doesn't appear to work with Pangolin (12.04).
One solution is to put make a shell script the aim of which is to get the fans running. Something like:
```
#!/bin/bash
echo “1” > /sys/devices/virtual/thermal/cooling_device0/cur_state &&
echo “1” > /sys/devices/virtual/thermal/cooling_device1/cur_state &&
echo “1” > /sys/devices/virtual/thermal/cooling_device2/cur_state
```
Once saved in /usr/bin as fanson.sh, for example, and made executable, this can be run with ```
sudo sh fanson.sh
```
Alternatively you can turn it into a sidebar launcher by editing a .desktop file and adding a fan icon to make it pretty. Something like:
```
[Desktop Entry]
Name=Fan start up script
Comment=
Exec=sudo sh fanson.sh
Icon=fan.png
Terminal=true
Type=Application
StartupNotify=true
```
A bit of a fuss, but a least the temperature now seems to be under control.

---

