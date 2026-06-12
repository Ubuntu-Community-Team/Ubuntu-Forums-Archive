---
title: "fan revving"
date: 2018-01-02
forum: Hardware
---

### Post by cmcanulty on 2018-01-02
I have a Dell 580s dual boot machine. The fan revs every 10 seconds when in xubuntu 16.04. This happens  whether it is using much ram and cpu or very little ram and cpu. However it never does this in Windows 10. Is there a utility to fix this or trouble shoot it? Thank you

---

### Post by DuckHook on 2018-01-02
Do you use *lm-sensors*? If so, it has an associated daemon that can be separately installed called: *fancontrol*. Don't know if it will help in your case, but no harm in trying. You can always uninstall it if it doesn't do anything for you.

---

### Post by cmcanulty on 2018-01-03
Thanks I installed it but it won't run in terminal and isn't in menus, how do I run it?


```

cmcanulty@ubuntu1:~$ sudo apt install lm-sensors
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version (1:3.4.0-2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@ubuntu1:~$  sudo  lm-sensors
sudo: lm-sensors: command not found
cmcanulty@ubuntu1:~$ 
```

---

### Post by DuckHook on 2018-01-03
Instructions on setting up/using *lm-sensors*: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
Instructions for setting up *fancontrol* are further down the same page: [https://help.ubuntu.com/community/SensorInstallHowto#Controlling_fanspeeds_according_to_sensor_values](https://help.ubuntu.com/community/SensorInstallHowto#Controlling_fanspeeds_according_to_sensor_values)

*fancontrol* must be installed separately:```
sudo apt install fancontrol
```

---

### Post by cmcanulty on 2018-01-03
OK thanks

---

