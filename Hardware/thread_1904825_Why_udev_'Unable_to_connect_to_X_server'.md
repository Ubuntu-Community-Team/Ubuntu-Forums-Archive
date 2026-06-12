---
title: "Why udev 'Unable to connect to X server' ??"
date: 2012-01-05
forum: Hardware
---

### Post by FreshFish47 on 2012-01-05
Hi everyone, recently, I come up writing a udev rules to disable the touchpad while I use the mouse. But I came across a strange situation as the title. I have tried the "synclient", but it doesn't seem to work at times.
```
synclient TouchpadOff=1
```

I lean how to do that from the web-site below. I have read it completely at least twice.
[HTML]http://www.reactivated.net/writing_udev_rules.html[/HTML]I want to analyze how the udev works, so I the command below to grasp the information, you can check them out from the attachments.
```
sudo udevd --debug
```You can see the corresponding message that present the situation at LINE 100 from add.txt. Like this.
```
1325675158.824063 [4626] util_run_program: '/usr/bin/xinput' (stderr) 'Unable to connect to X server'
```And here is my udev rules.
```
ACTION=="add", SUBSYSTEM=="input", ATTR{name}==" USB OPTICAL MOUSE", RUN+="/usr/bin/xinput set-prop 13 125 0"
ACTION=="remove", SUBSYSTEM=="input", ATTR{name}==" USB OPTICAL MOUSE", RUN+="/usr/bin/xinput set-prop 13 125 1"
```Thanks a lot.

---

### Post by FreshFish47 on 2012-01-06
Bump!
Hopes this thread can may be seen by somebody knows how to figure it out.

---

