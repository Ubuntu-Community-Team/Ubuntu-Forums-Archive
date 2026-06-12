---
title: "CPU Temperature jumps up and down"
date: 2018-07-13
forum: Hardware
---

### Post by canavaroski90 on 2018-07-13
I'm having a problem since I've started using kernel > 4.x versions. It seems that the kernel, or some part of the OS or hardware, cannot read the CPU temperature correctly. According to sensord, CPU package temp goes high as 90-100 C for a short period of time like 1 seconds. Then it starts reading it correctly. Here is the log I've collected from sensors.

> 11:31:58:406650710 +57.0°C
11:31:58:516196206 +57.0°C
11:31:58:621513975 +57.0°C
11:31:58:727823864 +57.0°C
11:31:58:911125884 +57.0°C
11:31:59:017793610 +57.0°C
**11:31:59:124754064 +86.0°C**
**11:31:59:237313849 +86.0°C**
**11:31:59:365184465 +86.0°C**
**11:31:59:511534916 +86.0°C**
**11:31:59:662619754 +86.0°C**
**11:31:59:816669327 +86.0°C**
**11:31:59:964797207 +86.0°C**
**11:32:00:110941213 +86.0°C**
11:32:00:260444934 +58.0°C
11:32:00:386547237 +58.0°C
11:32:00:514622494 +58.0°C
11:32:00:632735632 +58.0°C
11:32:00:754842985 +58.0°C
11:32:00:879610746 +58.0°C





Here you can see sensord reports that CPU was overheated just for one second. Since it is physically not possible to lower the CPU temp around 30 C in nearly 100ms, I'm suspicious about the reliability of the sensord readings. Most frustrating part starts when those readings go higher than the critical temp threshold of the CPU; _*Machine shuts down itself immediately*_.

I made a test to see if this is a software problem rather than a hardware. I used psensor and logged last 30 minutes. I'm pretty sure you're gonna be surprised.

[[IMG]https://preview.ibb.co/k4BV48/psensor_edit.png[/IMG]]("https://ibb.co/e1XEWo")

(Peaks are around 85 to 95 Celcius)

As you can see when I put the device into heavy-load, temperature readings become more accurate, but when I leave the device idle, sensor readings start fluctuating. I -without having any deep knowledge- assuming that sensor application cannot continue to poll the temperature with the same interval when the device is on load (most probably it cannot get enough cpu-time), so it -seems like- starts working correctly. However, when I leave the device, it can poll as frequent as it wants and then we see those results.

So, any idea about that? Who is responsible for hwmon things? Should I contact some devs? What do you suggest for this particular problem and how can I track whats going on?
Thanks.

---

### Post by TheFu on 2018-07-13
I would first assume it is an issue with my hardware and check the CPU, fan, thermal grease and motherboard.
I don't think there is any issue with the software.

Yours is the first that I've see with this issue in these forums.
I have a CPU that slows down due to thermal issues under heavy load.  The sensor data appears to be correct to me.
```
[1353471.754923] CPU4: Core temperature above threshold, cpu clock throttled (total events = 97551719)
[1353471.754925] CPU0: Core temperature above threshold, cpu clock throttled (total events = 97552195)
```

You can file a bug - just google "ubuntu bug report" and follow the instructions there to see if it has been previously reported, if not, file a new one.  That would be helpful, if you've verified it isn't the hardware at fault.

---

### Post by canavaroski90 on 2018-07-15
Thanks for the answer. 

Here is also a little part from dmesg.
```
[ 1282.296247] CPU0: Core temperature above threshold, cpu clock throttled (total events = 109)[ 1282.296267] CPU4: Core temperature above threshold, cpu clock throttled (total events = 109)
[ 1282.296269] CPU5: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296269] CPU1: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296271] CPU4: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296272] CPU6: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296273] CPU2: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296274] CPU7: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296275] CPU3: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.296281] CPU0: Package temperature above threshold, cpu clock throttled (total events = 220)
[ 1282.297226] CPU4: Core temperature/speed normal
[ 1282.297227] CPU5: Package temperature/speed normal
[ 1282.297228] CPU0: Core temperature/speed normal
[ 1282.297229] CPU1: Package temperature/speed normal
[ 1282.297229] CPU0: Package temperature/speed normal
[ 1282.297230] CPU4: Package temperature/speed normal
[ 1282.297233] CPU3: Package temperature/speed normal
[ 1282.297233] CPU7: Package temperature/speed normal
[ 1282.297269] CPU2: Package temperature/speed normal
[ 1282.297269] CPU6: Package temperature/speed normal
```

I started to be suspicious about the hardware and renew the thermal paste on both CPU and GPU, but nothing changed. I find an old bug report on RedHat Bugzilla: [https://bugzilla.redhat.com/show_bug.cgi?id=924570](https://bugzilla.redhat.com/show_bug.cgi?id=924570)

And starting from comment [#34 (link is here)]("https://bugzilla.redhat.com/show_bug.cgi?id=924570#c34") people tried to disable turbo_boost feature of the CPU and this fluctuation problem resolved partially. I did the same and psensor or dmesg didn't report any high-temperature warnings since then. When I turned the turbo-boost on again, psensor and dmesg start throwing the same errors. However, the CPU is limited to 1.8Ghz and is not going to further speeds when I disable the turbo-boost. 

I assume that this is kind of kernel problem. And apparently, this is not the first time the kernel has had bad thermal management, check this out; [https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)

Now I'm also disabling the intel_pstate drivers to see if the responsible one was it. Will update with the results.


[I][B][U]UPDATE (16/07/2018 11:30):
[/U][/B][/I]I disabled intel_pstate drivers and leave the device open for more than 10 hours under mixed heavy-load and idle mode. Psensors didn't report any high temperature and there is no CPU temperature warning in dmesg. Seems pstate driver is responsible for this bug.
Marking as solved. Will update this topic with the bug report link when I create one.

Thanks.

[I][B][U]UPDATE (16/07/2018 11:55):
[/U][/B][/I]Psensor started to report high temperatures when I changed governor from powersave to performance or ondemand. In fact, the device was reset once because of high temp. I'll leave this topic open until I solve this problem.

---

