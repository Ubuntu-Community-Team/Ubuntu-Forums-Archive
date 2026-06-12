---
title: "dell_smm_hwmon: unable to get smm Dell signature"
date: 2016-08-05
forum: Hardware
---

### Post by ggarra13 on 2016-08-05
I recently upgraded to Kubuntu 16.04.1 LTS from Kubuntu 14.04.4 LTS and now when booting I get the message:

dell_smm_hwmon: unable to get SMM Dell signature

This message corrupts the graphics of the login and, I may wrongly believe, also messes with the touchpad, as it becomes active on login (something that was not like that before).  The machine is a Dell Studio XPS.

Anyway, any help on trying to remove the message and make the login behave?

---

### Post by alex-pavlenko-onpriii on 2016-09-08
Hi Have same here, less than a week after upgrade start getting this message during boot (boot hangs 5 + seconds after this messsage.
How to fix this...Any one?

---

### Post by Yellow Pasque on 2016-09-09
[https://bugs.launchpad.net/ubuntu/+bug/1509578](https://bugs.launchpad.net/ubuntu/+bug/1509578)

You may want to try blacklisting the dell-smm-hwmon module. You may not be able to monitor CPU temp or fan speed, but it won't affect the actual power management:
```
echo "blacklist dell-smm-hwmon" | sudo tee -a /etc/modprobe.d/blacklistdellhwmon.conf
```
The dell-smm-hwmon module used to be called i8k and the two are aliased, so for good measure:
```
echo "blacklist i8k" | sudo tee -a /etc/modprobe.d/blacklistdellhwmon.conf
```
Reboot to test the change.

If you want to revert the change, you can delete the file you created:
```
sudo rm /etc/modprobe.d/blacklistdellhwmon.conf
```

It may also be worth looking to see if there is a BIOS update for your laptop.

---

### Post by cocoamok on 2016-09-18
Thanks. To upgrade my BIOS to the latest didn't work, but to blacklist the dell-smm-hwmon module did work and saved me time with every boot.

---

### Post by bvansteen on 2017-08-27
Hello all,
I just installed 16.04 onto a Dell Inspiron 530 desktop, overwriting Window 7.
This is obviously a very old machine, and only intended to be a hacking machine (I want to learn to use Linux).
After the installation and multiple attempted re-starts, I only get this message, and the boot process completely hangs.
Does anyone have any suggestions?
It seems that this is an issue with many Linux distros, so not sure a different version would help.
Or is my desktop just too old for load Linux onto it?
Thanks.
Brian.

---

