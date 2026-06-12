---
title: "Tell if lm-sensors is actually working?"
date: 2015-06-08
forum: Hardware
---

### Post by mamamia88 on 2015-06-08
I just swapped out a e7400 for an e8600 on an old dell and would like to keep an eye on the temps. So I installed lm-sensors and the xfce4-sensors applet and so far it just seems to give me a static 41C even though it's supposed to update every 5 seconds.  When I try service kmod start I get ```
Job for systemd-modules-load.service failed. See "systemctl status systemd-modules-load.service" and "journalctl -xe" for details.

``` Is there any way to tell if sensors are actually working?  It's really hard to believe it's a constant 41

---

### Post by QIII on 2015-06-09
Some of those Dells, with their proprietary motherboards, have sensor systems that are specific to the hardware originally installed.  That can be problematic with fan control along with temperature sensors.

Do you get an increase in fan speed under load?

---

### Post by sportscrazed2 on 2015-06-09
To be honest I can't really tell or I haven't stressed it enough to tell if fan speed is increasing with load

---

### Post by mamamia88 on 2015-06-09
edit I ran the stress command for 5 minutes and temps immediately began climbing

---

### Post by QIII on 2015-06-09
I'd say it's working, then.  ;)

---

