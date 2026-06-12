---
title: "sensors in xfce premission issue"
date: 2009-07-15
forum: Hardware
---

### Post by Omrilicious on 2009-07-15
since i came to a conclusion the shutdown i experienced occurred due to overheating i decided to add the sensors toolbar, yet to no avail:
i got this error while adding it to me toolbar:

"hddtemp" was not executed correctly, although it is executable. This is most probably due to the disks requiring root privileges to read their temperatures, and "hddtemp" not being setuid root.

An easy but dirty solution is to run "chmod u+s /usr/sbin/hddtemp" as root user and restart this plugin or its panel.

Calling "/usr/sbin/hddtemp -n -q /dev/sda" gave the following error:
/dev/sda: Permission denied

with a return value of 0.

---

### Post by b.a.w on 2009-07-15
You can run ```
sudo chmod u+s /usr/sbin/hddtemp
``` and then restart.  Like the error says it's crude but works. This is what I ended up doing for my sensors applet. You may also want to run sensors-detect with sudo to get all the sensors information if you haven't already.

---

### Post by Omrilicious on 2009-07-16
i ran that cmd, and eventually after running detect i found out there are no drivers for my cpu sensors and i cannot see the cpu temp although vista did show these stats...

---

