---
title: "control fan speed"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by Wascalwabbit on 2006-11-04
wow, i`m realy starting to enjoy linux, slowly but shurely.
ran into something i need some help with though

I tried to get some fan speed control, just for the hell of it really, if got a loud fan, but no heat problem.
I followed the steps described at 

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_control_fan_speed_.28lm-sensors.29)


 i`ve detected my speed, temps, and v`s, so far so good. i created the "fancontrol" file, but when i run it i get this


 * Starting fancontrol daemon... start-stop-daemon: Unable to open pidfile `/var/run/fancontrol-pid' for writing:  Permission denied (Permission denied)
                                                                         [ ok ]




thanks for the help

---

### Post by kswenson on 2006-11-04
Make sure to use "sudo" before the command you are doing...

---

### Post by esaym on 2006-11-04
or sudo chmod 777 /var/run/fancontrol-pid

---

### Post by Wascalwabbit on 2006-11-05
sudo, duh!

thanks for the help

---

