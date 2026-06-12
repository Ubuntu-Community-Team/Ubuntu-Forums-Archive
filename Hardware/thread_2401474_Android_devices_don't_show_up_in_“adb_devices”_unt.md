---
title: "Android devices don't show up in “adb devices” until logged into Ubuntu GUI session"
date: 2018-09-18
forum: Hardware
---

### Post by Mike_Soultanian on 2018-09-18
We have thousands of Android devices that we test on hundreds of Ubuntu hosts and one of the big problems we're running into is that unless you log into the host via the GUI, some of the devices (mainly tablets) don't show up in ADB (Android debug bridge). I was speaking with a coworker and he was saying this was due to the device being unable to mount until an active session was started, but he didn't know how to fix it - does anyone know a way around this? This is a huge problem for us because if we need to reboot a host (or many hosts), we need to remote into each one, log in, and then the devices show up.  One thing that worked (temporarily) was running "sudo udevadm trigger", but after a while the devices disappear.  It seems the only solution so far is to log in to the GUI and then the devices will stay there indefinitely.
Our systems are running Ubuntu 16.04.
Thanks!
Mike

---

