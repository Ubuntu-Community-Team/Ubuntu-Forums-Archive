---
title: "pwmconfig/fancontrol/sysfs no workie workie...Help?"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by seedoubleyou on 2006-06-20
yes, cross-posted from General forum, which I think is too busy with Google-worthy questions like the IRC channel to be useful...

I am trying to get my fans to stop running at full throttle as my family and I are on the cusp of deafness. I have installed fancontrol/pwmconfig/sensors/sensord, however pwmconfig or fancontrol appear to be unable to successfully write to anything under the /sys partition on my Dapper 6.06 LTS partition.

Here is the error output on first running pwmconfig:

Found the following PWM controls:
0-002e/pwm1
/usr/sbin/pwmconfig: line 102: 0-002e/pwm1_enable: Permission denied
0-002e/pwm2
/usr/sbin/pwmconfig: line 102: 0-002e/pwm2_enable: Permission denied
0-002e/pwm3
/usr/sbin/pwmconfig: line 102: 0-002e/pwm3_enable: Permission denied

It would appear nothing is able to modify the files located in SDIR=/sys/bus/i2c/devices , and it would appear DIR=/proc/sys/dev/sensors
doesn't even exist.

'mount' output says that /sys is mounted as sysfs with rw permissions, yet I cannot even modify these files as root user.

any ideas? help?

---

### Post by slider on 2006-07-12
I have the same problem. When trying to modify any files in /sys/bus/i2c/devices I get either "FSync failed" or "Warning: The file has been changed since reading it Do you really want to write to it?". This is with 6.06 Dapper.

Kind of stuck at this point.

On Edit:

I found this thread:

[http://lists.lm-sensors.org/pipermail/lm-sensors/2005-February/010775.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2005-February/010775.html)

So I tried the following:
echo 0 > pwm1_enable
And now get the error
bash: echo: write error: Input/output error

Maybe a sysfs kernel bug or did something change with regard to writing procfs files and pwmconfig just hasn't kept up? Really just guessing here. I'm using kernal 2.6.15-26-686. If anybody could shed some light on this it would be much appreciated.

---

### Post by slider on 2006-07-12
[http://lists.lm-sensors.org/pipermail/lm-sensors/2006-January/015110.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2006-January/015110.html)

---

