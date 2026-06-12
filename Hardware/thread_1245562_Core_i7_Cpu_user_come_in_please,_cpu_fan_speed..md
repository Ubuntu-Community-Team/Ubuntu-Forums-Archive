---
title: "Core i7 Cpu user come in please, cpu fan speed."
date: 2009-08-20
forum: Hardware
---

### Post by yingwuzhao on 2009-08-20
Hi, everyone, I have this new computer:
 

Core i7 920 D0 stepping @ 2.66Ghz stock speed
ASUS P6T Mobo
OCZ Gold PC12800 2Gx3
MSI twin tower OC GTX275
...
I update the BIOS to the latest version, which is 0603. Q-fan enabled.
 

In windows 7 idle, the CPU temp (Tcase) I see in Everest and Speed fan is both about 36C, and fan speed is both reported about 500 - 700 rpm. I can visually confirm the CPU fan is running very slow and the heat sink is cold, so nice.  
 
However, In Linux (Arch), the CPU temp (Tcase) temperature is reported by lm-sensors as 49C (obviously wrong since it is higher than core temp!) and CPU fan is running from 1100 - 1300 rpm. Thus linux runs a lot louder than windows. But when I open the case the cpu heat sink is cold while the fan is running fast for no reason. The CPU fan control is working, but the speed just change only from 1100 rpm up.

**So core i7 users, can you share your experience with this issue? **
**What is your cpu fan speed under ubuntu?**
**Is the CPU fan control works well out of box for your new core i7 ?**
Any info is appreciated thanks a lot.
 
I want to know whether this problem only exist in Archlinux, or it is universal for linux, hopefully it works in ubuntu, then I will be more than happy to switch back home. 

Btw, the Core temps at idle are 42, 39, 41, 40

Update: the issue is solved, see my last post, the solution is blacklisting: asus_atk0110, instead use w83667hg.
Cheers.

---

### Post by yingwuzhao on 2009-08-27
WTF, nobody in ubuntu forum is using core i7 cpu?

Come on, guys, this issue is basically confirmed with Arch linux, the cpu fan is running 500rpm faster in archlinux than in windows under the same idle condition. I want to know whether the cpu fan regulation is working properly in Ubuntu, 

Somebody who has core i7 please report your cpu fan speed, and if you can please compare the speed in ubuntu and in windows.

Thanks a lot.

---

### Post by yingwuzhao on 2009-08-28
wait.....

---

### Post by yingwuzhao on 2009-08-29
....

---

### Post by bear24rw on 2009-08-29
i have an i7 with evga micro mobo. my fan speed and temps report fine, the problem is with the drivers for your mobo not the i7

---

### Post by Yellow Pasque on 2009-08-29
It just sounds like you need to tweak lm-sensors. You can edit /etc/sensors.conf and tweak the raw data values.

---

### Post by yingwuzhao on 2009-08-29
NO, it is NOT.

The fan is physically running much faster, I can hear it and see it if I open the case. In windows 7, it is running very leisurely, while in arch linux it is running like crazy.

This problems has been confirmed by another Arch linux users, whose fan is running about 500rpm faster in linux than in windows. 

Now my question is that whether or not this problem exist in Ubuntu? 

If there is any core i7 user, I would very much like hear about your experience, what is your cpu fan speed in ubuntu under idle, and if you happen to have a dual boot, what is it under windows? and what is it in BIOS?

Thanks a lot.

---

### Post by Yellow Pasque on 2009-08-29
..but it sounds like your sensor chip is reporting bad values. Have you tried editing /etc/sensors.conf and offsetting the raw values?

---

### Post by yingwuzhao on 2009-08-30
bear24rw, thanks. 

My mobo is Asus p6t, is this a common problem with this mobo?

Do you know is there a good driver for this mobo?

Thanks a lot.

---

### Post by yingwuzhao on 2009-08-30
By the way, I surely tried to Google about his issue, until now, I have seen numerous core i7 linux users posting their lm-sensors output, without one exception, they ALL have very high CPU fan speed, normally more than 1300rpm. Well, they simply don't know their fan is running to fast!!

This is terrible, for people who absolutely appreciate the golden quietness.


Why the hell Windows 7 manage the CPU fan speed much better? 

P.S. Right now, I am under windows 7 typing, the cpu fan is about 600rpm compared to the 1200rpm in my Archlinux.

Damn!!~

---

### Post by yingwuzhao on 2009-09-03
Do you guys think it is related to BIOS? 

I mean should I contact ASUS for solution or wait for better support from linux, waiting it to catch up ?

Any suggestion?

---

### Post by yingwuzhao on 2009-09-03
By the way,

Where should I file this issue? to kernel developing groups or who else? 


thansk

---

### Post by earthpigg on 2009-09-03
posting here so i can find this thread later.

will finish assembly of my new i7 computer over the next few days, will report back with any issues.

---

### Post by yingwuzhao on 2009-09-05
Great, earthpigg. 

Please include your hardware configuration, most importantly I guess is the mobo. 

I hope for good news from you :)

best

---

### Post by bear24rw on 2009-09-05
After a few updates 'sensors' no longer picks up half the sensors it used to, including fan speed :(

(im on evga x58 micro mobo)

---

### Post by yingwuzhao on 2009-09-05
Oh, really? that's weird.

But you don't really need the lm-sensors to tell the huge cpu fan speed difference under idle in linux and windows-7, in my case, I easily hear/see the difference :(

Until now, I still have no clue where should I file the issue: the right people who is supposed to make this work.

---

### Post by Yellow Pasque on 2009-09-05
Try slowing your fan down with 'pwmconfig'

---

### Post by yingwuzhao on 2009-09-05
Is there any core i7 user get the fan slow down by doing that? 
I definitely tried it before I even think of posting the issue. 

It does NOT work. And I tried to mess up with the configuration file, no work. I know someone slow the fan down by relate another non-cpu temp to the fan control by editing the configuration file.

That is way too "dirty" and dangerous, which I don't consider a solution.

---

### Post by earthpigg on 2009-09-06
> **bear24rw said:**
> After a few updates 'sensors' no longer picks up half the sensors it used to, including fan speed :(

(im on evga x58 micro mobo)

lm-sensors does not work for me in Ubuntu, either, though i havent played with it much. (not at home right now, so cant test right now)

didn't want to invest to much time as i only installed ubuntu as a proof-of-concept to see if the computer was assembled correctly.... Arch will be the eventual distro on that machine.

mobo is an ASUS "P6T Deluxe V2".

manually slowing down the fan speed - without lm-sensors working - doesn't sound smart. 

my *guess* (i'd love to be proven wrong) is just that lm-sensors does not yet work with i7 mobos/cpus. has anyone tried ubuntu 9.10 alpha? or a rolling release distro, yet?

In the Ubuntu world, we may need to wait for 9.10 or need to find/use an lm-sensors PPA.

the bug report, if it needs to be filed, would be on launchpad and sourceforge. launchpad for Ubuntu (with lm-sensors as the 'package hint', and sourceforge for the upstream lm-sensors devs. (im assuming sourceforge is where lm-sensors devs hang out. could be wrong.)

edit: note these google results - [http://www.google.com/search?q=i7+lm-sensors](http://www.google.com/search?q=i7+lm-sensors)

---

### Post by bear24rw on 2009-09-06
Im on Karmic right now like i said lm-sensors was working great and detecting a ton of temps and fan speeds on my board but on of the updates broke it, hopefully they fix the regression

---

### Post by yingwuzhao on 2009-09-06
so how about the cpu fan speed, is it working normally? not over spinning anymore?

I heard people who run core i7 on a msi mobo have cpu fan speed running normally (600rpm in sythe mugen, the same performance as in windows) in archlinux. 

So I suspect that it may be a issue only concerns ASUS 1366 mobos.

---

### Post by earthpigg on 2009-09-07
well, i never did get lm-sensors working with ubuntu.

but, here it is with arch on an ASUS mobo:

```
[chris@chris-desktop ~]$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +0.94 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.26 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.17 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.31 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     **_1962_** RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS3 FAN Speed:**_1318_** RPM  (min =  600 RPM)
POWER FAN Speed:   **_1939_** RPM  (min =    0 RPM)
CPU Temperature:    +43.0°C  (high = +60.0°C, crit = +75.0°C)  
MB Temperature:     +40.0°C  (high = +45.0°C, crit = +75.0°C)  
[chris@chris-desktop ~]$
```

---

### Post by yingwuzhao on 2009-09-08
1962 ?? man that was absurd. 

You might want to open the case and look/hear the cpu fan yourself, if the sensors are reporting something wrong. Otherwise, you fan is much crazier than mine, I bet it is very noisy!

Compare to the speed/sound of it in windows-7 you will know what I am talking about.

---

### Post by ElSlunko on 2009-09-08
I haven't found too much issue running 9.04 but I haven't looked for it. I'll poke around my setup and report back any results later this week. I'm on evga SLI mobo btw.

---

### Post by yingwuzhao on 2009-09-08
elslunko, great, 

if you can, please compare the cpu fan speed difference in Windows and linux.
Thanks.

---

### Post by 7x1x on 2009-09-14
Hi, I have an AMD Turion 64 x2 TL-58 1.9Ghz. It was runnig fine in ubuntu and win7, however started cooking in arch linux 70-80 degress at 2-5% cpu usage.

I installed cpufreq and temperatures dramaticaly dropped. have a look at:
[http://wiki.archlinux.org/index.php/CPU_Frequency_Scaling](http://wiki.archlinux.org/index.php/CPU_Frequency_Scaling)

Hope this helps.

---

### Post by yingwuzhao on 2009-10-01
Hi, guys, finally I got some time to carefully investigate this matter. This problem happens only for ASUS mobo owner, and the problem is rooted in the ASUS motherboard driver: 
```
asus_atk0110
```
which is loaded automatically ( I guess by udev), this driver provides wrong CPU diode temp, thus force the fan spin almost twice than necessary. In some cases, it even shutdown your computer due the extremely wrong high temp. 

Thus solution is of cource to blacklist this thing, if you use arch, you can do so in your MODULES in /etc/rc.conf, in ubuntu it should be something similar. Then instead load 
```
w83667hg
```
trhough lm_sensors, this way, you will have an accurate CPU diode temperature, and your CPU fan should run normally now. 

Cheers!

---

### Post by earthpigg on 2009-10-01
yingwuzhao,

have you filed a bug report with [Ubuntu]("https://launchpad.net/ubuntu") and/or [Arch]("http://bugs.archlinux.org/")? you seem the most familiar with the problem, so you would be the right person for that job.

---

### Post by yingwuzhao on 2009-10-01
Not yet, but I send email to the lm_sensors mailing list, and the guy who develop asus_atk0110, asking for more information. You can find my message I posted today there.

---

### Post by Syncan on 2009-10-05
> **yingwuzhao said:**
> Hi, guys, finally I got some time to carefully investigate this matter. This problem happens only for ASUS mobo owner, and the problem is rooted in the ASUS motherboard driver: 
```
asus_atk0110
```which is loaded automatically ( I guess by udev), this driver provides wrong CPU diode temp, thus force the fan spin almost twice than necessary. In some cases, it even shutdown your computer due the extremely wrong high temp. 

Thus solution is of cource to blacklist this thing, if you use arch, you can do so in your MODULES in /etc/rc.conf, in ubuntu it should be something similar. Then instead load 
```
w83667hg
```trhough lm_sensors, this way, you will have an accurate CPU diode temperature, and your CPU fan should run normally now. 

Cheers!
I have the same problem and I have an ASUS P5B-E Mobo.
As I am an absolute beginner in Linux I like to know how I can solve it, using your method.
Please can you ( or somebody else ) explain me in more detail what to do to fix it?

---

### Post by iTrascurato on 2009-10-05
I will let you know after tonight when I build my Core i7 machine how the fan speeds work.

I am going to be using a DFI DK X58-T3EH6 ([like I posted here]("http://ubuntuforums.org/showthread.php?t=1283229"))

Does anybody else have that motherboard?  I want to know if I am going to have any issues.

---

### Post by yingwuzhao on 2009-10-06
Sure, as I said in the previous post, you need to disable the "asus_atk0110", and the lm_sensors should automatically load the right driver, in my case the "w83667hg", in your case may be slightly differently.

So all you need to do is searching/asking people here how to correctly disable a modules from loading at startup. Since I am using Archlinux, it is a little different, but should be similar, like putting asus_atk0110 in the blacklist or something. 

best

---

### Post by abonnema on 2010-01-02
> **yingwuzhao said:**
> By the way, I surely tried to Google about his issue, until now, I have seen numerous core i7 linux users posting their lm-sensors output, without one exception, they ALL have very high CPU fan speed, normally more than 1300rpm. Well, they simply don't know their fan is running to fast!!

This is terrible, for people who absolutely appreciate the golden quietness.


Why the hell Windows 7 manage the CPU fan speed much better? 

P.S. Right now, I am under windows 7 typing, the cpu fan is about 600rpm compared to the 1200rpm in my Archlinux.

Damn!!~

Hi yingwuzhao,

I am really grateful for your posts, as this was the main reason (plus the guy who found this for me), that I discovered how it works.

I was pointed out this thread from a Fedora forum. I have almost the same mobo as you do and exactly the same CPU:

CPU7: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
ASUS P6T SE
AMI BIOS

Anyway, I reply, because the readings I get are very reasonable and when checking these with W7, I get the same readings from Windows. So has this been changed? Can you confirm?

The readings I got from sensors are (and are equal to W7 readings):

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +0.94 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.28 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.00 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.19 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      691 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed: 629 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM)
CPU Temperature:    +37.0°C  (high = +60.0°C, crit = +75.0°C)  
MB Temperature:     +32.0°C  (high = +45.0°C, crit = +75.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +33.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +27.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +30.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +30.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +33.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +27.0°C  (high = +80.0°C, crit = +100.0°C)  

From W7 I use the ASUS utiliity E6X or something (windows only).

The readings I get here, conincide with the readings in the W7 "normal"  mode, which is called "high performance" . There are 2 higher levels (without overclocking) and there iare 2 lower levels. The lowest level is called "Max Energy Saving"  mode. 

Using the  lowest "max energy saving"  mode, I get significantly less noise, because the main FAN is shut down. I assume when putting on a heavier load it will switch on again :)
So all I need to do now, is figure out, how I can get Linux to use the "max saving mode" when the load is light, and automatically switch up, when the load is heavier.

Hopefully you can also confirm that the driver is now ok for your motherboard.

---

### Post by iTrascurato on 2010-01-02
I have the same CPU and motherboard as you.  I haven't notice excessive noise.  If I do, I click the "Volume Up" button three times.

:popcorn::popcorn::guitar::guitar:

---

### Post by emma_peel on 2010-02-16
> **yingwuzhao said:**
> Sure, as I said in the previous post, you need to disable the "asus_atk0110", and the lm_sensors should automatically load the right driver, in my case the "w83667hg", in your case may be slightly differently.

So all you need to do is searching/asking people here how to correctly disable a modules from loading at startup. Since I am using Archlinux, it is a little different, but should be similar, like putting asus_atk0110 in the blacklist or something. 

best

Hello.

I'm facing exactly the same issue ... does anybody found the way to activate the module w83667hg ? I have blacklisted the asus_atk0110, but the only result is that sensors can no longer reader the readings.

Moreover, do we have to update the firmware of the mobo ? What is the detail configuration of the BIOS ?

Thank you all in advance for your explanations.

---

### Post by GSF1200S on 2010-03-29
> **emma_peel said:**
> Hello.

I'm facing exactly the same issue ... does anybody found the way to activate the module w83667hg ? I have blacklisted the asus_atk0110, but the only result is that sensors can no longer reader the readings.

Moreover, do we have to update the firmware of the mobo ? What is the detail configuration of the BIOS ?

Thank you all in advance for your explanations.

Well, I too have had some issues here. I now have the w83667hg working, but with mixed results. I blacklisted the asus_atk0110 module and attempted to modprobe w83667hg, but I got a message like:
```
w83627ehf.ko: Device or resource busy
```
Yes, when you run sensors-detect, you will notice that w83627ehf is the module name for w83667hg. I cant give you the exact error, as its now loading with the changes I made.

I did, however, figure out how to get the module to load. First, ensure that asus_atk0110 is blacklisted by adding the module and a brief description to:
```
/etc/modprobe.d/blacklist.conf
```

Then, edit the /etc/default/grub file as root:
```
sudo gedit /etc/default/grub
```
Go down to the line that says:
```
GRUB_CMDLINE_LINUX=""
```
and change it to:
```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
```

Now, edit the file /etc/modules as root:
```
sudo gedit /etc/modules
```
and add the w83627ehf module to the file. Of course, you might want to ensure the coretemp module is in there as well. This is what mine looks like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
w83627ehf
coretemp
```

Restart the computer, and you're done. As I said, its a mixed set of results. My CPU fan speed under the asus_atk0110 never dropped below 1300rpm, while for some reason with this module it runs at 900 to 1000 rpms. The computer is notably quieter, and coretemp shows my cores sitting in the high 40s (I really need a TRUE for this cpu..) However, the rest of the output is garbage. This is the output from sensors minus coretemp's output:
```
[poeticrpm@geekdom ~]$ sensors
w83667hg-isa-0290
Adapter: ISA adapter
in0:         +0.98 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.73 V  (min =  +0.51 V, max =  +1.66 V)   ALARM
in2:         +3.31 V  (min =  +1.02 V, max =  +0.05 V)   ALARM
in3:         +3.28 V  (min =  +2.34 V, max =  +2.45 V)   ALARM
in4:         +1.62 V  (min =  +0.79 V, max =  +0.13 V)   ALARM
in5:         +2.04 V  (min =  +1.02 V, max =  +1.03 V)   ALARM
in7:         +3.41 V  (min =  +3.09 V, max =  +0.02 V)   ALARM
in8:         +3.31 V  (min =  +1.74 V, max =  +2.34 V)   ALARM
fan1:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan2:       1081 RPM  (min =  577 RPM, div = 16)
fan3:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:       +38.0°C  (high = +32.0°C, hyst = +48.0°C)  ALARM  sensor = thermistor
temp2:       +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       -13.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

```

Fan2 must be my CPU fan, and I have no less than 6 other fans on this case, yet none of them register. I dont even know what the voltages mean. Under the asus_atk0110 module, everything was labeled and made perfect sense, although the cpu temp was roughly the same as coretemp, which seems too high. Im pretty sure the above is telling me my cpu is at 38 degrees, which is pretty much perfect.

Give the above a try and report back here- Id be interested to hear what everyone elses results are.

Motherboard: Asus Rampage II Extreme w/ i7 920

---

### Post by Mark620 on 2010-04-03
I got the same thing:
```

w83667hg-isa-0290
Adapter: ISA adapter
in0:         +1.22 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.74 V  (min =  +0.29 V, max =  +1.06 V)   ALARM
in2:         +3.38 V  (min =  +0.77 V, max =  +1.50 V)   ALARM
in3:         +3.34 V  (min =  +0.06 V, max =  +2.78 V)   ALARM
in4:         +1.72 V  (min =  +0.51 V, max =  +0.70 V)   ALARM
in5:         +2.04 V  (min =  +1.78 V, max =  +0.98 V)   ALARM
in7:         +3.42 V  (min =  +0.78 V, max =  +3.66 V)   
in8:         +3.28 V  (min =  +2.38 V, max =  +2.29 V)   ALARM
fan1:       4687 RPM  (min = 3443 RPM, div = 8)
fan2:       1622 RPM  (min = 2556 RPM, div = 16)  ALARM
fan3:       1412 RPM  (min = 337500 RPM, div = 4)  ALARM
fan4:       1654 RPM  (min = 1035 RPM, div = 8)
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:       +35.0°C  (high = +47.0°C, hyst = +116.0°C)  sensor = thermistor
temp2:       +61.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +2.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.950 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +64.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +63.0°C  (high = +80.0°C, crit = +100.0°C)  


```
THANKS for the in-depth instructions GSF1200S! I give it: :KS:KS:KS:KS:KS
It may not be exact but it helps.

P6T, i7-920 oc to 3.8 GHZ Bclock = 190 on 1.225 V-core(Std setting for chip!)
Core temp above are while folding bigadv:
Folding@Home Client Version 6.29
Executable: ./fah6
Arguments: -bigadv -smp 8 -verbosity 9

---

### Post by gjoellee on 2010-04-03
I experienced the same with all Linux distros I have tried....the fan is going crazy!

---

### Post by GSF1200S on 2010-04-04
> **Mark620 said:**
> I got the same thing:
```

w83667hg-isa-0290
Adapter: ISA adapter
in0:         +1.22 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.74 V  (min =  +0.29 V, max =  +1.06 V)   ALARM
in2:         +3.38 V  (min =  +0.77 V, max =  +1.50 V)   ALARM
in3:         +3.34 V  (min =  +0.06 V, max =  +2.78 V)   ALARM
in4:         +1.72 V  (min =  +0.51 V, max =  +0.70 V)   ALARM
in5:         +2.04 V  (min =  +1.78 V, max =  +0.98 V)   ALARM
in7:         +3.42 V  (min =  +0.78 V, max =  +3.66 V)   
in8:         +3.28 V  (min =  +2.38 V, max =  +2.29 V)   ALARM
fan1:       4687 RPM  (min = 3443 RPM, div = 8)
fan2:       1622 RPM  (min = 2556 RPM, div = 16)  ALARM
fan3:       1412 RPM  (min = 337500 RPM, div = 4)  ALARM
fan4:       1654 RPM  (min = 1035 RPM, div = 8)
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:       +35.0°C  (high = +47.0°C, hyst = +116.0°C)  sensor = thermistor
temp2:       +61.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +2.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.950 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +64.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +69.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +63.0°C  (high = +80.0°C, crit = +100.0°C)  


```
THANKS for the in-depth instructions GSF1200S! I give it: :KS:KS:KS:KS:KS
It may not be exact but it helps.

P6T, i7-920 oc to 3.8 GHZ Bclock = 190 on 1.225 V-core(Std setting for chip!)
Core temp above are while folding bigadv:
Folding@Home Client Version 6.29
Executable: ./fah6
Arguments: -bigadv -smp 8 -verbosity 9

Eh, yeah looking back at it I could have been a little more specific. I ended up going back to the asusatk0110 module. For reference, heres what sensors shows now:
```
[poeticrpm@geekdom ~]$ sensors
atk0110-acpi-0
Adapter: ACPI interface
3.3V Voltage:          +3.28 V  (min =  +2.97 V, max =  +3.63 V)
5V Voltage:            +4.85 V  (min =  +4.50 V, max =  +5.50 V)
12V Voltage:          +12.14 V  (min = +10.20 V, max = +13.80 V)
CPU Voltage:           +1.12 V  (min =  +0.80 V, max =  +1.80 V)
CPU PLL Voltage:       +1.82 V  (min =  +1.50 V, max =  +2.00 V)
QPI/DRAM Core Voltage: +1.32 V  (min =  +0.80 V, max =  +1.50 V)
IOH Voltage:           +1.14 V  (min =  +0.90 V, max =  +1.35 V)
IOH PCIE Voltage:      +1.51 V  (min =  +1.20 V, max =  +1.80 V)
ICH Voltage:           +1.12 V  (min =  +0.90 V, max =  +1.35 V)
ICH PCIE Voltage:      +1.51 V  (min =  +1.20 V, max =  +1.80 V)
DRAM Bus Voltage:      +1.65 V  (min =  +1.40 V, max =  +1.90 V)
CPU FAN Speed:        1044 RPM  (min =  600 RPM)
CHA_FAN1 FAN Speed:   1357 RPM  (min =  600 RPM)
CHA_FAN2 FAN Speed:   1407 RPM  (min =  600 RPM)
CHA_FAN3 FAN Speed:   1299 RPM  (min =  600 RPM)
PWR_FAN FAN Speed:    1013 RPM  (min =  600 RPM)
OPT_FAN1 FAN Speed:    995 RPM  (min =  600 RPM)
OPT_FAN2 FAN Speed:      0 RPM  (min =  600 RPM)
OPT_FAN3 FAN Speed:   1061 RPM  (min =  600 RPM)
CPU Temperature:       +38.0°C  (high = +60.0°C, crit = +65.0°C)  
MB Temperature:        +35.0°C  (high = +45.0°C, crit = +55.0°C)  
SB Temperature:        +52.0°C  (high = +65.0°C, crit = +65.0°C)  
NB Temperature:        +52.0°C  (high = +80.0°C, crit = +80.0°C)  
OPT_FAN1 Temperature:   +0.0°C  (high = +45.0°C, crit = +45.0°C)  
OPT_FAN2 Temperature:   +0.0°C  (high = +45.0°C, crit = +45.0°C)  
OPT_FAN3 Temperature:   +0.0°C  (high = +45.0°C, crit = +45.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +53.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +53.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +55.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 4:      +53.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 5:      +53.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 6:      +53.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 7:      +56.0°C  (high = +80.0°C, crit = +100.0°C)  


```

For some reason, the fan is spinning down at 1000rpms now, and I dont know why. I have dynamic fan control being handled by the motherboard and im running the latest stable release from lm-sensors homepage. Make sure to check out the install text in the tarball to ensure you have all the necessary dependencies to install it.

---

