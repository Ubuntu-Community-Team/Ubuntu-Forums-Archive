---
title: "Disabling Trackpoint"
date: 2008-05-02
forum: Hardware
---

### Post by romack991 on 2008-05-02
Running 8.04, I have configure-trackpoint driver which lets me turn off the trackpoint on my dell c610. (stops the drifting) 

Anyways I can apply it and stop the trackpoint from working. Also save it to /etc/trackpoint/trackpoint.conf

but when I restart, the trackpoint works again and I have to go into the driver and turn it off again.

trackpoint.conf listed below
#!/bin/bash

echo -n  > /sys/devices/platform/i8042/serio0/serio2/sensitivity
echo -n  > /sys/devices/platform/i8042/serio0/serio2/inertia
echo -n  > /sys/devices/platform/i8042/serio0/serio2/speed
echo -n  > /sys/devices/platform/i8042/serio0/serio2/reach
echo -n  > /sys/devices/platform/i8042/serio0/serio2/draghys
echo -n  > /sys/devices/platform/i8042/serio0/serio2/mindrag
echo -n  > /sys/devices/platform/i8042/serio0/serio2/thresh
echo -n  > /sys/devices/platform/i8042/serio0/serio2/upthresh
echo -n  > /sys/devices/platform/i8042/serio0/serio2/ztime
echo -n  > /sys/devices/platform/i8042/serio0/serio2/jenks
echo -n  > /sys/devices/platform/i8042/serio0/serio2/press_to_select
echo -n  > /sys/devices/platform/i8042/serio0/serio2/skipback
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/inertia
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/speed


I tried to add the trackpoint.conf into my startup programs in session preferences but that didn't seem to work either. I'm new to Ubuntu and Linux. Can anybody explain how to apply these settings at startup?

In the configure-trackpoint, it states "To save settings, please copy the following lines into your start up file."

echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/inertia
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/speed

But I haven't been able to find what startup file and how to edit it.

---

### Post by Doc Hoss on 2008-06-18
I'm still pretty new to the Ubuntu scene myself, but I think you may be looking for the startup file called /etc/rc.local  Someone please feel free to correct me if I'm wrong.  I've got some startup things in there and they seem to work, so maybe try there.  Good luck!

---

### Post by immeëmosol on 2009-01-21
rc.local gets run everytime the user-level is altered.

It probably wouldn't harm doing it like this though.
----
I think it might be better to put it in another start-up script.

On [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint) more information can be found as well as some examples of how to configure it all(all different methods of accomplishing the same

On that site amongst many /etc/sysfs.conf is mentioned as a place to put in the configuration.
I have no tried to source the /etc/trackpoint/trackpoint.conf file from there, as I see no reason to type the echo`s on two different places. Haven't tried if this will work though.

As is it says in the notes:
With kernels 2.6.19 (Feb 2007) and later, config files for this driver are located in /sys/devices/platform/i8042/serio1.
(I somehow missed this the first time I read the page.)

(You're current kernel-release/version van be found with the command:
uname -r    (or uname -a   (if you want to see everything...)

And as it says on the end of that page, the default /etc/init.d/trackpoint script generates an error, which makes it not source||load the trackpoint.conf file.
(But this file is not really needed if the config-stuff is put inside the sysfs.conf)

I will however notify the creator of the init-script of this error, as it seems as a nice way to configure the trackpoint.


My apollogies if this post is confusing,
please do ask for more information if things are unclear.

---

