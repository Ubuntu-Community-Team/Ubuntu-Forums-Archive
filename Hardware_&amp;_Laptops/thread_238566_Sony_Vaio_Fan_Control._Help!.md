---
title: "Sony Vaio Fan Control. Help!"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by deepgray on 2006-08-17
Hello,

Overall, Ubuntu Dapper has done a great job with my hardware. I am having one aggravating problem though. The power supply (ps) fan is very loud all the time, whereas it idles down quietly after booting into windows. I have a Sony Vaio PCV-RX450 desktop and I understand the sony fan control includes sonyfanc.vxd in windows. My BIOS will display the cpu and ps RPMs and temperatures, but that is all (no control). I have referred to numerous forums and followed the directions as best I could with little success. In particular, I have tried [SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto") and succeeded (I think) with the exception of this message: 
```
sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
```

Besides this, I was able to execute sensors as the guide instructs:
```
sensors
it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.79 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +1.74 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +3.26 V  (min =  +3.14 V, max =  +3.46 V)
+5V:       +5.03 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +11.97 V  (min = +11.39 V, max = +12.61 V)
-12V:     -14.47 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -9.76 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +5.00 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.38 V
fan1:     2766 RPM  (min =    0 RPM, div = 4)
fan2:     5075 RPM  (min = 3000 RPM, div = 2)
fan3:        0 RPM  (min = 3000 RPM, div = 2)
M/B Temp:    +34°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +38°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:       +43°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor

```

and now xsensors, GKrellM and other similar programs can display fan RPM and temperature info. That is something, but there is still the noise.

So I tried this:
```
sudo fancontrol
Loading configuration from /etc/fancontrol ...
grep: /etc/fancontrol: No such file or directory
grep: /etc/fancontrol: No such file or directory
grep: /etc/fancontrol: No such file or directory
grep: /etc/fancontrol: No such file or directory
grep: /etc/fancontrol: No such file or directory
grep: /etc/fancontrol: No such file or directory
grep: /etc/fancontrol: No such file or directory
Some mandatory settings missing, please check your config file!
```

And some of this:
```
pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

Finally, typed this in for good measure, to no (apparent) affect:
```
modprobe fan
modprobe thermal

```

I have attacked this problem from every angle I could find, but the fan is still roaring. I'm still confident that this can be fixed though; just let me know what needs to be done!

---

### Post by voltronguy on 2006-08-24
I have the exact same problem, with the 650 model!  It really worries me.  Sorry to say that i know nothing about Linux and jsut installed Kubuntu last night so I won't be much help.

---

### Post by deepgray on 2006-08-26
> **voltronguy said:**
> I have the exact same problem, with the 650 model!  It really worries me.  Sorry to say that i know nothing about Linux and jsut installed Kubuntu last night so I won't be much help.

Well, I've seen this issue mentioned on various forums, so at least we're not alone! I've spent a couple hours on this without much luck though. Please post here if you have any success. I'll do the same.

---

### Post by voltronguy on 2006-08-29
OK, I finally had some success.  I'm going to need to crack my case open to really watch the fans to adjust the pwm values, but it is quieter right now.

I got the same error with lm-sensors as you:
```
sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
```

I think this would be your problem:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
That seems to be the part that will prevent you from running fan control.

I seriously doubt our motherboards are so different that you wouldn't have these sensors.  Perhaps you should look over the lm-sensors install again?

---

### Post by deepgray on 2006-09-10
Well, I still have this fan problem after carefully following the directions; I've tried three or four times now and I don't think I've made any mistakes.

This is the road block:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

However(!), I did find a new clue that might solve the issue for any Ubuntu users more knowledgable than me. When booting into "recovery" from GRUB I just noticed this message:

```
it87-isa detected broken BIOS defaults, disabling PWM interface
```

So if anyone knows how to unbreak my BIOS defaults or enable the PWM interface I would be grateful. I just wanted to add this piece of information for anyone that has the same issue or anyone who might be able to help me. Thank you.

---

### Post by LoverBoyz on 2006-10-28
I am having the same problem as you guys. I installed ubuntu 2 days ago and this fan noise is killing me. I am running pcv-rx450 too.kernel 2.6.15-26-386
Somebody please help us.

---

### Post by rickprather on 2006-11-07
Well, if any of you find the answer to this let me know.

I just installed ubuntu on my Vaio and have the same "start up" fan speed.

It is way more fan than I want and I will have to minimize my use until we find a solution.

Rick
Sony Vaio 
Intel iMac
MacBook

---

### Post by robgill on 2006-11-07
I have a Sony VAIO FS-640

but my fan never runs (simple install no changes/sensors) and I'm afraid I'll overheat sometime.  

My laptop gets  warm on the bottom, but I don't know how standard that is because this is my first laptop.  For those of you whose fan runs always does your laptop get warm on the bottom? 

I may try setting up these sensors to see what the internal temperature is.  Any advice is apreciated.

---

### Post by robgill on 2006-11-08
I can get sensor readings with conky and not lm-sensors.

My cpu temp is ~55C, seems to me that the fan should come on but it doesn't?

Any ideas?

---

### Post by mirkov on 2007-01-07
> **deepgray said:**
> 
```
it87-isa detected broken BIOS defaults, disabling PWM interface
```

So if anyone knows how to unbreak my BIOS defaults or enable the PWM interface I would be grateful. I just wanted to add this piece of information for anyone that has the same issue or anyone who might be able to help me. Thank you.

try loading it87 with the following parameter

```
sudo modprobe it87 fix_pwm_polarity=1
```

---

### Post by virtualXTC on 2007-02-18
I have a solution that was posted here:
[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)

install package: lm-sensors
run: sensors-detect (answered "yes" to all of their questions)
run: pwmconfig
to set the preferences
you can try to run fancontrol at this point as root to see if it is working.

Finally add
/usr/sbin/fancontrol &
to /etc/rc.local

---

### Post by remotedevice on 2007-02-21
Did the add to rc.local fix work for anyone? Not me...

---

### Post by virtualXTC on 2007-03-04
you may be required to set execution bit of rc.local for it to execute on boot:

sudo chmod 755 /etc/rc.local

---

### Post by pball on 2007-04-20
I have just installed v 6.10 on a Sony RX550
Same problem with "roaring fan"
It starts same way in Windows, but
then slows down after boot
Does not slow down on 6.10

I do  not see that anyone has solved problem

pball

---

### Post by starfry on 2007-05-23
Hi, I have the same problem but I am not on a Vaio. This is on Feisty.

I can get sensor output:

```

dual:~$ sensors
as99127f-i2c-0-2d
Adapter: SMBus Via Pro adapter at e800
VCore 1:   +1.73 V  (min =  +1.54 V, max =  +1.95 V)              
VCore 2:   +1.73 V  (min =  +1.54 V, max =  +1.95 V)              
+3.3V:     +3.33 V  (min =  +2.96 V, max =  +3.63 V)              
+5V:       +4.95 V  (min =  +4.49 V, max =  +5.51 V)              
+12V:     +11.92 V  (min =  +9.55 V, max = +14.41 V)              
-12V:      -2.10 V  (min =  -4.07 V, max =  -0.32 V)              
-5V:       -1.13 V  (min =  -1.76 V, max =  -0.82 V)              
fan1:     4530 RPM  (min =   -1 RPM, div = 2)                     
fan2:     4687 RPM  (min = 56250 RPM, div = 8)                     
fan3:        0 RPM  (min = 7031 RPM, div = 2)                     
M/B Temp:    +41°C  (high =   +70°C, hyst =   -32°C)          
CPU Temp:  +39.0°C  (high =   +67°C, hyst =   +60°C)          
temp3:     +40.0°C  (high =   +67°C, hyst =   +60°C)          
vid:      +1.750 V  (VRM Version 8.2)
alarms:   
beep_enable:
          Sound alarm enabled

dual:~$ 


```

When I run pwmconfig, I get
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

Short of getting ear protectors I am going to have to go back to XtraPainful if I can't resolve this soon. I fear the title of this thread may stop non-vaio people responding to what is a problem not limited to Vaios.

Help, anyone?

---

### Post by kgantzer on 2007-07-16
I have Sony Vaio PCV-RX641 - same problem - MAJOR issue.  I know nothing about Ubuntu, Linux or Unix, but I loaded it and everything else works great.  Still need a fix for the Roaring Fan.:confused:

---

### Post by Centie on 2007-07-19
I'm not on a Vaio but had a similar problem with pwmconfig displaying ```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed  
```
I've used SpeedFan successfully under windows so knew this not to be true. I found a solution to fix this (on the lm-sensors mailing list) and as my motherboard uses the it87 sensor chip, as it appears the Vaio does, maybe the solution I found will work for others too:

First check if you have the same problem, by running from a terminal ```
dmesg | grep it87 
```
This should give you two lines, the second one saying something like
```
it87-isa detected broken BIOS defaults, disabling PWM interface
```

To fix this, edit the /etc/modprobe.d/options file, and add this line to the end ```
options it87 fix_pwm_polarity=1 
```

Finally reboot the system, and run the dmesg command as before, which should hopefully now return something like
```
it87-isa 9191-0290: Reconfiguring PWM to active high polarity
```

You should now be able to run pwmconfig without any problems.

---

### Post by deepgray on 2007-09-19
Everyone,

I had given up on running Ubuntu on my Sony Vaio for about four months because of this fan issue, but after coming back here in April, I found mirkov had posted a solution that worked for me. The key piece of voodoo needed was loading the it87 module with:
```
sudo modprobe it87 fix_pwm_polarity=1
```Of course, I can't guarantee this will work for everyone with this fan issue, let alone all Vaio's, but I thought I should mention that this worked for me. Thanks, mirkov.

So in summary, I just followed the directions at [SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto") and IIRC, sensors-detect will prompt you to add some modules to /etc/modules. I just made sure the fix also appears in /etc/modules, so the relevant section of the file looks like:
```
# Generated by sensors-detect on Fri Apr  6 20:07:13 2007
...
it87 fix_pwm_polarity=1

```I should mention that Centie's detailed post looks like a fix as well; he adds the option to /etc/modprobe.d/options instead. I'm pretty sure (based on the man pages for modules and modprobe.d) that this has the same effect, though I haven't tried it.

I've attached my /etc/fancontrol file which I've been running with for a few months now with no problems (I had to append .txt to upload it, but it does NOT use this extension). It keeps things cool and is very quiet with my Sony Vaio PCV-RX450 desktop, but results may vary.

I'd like to mark this thread as solved, but I've noticed many people with the same issue have gathered here. Is anyone still having this issue? Have you tried the fix_pwm_polarity=1?

---

### Post by grendel38 on 2007-09-20
> OK, I finally had some success.  I'm going to need to crack my case open to really watch the fans to adjust the pwm values, but it is quieter right now.

I got the same error with lm-sensors as you:
```
sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
```

I think this would be your problem:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
That seems to be the part that will prevent you from running fan control.

i have a Sony Vaio PCV-RX640 desktop , and after much frustration and tinkering finally got the fan speed under control.  lm-sensors will not work out of the box so to speak.  I followed the directions here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")

it's a large document -- look for the section called "how to detect cpu temperature" and the one immediately following, "how to control fan speed"

you might have to do some tweaking with the values, it worked for me.

good luck

---

