---
title: "Trackpoint Headaches T61 Thinkpad"
date: 2012-03-14
forum: Hardware
---

### Post by ATPJOE on 2012-03-14
I have a T61 with 11.10 and Im having the hardest time figuring out how to make my trackpoint sensitivity and speed better. I've googled it for the past hour and no luck. I have installed "Pointing Devices" and "configure-trackpoint" and both apps are not able to be found ANYWHERE even though they are "installed". 

Could somebody point me in the right direction? My finger is super sore from pushing the nub so darn hard.

Thanks
Joe

---

### Post by kurt18947 on 2012-03-14
I don't know if it'll help but "gpointing-device-settings" is in the Precise repository.

---

### Post by dave2001 on 2012-03-24
I used 11.10 on my T60 for a while, so I know this method worked for me. 

Try this first
```
echo -n 225 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
```

If your trackpoint now moves much faster, great!
If not try this
```
echo -n 225 > /sys/devices/platform/i8042/serio1/sensitivity
```

IF you got a "permission denied" message, become root first
```
sudo su
``` and then give the above commands.

Hopefully one of the two commands made your trackpoint very sensitive.

Take the command that worked, and put into a config file so that it will happen at boot.
create the file:
```
gksudo gedit /etc/udev/rules.d/10-trackpoint.rules
```
enter the following into the file:
```
[SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity", ATTR{sensitivity}="225"]
```
Please change the path to match (you may have to omit the /serio2 portion if the second command was the one which worked earlier). Save the file and reboot.

I found this method on the thinkwiki page:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint")

---

