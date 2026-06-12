---
title: "/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed"
date: 2015-04-19
forum: Hardware
---

### Post by patiobarbecue on 2015-04-19
Hi, I am trying to install lm-sensors to get my fan under control. Even after BIOS is set to Silent, the chase fan is still running at high speed.  As I have a dual system, hence I know from SpeedFan under windows that the chase fan can be run at a much lower speed.

I followed [http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed) to install lm-sensors and fancontrol, and got stuck at the third step, i.e., the pwmconfig found no pwm-capable sensor. 

Then I followed [https://forums.gentoo.org/viewtopic-t-923962.html](https://forums.gentoo.org/viewtopic-t-923962.html) as my motherboard is ASUS Rampage III Formula. After put asus_atk0110 into the /etc/modules, it is successfuly loaded as seen here:

home: lsmod  | grep asus
asus_atk0110           18078  0 

However, running pwmconfig still returned nothing. Any suggestion?

MB: ASUS RAMPAGE III FORMULA
Chase Fan with 4 pin wired at CHA_FAN1 on the MB
Ubuntu 14.o4 LTS with KDE

---

### Post by patiobarbecue on 2015-04-19
just double checked my BIOS setting in Power->Fan Speed and found that the cha_fan1 speed is 0, which is wrong. and Power->Fan Control only shows Ignore or N/A for cha_fan1. Hence it is not a surprise that fan control attemp at OS level is useless. However, according to the manual of this MB, ASUS RAMPAGE III FORMULA should be able to control all chasis fans, power fan, and OPT fans. Anyone has experience with this MB?

---

