---
title: "Sensors not all working"
date: 2015-07-10
forum: Hardware
---

### Post by john409 on 2015-07-10
I have tried to get them working without asking for help.

I can see a couple of my sensors on my motherboard using "sensors" but not all. Many are not even detected.

I have run lm-sensors then restarted. I have also tried the "/etc/init.dkmod start" command without success.

Here is my sensors output, as you can see none of my fans are reporting, nor are any of my CPU cores. Suggestions?

```
$ sensors
nct6776-isa-0290
Adapter: ISA adapter
Vcore:          +0.87 V  (min =  +0.00 V, max =  +1.74 V)
in1:            +1.83 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:           +3.26 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:          +3.26 V  (min =  +2.98 V, max =  +3.63 V)
in4:            +1.48 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:            +1.70 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:            +0.87 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:           +3.46 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:           +3.38 V  (min =  +2.70 V, max =  +3.63 V)
fan1:             0 RPM  (min =    0 RPM)
fan2:             0 RPM  (min =    0 RPM)
fan3:             0 RPM  (min =    0 RPM)
fan4:             0 RPM  (min =    0 RPM)
fan5:             0 RPM  (min =    0 RPM)
SYSTIN:         +41.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:         +35.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:          +3.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PCH_CHIP_TEMP:   +0.0°C  
PCH_CPU_TEMP:    +0.0°C  
PCH_MCH_TEMP:    +0.0°C  
intrusion0:    ALARM
intrusion1:    ALARM
beep_enable:   disabled


fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       44.54 W  (crit = 125.19 W)


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +23.6°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)

```

---

### Post by QIII on 2015-07-10
K10temp is your CPU temperature.  The CPU itself does not report temperatures of the individual cores.

You can see also that your CPU is reporting its power consumption in watts.

K10temp also doesn't report physical temperature, but a "thermal margin" used to control cooling.  One of my few articles (haven't had much free time lately) on my blog at theleftcoastgeek.net discusses the issue.

The fans not reporting is a mystery.

---

### Post by john409 on 2015-07-10
Only 3 of the fan headers are plugged in. 
1 connects to a H100i liquid cooler with 2 120mm fans via a 3-pin connector at the CPU - the pump should be reporting about 2100 rpm - I don't think the fans report via CPU
1 connects to a 3 pin 140mm case fan that is running about 1000 rpm
1 connects to a pair of 3 pin 140mm case fans via a splitter cable they both should be at about 1000 rpm. I don't think they both report - I had one plugged into the pwr fan connector, but moved it to the splitter.
The fans also don't report in my Corsair Link on Windows, but I can see them just fine in the Motherboard control panel.
The other two fan headers are 4 pin, 1 at the CPU and the other just on the Motherboard.
I also see temperature readings in Corsair Link for my drives, but don't see that in Motherboard Control Panel, nor anywhere in Ubuntu.
And I have fan and temperature reporting in Windows Corsair Link for my GPU, but see nothing of that too.
I am simply confused. I recognized that it isn't really all that important, but it is bugging me!

---

### Post by QIII on 2015-07-10
I'm not terribly surprised that your AIO is not reporting anything through sensors, since I think all the software for that is built for Windows.  The other fans I don't know.

To get HDD temps, you'll need to install hddtemp and set it to run as a daemon at startup.  

Install:

```
 sudo apt-get install hddtemp 
```

Set up to run as a daemon:

```
 sudo dpkg-reconfigure hddtemp 
```

Just accept the defaults and be sure to say yes when asked if you want it to run as a daemon.

At the very end, you'll be given some instructions for starting the service.  Follow those.

For your GPU, you'll have to install the proprietary driver to get any information from it.  There's nothing in sensors to deal with it.

To get the GPU temperature, you'll need to use amdconfig --odgt with some parameters (on cell phone right now, so hard to give details).  Overdrive in Linux is strictly command line.  There is no GUI.

---

### Post by john409 on 2015-07-10
I ran the hddtemp install and configuration, but nothing new on sensors.

---

### Post by john409 on 2015-07-10
Restarted. Now I see the drive temps.

Really wish I could see my fan temps.

I'm half tempted to pull the 4 pin fans off my H100i and install them on a 4 pin connector on the board just to see if they report.

---

### Post by john409 on 2015-07-10
So..I found this...```
sudo pwmconfig
``` and it offers to adjust my fan settings, but that is not my plan. But after I said no to all the questions to skip over it, I was given this little snippet:

```
Giving the fans some time to reach full speed...Found the following fan sensors:
   hwmon0/fan1_input     current speed: 0 ... skipping!
   hwmon0/fan2_input     current speed: 0 ... skipping!
   hwmon0/fan3_input     current speed: 0 ... skipping!
   hwmon0/fan4_input     current speed: 0 ... skipping!
   hwmon0/fan5_input     current speed: 0 ... skipping!


There are no working fan sensors, all readings are 0.
Make sure you have a 3-wire fan connected.
You may also need to increase the fan divisors.
See doc/fan-divisors for more information.

```
Any idea what it is talking about??? I don't see a doc/fan-divisors

---

### Post by john409 on 2015-07-10
Somehow I missed your suggestion for the GPU temps! I ran amdconfig --odgt and it prompted me to run aticonfig --initial which I did...with some trepidation...and then amdconfig --odgt ran and I was able to see that my GPU is sitting at a cool 39 degrees.

It does not seem to report to Psensor though.

---

### Post by QIII on 2015-07-10
No.  It won't go through sensors.  It's proprietary functionality in the proprietary driver.  Cell phone is dying.  Will be at my computer momentarily.

OK -- here.

You can keep tabs on the temperature every second by running the following in the terminal:

```
watch -n 1 amdconfig --odgt
```

But that's a little inconvenient.

If you want to get in to using conky to monitor your system, you can add the following sort of thing to your conky configuration:

```
${execi 1 amdconfig --odgc --odgt --adapter=0 | egrep -i "load|temperature" | xargs echo | awk '{print $4 "    " $9 "°C "}'}${alignr 30}${execi 1 aticonfig --pplib-cmd "get fanspeed 0" | grep -i result | awk '{print $4}'} 
```

conky is not for the faint of heart, though.  What I have there gives me a horizontal tabulated readout of GPU load, GPU temp and GPU fan speed.

---

### Post by Yellow Pasque on 2015-07-12
Apparently, the lm-sensors devs only got the 2 CPU fan headers and one chassis fan header to report correctly. The 2 CPU fan headers are combined/"multiplexed" together in a way that doesn't make it straightforward to get the output, even with regular fans.
[http://www.spinics.net/lists/lm-sensors/msg38019.html](http://www.spinics.net/lists/lm-sensors/msg38019.html)
So, you should try plugging a fan into the 3-pin "CHA1" and/or "CHA2" header. One of those headers should give you a reading assuming the fan has wires connected to all 3 pins.
As for the proprietary Corsair Link garbage, I doubt you'll get a reading in Linux. I gave you a link in another thread to the independent work being done to try and get it working under Linux, but it looks like the work is not final and not yet in the Linux kernel.

> pwmconfig
pwmconfig uses the values that sensors reports, so until you get reasonable fan speed output from sensors command, you're wasting your time with pwmconfig.

> Any idea what it is talking about??? I don't see a doc/fan-divisors 
Your sensor chip (Nuvoton NCT6776F) does not need or support manual tweaking of the fan divisor.
[http://www.mjmwired.net/kernel/Documentation/hwmon/nct6775](http://www.mjmwired.net/kernel/Documentation/hwmon/nct6775)

---

### Post by john409 on 2015-07-12
Conky is cool!!!

I have it reporting all 8 cores, CPU temp, Drive temp, GPU temp, and SYStemp.

I have no idea what AUXtemp is all about, it says 4 degrees, and moves a bit, but it is definitely not that cold in there.

Is there a way to get the fanspeed in RPM rather than % in Conky?

I will open the case later and see about moving my fans to different headers.

I appreciate the help!

---

### Post by QIII on 2015-07-12
If you are talking about the GPU fan, no you can't get RPM.  That value is reported by the proprietary driver in percent.

You could, however, research the maximum design fan speed on the card and simply multiply that by the percent -- I'd do that in a script and call the script from your conky.

---

### Post by john409 on 2015-07-12
> [COLOR=#000000] I'd do that in a script and call the script from your conky.[/COLOR]
UMMM.....ok........

I know this probably sounds like a stupid question, but I guess I gotta learn somehow. 

How do I write a script to call from Conky? 

this is my current Conky script for the GPU.

```
${color #0ABFFF}GPU ${hr 1}$color${voffset 8}${color 0ABFFF}Load  Temperature               Fan $color 
${execi 1 amdconfig --odgc --odgt --adapter=0 | egrep -i "load|temperature" | xargs echo | awk '{print $4 "      " $9 "°C "}'}${alignr 30}${execi 1 aticonfig --pplib-cmd "get fanspeed 0" | grep -i result | awk '{print $4}'}
```

---

### Post by QIII on 2015-07-12
Not a stupid question at all!

But (there's always a but... :) )

We're starting to move away from your initial question about sensors.  If that is pretty much answered, it would probably be best to start a new thread specifically asking about how to write such a script.

Long, rambling threads that drift around a lot tend to get muddy.

---

### Post by john409 on 2015-07-12
> **Temüjin said:**
> Apparently, the lm-sensors devs only got the 2 CPU fan headers and one chassis fan header to report correctly. The 2 CPU fan headers are combined/"multiplexed" together in a way that doesn't make it straightforward to get the output, even with regular fans.
[http://www.spinics.net/lists/lm-sensors/msg38019.html](http://www.spinics.net/lists/lm-sensors/msg38019.html)
So, you should try plugging a fan into the 3-pin "CHA1" and/or "CHA2" header. One of those headers should give you a reading assuming the fan has wires connected to all 3 pins.


Ok...I moved over to the Cha_Fan_1 header and can see the RPM of the two front fans that are conneced with a 1 - 2 Y adaptor:

```
$ sensorsnct6776-isa-0290
Adapter: ISA adapter
Vcore:          +0.87 V  (min =  +0.00 V, max =  +1.74 V)
in1:            +1.84 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:           +3.26 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:          +3.26 V  (min =  +2.98 V, max =  +3.63 V)
in4:            +1.46 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:            +1.70 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:            +0.81 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:           +3.46 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:           +3.38 V  (min =  +2.70 V, max =  +3.63 V)
fan1:          1028 RPM  (min =    0 RPM)
fan2:             0 RPM  (min =    0 RPM)
fan3:             0 RPM  (min =    0 RPM)
fan4:             0 RPM  (min =    0 RPM)
fan5:             0 RPM  (min =    0 RPM)
SYSTIN:         +38.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:         +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:          +4.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PCH_CHIP_TEMP:   +0.0°C  
PCH_CPU_TEMP:    +0.0°C  
PCH_MCH_TEMP:    +0.0°C  
intrusion0:    ALARM
intrusion1:    ALARM
beep_enable:   disabled


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +11.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)


fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       33.17 W  (crit = 125.19 W)

```

I then followed the links you gave me to find:```

[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[/TR]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]
Enable and select CPUFANIN2[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[/TR]
[/TABLE]

[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]isaset -y -f 0x2e 0x87[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number"]isaset -y -f 0x2e 0x87[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[/TR]
[TR]
[/TR]
[/TABLE]
[LEFT]isaset -y 0x2e 0x2f 0x7 0x8[/LEFT]
[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"]isaset -y 0x2e 0x2f 0xf0 0xb2[LEFT]saset -y 0x2e 0x2f 0xf1 0xf2[/LEFT]
[/TD]
[/TR]
[/TABLE]

```

and now I see:
```
fan1:          1018 RPM  (min =    0 RPM)fan2:          2261 RPM  (min =    0 RPM)
fan3:             0 RPM  (min =    0 RPM)
fan4:             0 RPM  (min =    0 RPM)
fan5:             0 RPM  (min =    0 RPM)



```

Thank you for your help! Now I get to start a new thread about Conky to get my reporting right.

---

### Post by Yellow Pasque on 2015-07-12
So I guess the H100 is not using anything proprietary to monitor the fan speeds? I guess you could use SpeedFan in Windows and don't need to bother with special Corsair software.
Maybe the only reason it comes with Corsair Link software is that Corsair wants you to buy one of their Link controllers.
Anyway...
If the thread is solved to your satisfaction, please mark it solved.

Oh, and a couple other notes:
```
k10temp-pci-00c3
temp1:        +11.0°C
```
IIRC, Kaveri-based CPU's are known to report really low values through k10temp when idle/cool, but when running under load, they are accurate. At least your CPUTIN readout looks accurate.

Also, it seems AsRock didn't connect AUXTIN to anything on their 990FX boards. When I was googling, I saw other people with similar boards note that it gives garbage values (under Windows or Linux).

---

### Post by john409 on 2015-07-12
Actually, the fan speed that is being reported at the H100i header is the pump speed, not actually the fans. From what I understand the fans are reported via a USB link that is connected to the motherboard, but I think that might be beyond my skills to google.

I had heard that the CPU reports weird readings at light load, but 11 is about the lowest I have seen it go. 

The AUXTIN number is reporting low in the ASRock system control panel as well, so I guess it is worthless.

Thank you so much for your help, I will be back with more questions on another thread, I am sure.

I got a bit spoiled with Windows doing all the work for me, but I do like the Ubuntu OS better, it feels like I have a bit of control.

---

### Post by Yellow Pasque on 2015-07-12
> Actually, the fan speed that is being reported at the H100i header is the pump speed, not actually the fans.
Oh, I see. Then yeah, the fans probably use the proprietary Corsair Link for some reason

> Thank you so much for your help
You're welcome. Please mark the thread solved (thread tools menu above the first post).

---

