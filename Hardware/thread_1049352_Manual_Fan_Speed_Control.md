---
title: "Manual Fan Speed Control"
date: 2009-01-24
forum: Hardware
---

### Post by frankelr on 2009-01-24
I would like to be able to change my case and cpu fan speed under manual control.  I installed pwmconfig and started its self-test, it increased the fan speeds to 100% GREAT!, but I was to afaid to let it test the system by turning off the fans and control-Ced out.  I then ran my high load program and found that 100% was what I wanted for this job.  I did not allow pwmconfig to store a config file.  I then went back to windowsXP and tried speedfan, which also worked and allowed the kind of manual control I need.

So I know that the hardware infrastructure is there.  Could someone direct me to a Ubuntu friendly version of speedfan or tell me how to set up manual control of fans via pwmconfig without the scary part of turning off the fans.

thanks

Bob

---

### Post by seldon77 on 2009-12-30
I can do this via the command line -

ie..

#echo 1 > /sys/class/hwmon/hwmon0/device/pwm1_enable
#echo 100 > /sys/class/hwmon/hwmon0/device/pwm1

your device names might be different though, or require a slightly different input

if it works for you, you can make it permanent by putting the commands in a script and running it at each boot from /etc/rc.local

---

