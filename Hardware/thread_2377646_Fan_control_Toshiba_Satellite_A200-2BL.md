---
title: "Fan control Toshiba Satellite A200-2BL"
date: 2017-11-15
forum: Hardware
---

### Post by stn021 on 2017-11-15
Hello,

the cooler of my Toshiba Satellite A200-2BL behaves a bit erratic.

At higher temperatures than 47 degrees celsius it runs continuously. That is fine.
Around 46 degrees it starts an stops every 2 seconds.  That is really annoying.

I have googled a lot and tried different options.

 lmsensors+fancontrol does not find any controllable fan.
/sys/devices/virtual/thermal/cooling_device?/cur_state exists but always  has the value "0". Values  0..7  have no effect at all on the fan.
Adding "coretemp" to /etc/modules and reboot has no effect, neither on the fan nor fanconctol.

Is there anything else I can try?

THX , stn

---

