---
title: "CPU is running hot with Ubuntu"
date: 2008-06-30
forum: Hardware
---

### Post by Murky McWaters on 2008-06-30
I have a Toshiba P25-S5092 laptop that I recently removed Windows XP from (formatted the drive) and installed Ubuntu. The new OS seems to work fine, but just a couple minutes after booting up, my cooling fans start up and continue to run faster until the CPU fan is at full speed.

In my past experience this means the CPU is running hot. But in Windows it only did this if I was really stressing the machine. In Ubuntu it does it even when it's just sitting idle with no applications open.

The processor is an Intel P4 2.7GHz and the machine has 2GB RAM. Is there something I should do to address this, or is it even an important issue?

---

### Post by AlesUbu123 on 2008-06-30
Could you post the output of command:
```
acpi -t
```

Maybe scaling of CPU frequency is not enabled, causing your CPU to run at maximum frequency all the time.

Could you also give the output of:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
```

---

### Post by zgornel on 2008-06-30
If it is a desktop CPU, it will run hot and there is no frequency scaling. Regarding the Windows XP fan, maybe Windows is wrong not turning the fan on and leaving the CPU to fry. Monitor temperatures in both Windows and Linux and see if indeed the behavior in Linux is abnormal.

---

### Post by AlesUbu123 on 2008-06-30
zgornel, I disagree - I have a desktop computer and frequency scaling is enabled in XP and Ubuntu. He mentioned that XP actually did turn the fan on when it was under stress, so it could be a Ubuntu issue.

---

### Post by Murky McWaters on 2008-06-30
> **AlesUbu123 said:**
> Could you post the output of command:
```
acpi -t
```

Maybe scaling of CPU frequency is not enabled, causing your CPU to run at maximum frequency all the time.

Could you also give the output of:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
```
Output for acpi -t:
Battery 1: charged, 100%
No support for device type: thermal

Output for cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies:
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies: No such file or directory

---

### Post by zgornel on 2008-06-30
From what I know only the 6xx desktop series of the P4 had EIST (Enhanced SpeedStep) and I don't think this is the case. You might have a 6xx series Pentium 4 ore some Core2. Anyway, it is easyer to check if Ubuntu is actually the problem, especially on older hardware which is very well supported.
Edit: I also remeber that sometimes the kernel might create fan problems - on my system the server kernel does not turn the fan off. Recompiling the kernel might be a long shot but worth a try.

---

### Post by AlesUbu123 on 2008-07-01
Murky McWaters,

maybe you could try this
[http://ubuntuforums.org/showthread.php?t=190921]("http://ubuntuforums.org/showthread.php?t=190921")

---

### Post by zgornel on 2008-07-01
If you are lucky enough to have temperature readings of the processor you can regulate the trip point temepratures of the cooling fan : [http://powersave.sourceforge.net/powersave/Thermal.html](http://powersave.sourceforge.net/powersave/Thermal.html)

---

### Post by Skillachi on 2008-07-01
I am running a HPDV6700t with a Intel T9300 2.5ghz dual core installed. I also think my processor seems to run a little too hot (or maybe im just being paranoid, but it does feel hot after some use to me). 

The results i got for the stuff you posted was

acpi -t - Battery 1: charged, 100%, rate information unavailable

and for the other one

2501000 2500000 2000000 1600000 1200000 800000 
2501000 2500000 2000000 1600000 1200000 800000 

Am i being paranoid?

---

### Post by AlesUbu123 on 2008-07-01
Skillachi, at first we have to get info on the temperature of your cpu. 

You can try doing this at first:
> **jespdj said:**
> You can install the GNOME sensors applet by installing the package sensors-applet:
```
sudo apt-get install sensors-applet
```
After that, logout and login again, right-click the top panel on the desktop, select "Add to Panel...", and choose "Hardware Sensors Monitor".

Right-click the applet and select Preferences to choose the sensors that you want to monitor.
What are the temperatures reported by the applet?

Also, can you post the output of command:
```
cat /proc/acpi/thermal_zone/TZ*/temperature
```

---

### Post by Skillachi on 2008-07-01
I added the sensors monitor and stuff. However it is only monitoring the GPU temperature (which is 58 degrees celcius... thats hot... )

---

### Post by Skillachi on 2008-07-01
Also with the added command you type in I get the reply that there is no such file or directory

---

### Post by AlesUbu123 on 2008-07-01
I have a HP 6720s laptop with 1,6 Ghz Core2Duo. Frequency scaling works nicely and fan activity parallels that in XP. My Core2Duo CPU actually does reach 60&#730;C peaks at periods of maximum strain, and GPU temp is usually ranging between 50 and 60&#730;C.

Still, you can try installing lm_sensors to be sure:
[http://ubuntuforums.org/showpost.php?p=486752&postcount=4]("http://ubuntuforums.org/showpost.php?p=486752&postcount=4")

Also, try adding CPU frequency monitor to the panel, and check whether the frequency is changing with laptop activity. 

Can you hear fans on your laptop running?

---

### Post by Skillachi on 2008-07-01
Yeh i hear the fans coming on and off from time to time. I guess its safe and im paranoid then but i will take your suggestions. Thanx

---

### Post by -Outcast- on 2008-07-03
I am having a similar problem with a sony vaio TZ series am getting hot readings 
  Battery 1: charged, 79%
     Thermal 1: ok, 63.0 degrees C
     Thermal 2: ok, 62.0 degrees C
     Thermal 3: ok, 63.0 degrees C

There is a fan on. I can hear it. But it's not as fast as on Vista which I dual boot on. 

Any ideas?

---

### Post by AlesUbu123 on 2008-07-03
> **-Outcast- said:**
> I am having a similar problem with a sony vaio TZ series am getting hot readings
Any ideas?

Some people reported succes after performing steps decribed in this thread:
[http://ubuntuforums.org/showthread.php?t=539365&highlight=frequency+scaling]("http://ubuntuforums.org/showthread.php?t=539365&highlight=frequency+scaling")

---

### Post by Steveway on 2008-07-03
About 60°C are not very bad for your Pc. While my frequency-scaling was not working I easily got to temperatures of about 80°C and nothing has broken yet. (It does shut down after some time at those degrees.)
But now with powernowd it is constantly between 40 and 60°C.
Oh, yes, and this is a Laptop.

---

### Post by AlesUbu123 on 2008-07-03
If you are still worried about your laptop temperature, you can still checkout temperature measurements reported by other Ubuntu users. 
[http://ubuntuforums.org/showthread.php?t=210173&highlight=frequency+scaling]("http://ubuntuforums.org/showthread.php?t=210173&highlight=frequency+scaling")

I wouldn't be too worried about getting up to around 60 C.

---

### Post by zgornel on 2008-07-03
Actually, only above 90 for a long time should be concerning. Modern mobile processors are quite hot - the one in the Mac Air idles at about 70C. A temperature of 60C idle is nothing to worry (either GPU or CPU). The bad thing is the noise :| . My old Pentium M reached 85C under load and worked perfectly (after horus and hours at that temperature) - I solved the issue by blowing in the heatsink and removing some dust or whatever was is there, now it reaches 65 maximum.

---

