---
title: "Trackpoint is useless! Help appreciated!"
date: 2011-09-27
forum: Hardware
---

### Post by dave2001 on 2011-09-27
I am trying to increase the sensitivity of my trackpoint on a thinkpad A20m running Ubuntu 10.04. The default sensitivity is ridiculously hard to use!

The normal graphical options do not increase it anywhere near enough (in fact I'm not sure I even see a difference when adjusting the "sensitivity" slider).

So to make a quick on-the-fly adjustment, I tried using the following in terminal:

```
echo -n 250 > /sys/devices/platform/i8042/serio1/sensitivity
```

I get this in return-
bash: /sys/devices/platform/i8042/serio1/sensitivity: Permission denied

I tried with sudo (in the format for an echo command):

```
sudo sh -c echo -n 250 > /sys/devices/platform/i8042/serio1/sensitivity
```

same return, didn't even ask for a password

Finally, became root (sudo su), and command worked.

Hoping to make the change persistent, I followed the instructions here: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint")  in the "configuring other options" section.

I made the file /etc/udev/rules.d/10-trackpoint.rules and put in the appropriate following text:
```
SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/sensitivity", ATTR{sensitivity}="250"
```

But on reboot, I'm stuck with the same slow-as-molasses pointer. 

Using the terminal to run a test of the new udev file with:

```
udevadm test /sys/devices/platform/i8042/serio1
```

the pertinent portion of the return is:

```
udev_device_new_from_syspath: device 0x2203abd8 has devpath '/devices/platform/i8042/serio1'
wait_for_file: file '/sys/devices/platform/i8042/serio1/sensitivity' appeared after 0 loops
udev_rules_apply_to_event: ATTR '/sys/devices/platform/i8042/serio1/sensitivity' writing '250' /etc/udev/rules.d/10-trackpoint.rules:1
udev_rules_apply_to_event: error opening ATTR{/sys/devices/platform/i8042/serio1/sensitivity} for writing: Permission denied
udev_device_new_from_syspath: device 0x2203afc8 has devpath '/devices/platform/i8042'
udev_device_new_from_syspath: device 0x2203b168 has devpath '/devices/platform'
udev_rules_apply_to_event: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/platform/i8042/serio1
udevadm_test: DRIVER=psmouse
udevadm_test: SERIO_TYPE=01
udevadm_test: SERIO_PROTO=00
udevadm_test: SERIO_ID=00
udevadm_test: SERIO_EXTRA=00
udevadm_test: MODALIAS=serio:ty01pr00id00ex00
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=serio
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'

```

Again, I'm getting a "permission denied" when the new udev config file attempts to make it's changes. I'm stumped as to why this is happening. Any ideas on how to fix the udev solution? Any ideas for other solutions? Many thanks in advance.

---

### Post by dave2001 on 2011-09-29
no ideas? I'd really like to figure out what's going on here.

I made another attempt to fix the situation.. I changed to permissions on the file /sys/devices/platform/i8042/serio1/sensitivity so that everyone has write privileges.

After that the udev test worked successfully!

However the permission change did not persist through a reboot. So back to square one.

---

### Post by dave2001 on 2011-10-03
Anyone even got a guess? I'm all ears.

---

