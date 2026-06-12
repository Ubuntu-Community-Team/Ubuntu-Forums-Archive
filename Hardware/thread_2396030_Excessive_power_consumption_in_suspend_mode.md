---
title: "Excessive power consumption in suspend mode"
date: 2018-07-10
forum: Hardware
---

### Post by canavaroski90 on 2018-07-10
[COLOR=#111111][FONT=Ubuntu]When I put my laptop into suspend mode it consumes around half of the battery in around 8 hours. This is pretty higher when comparing the previous versions of Xubuntu that I've used.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any idea how to track why the consumption so high? I'm not able to install another OS to check the results since this is the only laptop I'm using for work and for my personal things.

Hardware:
```
[FONT=Consolas]Asus UX430UN[/FONT][/FONT][/COLOR]
i7-8550u
16GB Memory [COLOR=#111111][FONT=Ubuntu][FONT=Consolas]512Gb SSD[/FONT]
```
[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]Software:

```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]Xubuntu 18.04 [/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]Linux 4.15.0-24-lowlatency (I've also tried with generic kernel)[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
```
[/FONT][/COLOR]

---

### Post by Doug S on 2018-07-10
Perhaps, and as a test, try the current mainline release candidate kernel, [4.18-rc4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18-rc4/"). Your processor is very new, and sometimes the kernel takes awhile to catch up.

---

### Post by ajgreeny on 2018-07-10
There was another, probably unrelated problem with the 4.15.0-24 kernel which made boot take a very long time and the generic kernel version was therefore removed from the repos; I wonder if this has anything to do with your problem?

Did you notice the same when (or if) you booted to the previous kernel, 4.15.0-23?

---

### Post by canavaroski90 on 2018-07-11
@Doug S thanks for the suggestion, I'll try the 4.18 and let you know the results.

@ajgreeny , boot time is definitely slower comparing to the previous LTS (16.04) but unfortunately, I don't remember which version of the kernel I was using.

---

### Post by ajgreeny on 2018-07-11
Do you have an older kernel still installed in your system to which you can boot to check if the problem is still there?

You can check kernels available with command ```
ls /boot | grep vmlinuz
``` and then boot to the earlier version from grub, using the "Advanced options for ubuntu"

---

### Post by canavaroski90 on 2018-07-11
Nope, when I was referring to the old kernel I was mentioning about the kernel installed on Xubuntu 16.04. So I don't have any clue, sorry :(

BTW, installing kernel 4.18 seems working pretty well, at least power led started blinking in suspend mode (it was turned-on all the time on the previous kernel). Additionally, I didn't hear any fan noise in suspend mode. Let me try 4.18 for a few days then I will share the results with you again. 

Thanks for the help guys. You rocks!

---

### Post by ajgreeny on 2018-07-11
Sounds hopeful!

Good luck; make sure to let us know the score.

---

### Post by Doug S on 2018-07-11
> **canavaroski90 said:**
> installing kernel 4.18 seems working pretty well, at least power led started blinking in suspend mode (it was turned-on all the time on the previous kernel). Additionally, I didn't hear any fan noise in suspend mode. Let me try 4.18 for a few days then I will share the results with you again.If your longer term test is positive, then it would suggest that the problem is known and solved. Eventually, it will work its way down to an update from your normal kernel version, it just might take awhile.

---

### Post by canavaroski90 on 2018-07-13
@Doug S Yep, I'm gonna wait for the stable version of the kernel and then update. Thanks again.

However, I'm having another problem since I've started using kernel > 4.x versions. It seems that the kernel cannot read the CPU temperature correctly. According to sensord, CPU package temp goes high as 90-100 C for a short period of time like 1 seconds. Then it starts reading it correctly. Here is the log I've collected from sensors.

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





Here you can see sensord reports that CPU was overheated just for one second. Since it is physically not possible to lower the CPU temp around 30 C in nearly 100ms, I'm suspicious about the reliability of the sensord readings. Most frustrating part starts when those readings go higher than the critical temp threshold of the CPU. Machine shuts down itself immediately.

What do you suggest for this particular problem? How can I track whats going on?
Thanks.

[U][B]EDIT

[/B][/U] I made a test to see if this is a software problem rather than a hardware. I used psensor and logged last 30 minutes. I'm pretty sure you're gonna be surprised.

[[IMG]https://preview.ibb.co/k4BV48/psensor_edit.png[/IMG]]("https://ibb.co/e1XEWo")

As you can see when I put the device into heavy-load, readings become more accurate, but when I leave the device idle, sensor readings start fluctuating. I -without having any deep knowledge- assuming that sensor application cannot continue to poll the temperature with the same interval when the device is on load (must probably it cannot get enough cpu-time), so it -seems like- starts working correctly. However, when I leave the device, it can poll as frequent as it wants and then we see those results.

So, any idea about that? Who is responsible for hwmon things? Should I contact with some devs?

---

### Post by canavaroski90 on 2018-07-13
I believe this topic needs another post. So thanks for the help for previous problem guys. See you in another topic!

---

