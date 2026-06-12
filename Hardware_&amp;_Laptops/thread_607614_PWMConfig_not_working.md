---
title: "PWMConfig not working"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by azenz on 2007-11-09
I set up lm-sensors and get correct temperature and fan readings. Now when I type "pwmconfig" to use fancontrol I get:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

This error seems common and I wonder if this can be fixed under Gutsy Gibbon? There are other posts on this and some of the solutions offered don't seem to apply to my version of pwmconfig (e.g. the script fix).

---

### Post by Daelyn on 2007-11-09
> **azenz said:**
> I set up lm-sensors and get correct temperature and fan readings. Now when I type "pwmconfig" to use fancontrol I get:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

This error seems common and I wonder if this can be fixed under Gutsy Gibbon? There are other posts on this and some of the solutions offered don't seem to apply to my version of pwmconfig (e.g. the script fix).

Have you done a 
```
sudo sensors-detect 
``` 
to detect the sensors?

---

### Post by longman on 2007-11-11
I have the same problem.
I have executed ```
sudo sensors-detect
``` and then ```
sensors
``` but the response looks like this:
```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (crit = +100.0°C)                  
coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (crit = +100.0°C)
```
and no information about fans and voltages.
Sensors-detect only found coretemp module. 

Actually the problem for me is the annoying fan noise, spinning constantly, even when the processor is cool enough... I have tried pwmconfig, but ```
sudo pwmconfig
``` says that ```
/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
Any idea if this can be fixed somehow?

---

### Post by azenz on 2007-11-11
Yes I did run sensors-config and sensors output shows temps and fan speed, which I have displayed using ksensors. That all works, only pwmconfig doesn't.

---

### Post by Centie on 2007-11-29
I had a similar problem, and fixed as below..

[http://ubuntuforums.org/showpost.php?p=3046745&postcount=17]("http://ubuntuforums.org/showpost.php?p=3046745&postcount=17")

Can't guarantee it will work/apply for you, but good luck.

---

### Post by Yellow Pasque on 2007-11-29
1) What mobo do you folks have? Not all boards have PWM support and some just have it on the CPU fan header. Also, if your board is using a newer or less popular sensor chip, you might have to wait for the 2.6.24 kernel to get a kernel module for it. Personally, that's where I'm at right now.
2) Have you disabled the BIOS fan control?

---

### Post by flomar on 2007-11-30
Hi there!

im having a similar problem with the fancontrol unter Gutsy Gibbon. 
Status: (afer installing lmsensors after[ this german guide]("http://wiki.ubuntuusers.de/Lm_sensors") and pwmconfig after [that]("http://wiki.ubuntuusers.de/L%C3%BCftersteuerung") one from ubuntuusers.de. they are very alike yours on ubuntuforums.org)
```
florian@leda:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38°C  (high =  +100°C)
```and
```
florian@leda:~$ sudo pwmconfig
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
> 1) What mobo do you folks have?Its a MSI P6N SLI with nForce 650i chipset and im pretty sure it supports PWN as well es my cooler which is plugged in with a 4-pin cable.> 2) Have you disabled the BIOS fan control?Yes, I did disable this option in order to get pwmconfig working. However it does not make a difference in terms of fan speed, always runs full speed.
What makes you think, this issue will be fixed with kernel 2.6.24? More important, what motherboard/chipset do you have? hope it will work for me as well with the new kerne l:)

Thanks, flomar

---

### Post by Yellow Pasque on 2007-11-30
> More important, what motherboard/chipset do you have?
I have an MSI K9AG Neo2, which uses a Fintek F71882 sensor chip, the same as your motherboard.

> What makes you think, this issue will be fixed with kernel 2.6.24?
I looked at the status of the F71882 here: [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by flomar on 2007-12-01
Hi,

indeed that is great news! i hope this kernel version will be ready for the next ubuntu release in april.

i just have one more question; i can understand that the cpu fan is running on full speed because there is no os driver controlling the speed depending on the temperature. however i do not understand whyactivationg  the option for letting the bios control the fan speed makes no difference. possibly a bios update could help?!

cheers, flomar

---

### Post by azenz on 2007-12-10
I have a Shuttle SG33 mobo and that's probably more exotic. I haven't tried disabling bios fan control yet, all I can do in fact is set the fan to a fixed speed (currently it's on smartfan) - that should eliminate bios-control over the fan. So indeed we might have to wait for the new kernel, huh?

I will have a look at that solution ([http://ubuntuforums.org/showpost.php?p=3046745&postcount=17](http://ubuntuforums.org/showpost.php?p=3046745&postcount=17)) once I get back from travels, thanks!

---

### Post by Yellow Pasque on 2007-12-11
Well, Flomar, at this point the F71882 driver doesn't have pwm in it yet.

I just built my own kernel from the 2.6.24rc4 source and the included module wouldn't build, nor could I get it to build manually. I had to download a separate copy. The good news is that I was able to get the module to build on the current kernel and I now have temp/Voltage/fan speed monitoring.

For those interested, I'll give the procedure I used (derived from [http://forums.gentoo.org/viewtopic-t-567986.html](http://forums.gentoo.org/viewtopic-t-567986.html))

First, I downloaded the latest version of lm-sensors [here](ftp://ftp.netroedge.com/pub/lm-sensors/lm_sensors-3.0.0.tar.bz2)
Next, I removed the current version of lm-sensors and installed packages needed. sensors-applet and hddtemp are optional. The former gives you a nifty sensor readout that you can add to any GNOME Panel. The latter is used to monitor disk temps and also works with sensors-applet to give you a readout on your HD temp alongside the other sensors.
```
sudo apt-get remove lm-sensors
sudo apt-get install curl libsensors3 libsensors-dev libsysfs2 libsysfs-dev bison flex make build-essential hddtemp sensors-applet
```
Extract the lm-sensors folder to your home dir. Now open up the folder and gedit Makefile. On line 42, remove the /local from the end of the line. Now you can:
```
make
sudo make install
```
Now, get the f71882 files and build it:
```
cd /usr/src; sudo mkdir fintek-devel; cd fintek-devel
curl http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20070624/4fef1169/attachment-0003.obj > fintek71882.c
curl http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20070624/4fef1169/attachment-0004.obj > sensors.conf
curl http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20070624/4fef1169/attachment-0005.obj > Makefile
make 
```

Now, we have the kernel module, so let's move it to the proper place:
```
sudo mv fintek71882.ko /lib/modules/`uname -r`/kernel/drivers/hwmon/f71882fg.ko
```

We also need to make sure it loads at boot. My solution to this problem was to put the following line in the /etc/init.d/lm-sensors script, right after the initial comments (line 11):
```
insmod /lib/modules/`uname -r`/kernel/drivers/hwmon/f71882fg.ko
```

---

### Post by flomar on 2008-01-25
> **Temüjin said:**
> Also, if your board is using a newer or less popular sensor chip, you might have to wait for the 2.6.24 kernel to get a kernel module for it. Personally, that's where I'm at right now.The 2.6.24 kernel has just been released! :)  -> [http://www.kernel.org/]("http://www.kernel.org/")

Anybody already tested it?

cheers, flomar

---

### Post by flomar on 2008-04-19
Hey,

the Hardy Heron Release Candidate has been released. Reason enough to test out the new kernel (2.6.24) that is supposed to support my pwm chip F71882 (see previous posts).
after the dist-upgrad i finally got all the information i wanted:
```
florian@leda:~$ sensors
f71882fg-isa-0a00
Adapter: ISA adapter
3.3V:        +3.36 V
Vcore:       +1.15 V  (max =  +2.04 V)   
Vdimm:       +1.70 V
Vchip:       +1.23 V
+5V:         +4.96 V
12V:        +14.68 V
5VSB:        +4.91 V
3VSB:        +3.34 V
Battery:     +3.07 V
CPU:        2463 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +32.0°C  (high = +75.0°C, hyst = +71.0°C)  
                      (crit = +75.0°C, hyst = +71.0°C)  sensor = transistor
System:      +36.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (crit = +100.0°C)
```Unfortunately "sudo pwmconfig" leads to "[..]/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed" again.

cheers, Flo

---

### Post by ningo on 2008-04-23
f71882fg doens't support pwm (yet). Neither in 2.6.24 nor in 2.6.25. You'll have to wait.

---

### Post by flomar on 2008-04-30
> **ningo said:**
> f71882fg doens't support pwm (yet). Neither in 2.6.24 nor in 2.6.25. You'll have to wait.

Thanks ningo,

i will wait ;) Is this again the page were the newest development is to be announced? -> [http://http://lm-sensors.org/wiki/Devices]("http://http://lm-sensors.org/wiki/Devices")

flomar

---

