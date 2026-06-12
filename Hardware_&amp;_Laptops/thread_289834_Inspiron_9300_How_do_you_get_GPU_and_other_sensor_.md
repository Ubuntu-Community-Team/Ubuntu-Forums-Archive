---
title: "Inspiron 9300: How do you get GPU and other sensor readings and fan triggers?"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by AsGF2MX on 2006-10-31
I have an Inspiron 9300 and am aware that the i8k module (at least the Edgy default one) only brings out the CPU temps. Is there any easy way to get the sensor readings of both the GPU and CPU and set fan speeds accordingly? I don't feel too good with only the CPU temp being used to trigger the GPU fan as well](*,)

I am fairly sure there must be a way so what is it? Before someone asks if I'm having temperature problems, the answer is no but the fans are always on and absolutely kill the battery.

I have a PM 2.13GHz and an nV 6800Go.

---

### Post by John.Michael.Kane on 2006-10-31
Have a read [http://ubuntuforums.org/showthread.php?t=2780&highlight=sensor+readings](http://ubuntuforums.org/showthread.php?t=2780&highlight=sensor+readings) may be of use.

---

### Post by AsGF2MX on 2006-10-31
I can't seem to get any responses but then again, I am getting:

> Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!


I must be doing something wrong, just not sure what. Hmm...also despite having loaded the i8k module as well, the lm-sensors does not pick it up but I can confirm i8k is working.

[quote="sensordetect"]#----cut here----
# I2C adapter drivers
i2c-i801
# I2C chip drivers
eeprom
#----cut here----
[/quote]

[quote="mkdevshoutput"]/dev/i2c-0
mkdev.sh: 29: +: not found
/dev/i2c-0
mknod: `/dev/i2c-0': File exists
[/quote]

---

### Post by John.Michael.Kane on 2006-10-31
Here's more info on your particular machine. It would seem lm-sensors is no go on this machine you have.

[http://ubuntuforums.org/showthread.php?t=31147&highlight=i8k](http://ubuntuforums.org/showthread.php?t=31147&highlight=i8k)
[http://ubuntuforums.org/showthread.php?t=228243&highlight=i8k](http://ubuntuforums.org/showthread.php?t=228243&highlight=i8k)
[http://ubuntuforums.org/showthread.php?t=257684&highlight=i8k](http://ubuntuforums.org/showthread.php?t=257684&highlight=i8k)
[http://ubuntuforums.org/showthread.php?t=251741&page=2&highlight=i8k](http://ubuntuforums.org/showthread.php?t=251741&page=2&highlight=i8k)

---

### Post by AsGF2MX on 2006-10-31
Well, I managed to get the GPU readings after installing the nvidia official drivers. The screwy part is that I can get the readings now how do I get the fan trip points to work properly? ](*,) 

GKrellm...I've come across gi8k too but I can't quite get GAI (General Applet Interface) to work properly but it may be the last option.

GKrellm doesn't seem to work too well w.r.t to the GPU fan. I also noticed a mix up of left and right but it's 12:30AM at the moment, I'll try in the morning.

---

