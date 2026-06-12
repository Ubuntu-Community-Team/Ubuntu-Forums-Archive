---
title: "144 C temerature reached, random shut down [MUTEX]"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by uBo on 2006-09-23
Hi,

I am running Dapper on a Toshiba A105 and am quite happy with it apart from the ACPI support.

The first line of the code comes up in the logs very often, but now and again the following thing happens:

```
Sep 23 14:05:56 localhost kernel: [17186106.432000]     ACPI-0240: *** Error: Cannot release Mutex [MUT1], not acquired
Sep 23 14:05:56 localhost kernel: [17186106.432000] Critical temperature reached (144 C), shutting down.
Sep 23 14:05:57 localhost shutdown[8684]: shutting down for system halt
```

I do not think that the temperature reached 144 degrees celsius, the laptop was not really hot. The fans are working normally and the temperature never goes over 60 degrees at the highest loads. 

I think it is this Mutex thing. What is it it is hard to find anything about it.

These random shutdowns really make my Ubuntu experience much worse than it could be. Please help!!

---

### Post by xyz on 2006-09-23
This is just a thought...
If you right-click on top panel > Add to panel and add Hardware Sensors Monitor...what does it say?

---

### Post by xyz on 2006-09-23
Also in a console```
acpi -V
```

---

### Post by xyz on 2006-09-23
[Laptop Temperature Monitor 0.8.0 - FREE]("http://linux.softpedia.com/progDownload/Laptop-Temperature-Monitor-Download-4445.html")

> Laptop Temperature Monitor is a little applet for the GNOME desktop that shows the temperature of your laptop CPU on screen. You can log temperatures to a file as well. Installation tar xzf laptoptemp-0.2.tar.gz $ cd laptoptemp-0.2 $ ./configure $ make $ sudo make install Requirements: · python · python-gnome · python-gnome-extras What's New in This Release: · Added support for monitoring Harddis...

---

### Post by uBo on 2006-09-23
i have the computer temperature monitor on my bar, and as i have written it never shows more than 60 C, and the average is about 46 C.

when the temerature goes over 50 C, the additional fans turn on. it is working fine.

it is not the temperature, the 144 C are not real in my opinion.

I think it is this ACPI Mutex thing. But what is it and how to repair it.

the error

ACPI-0240: *** Error: Cannot release Mutex [MUT1], not acquired

comes very often, the shutdowns much more rarely. interestingly, when runing on battery, or when the battery is in the bay the shutdowns are very frequent.

help, this thing makes my ubuntu not very usable!

---

### Post by xyz on 2006-09-23
What is your
```
uname -r
```

---

### Post by xyz on 2006-09-23
Just in case...
[Kernel 2.6.15-19 was the last that worked fine. I've had this error Since Kernel 2.6.15-20.]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48556")

It may be a bug! Let me know.

---

### Post by insane_alien on 2006-09-23
if you can get your hands on an IR thermometer then give it a whirl, the tend to be a bit more accurate than the thermistors currently used. i've had a number of unreal temps upto around 30000 celsius. at 144 i think the processor would be a bit fried. sure its not farenheit?

---

### Post by K.Mandla on 2006-09-23
> **insane_alien said:**
> at 144 i think the processor would be a bit fried.
Right on. 144 C is close to 300 F. If it was really that hot, you'd notice. ;)

---

### Post by uBo on 2006-09-23
@xyz:
2.6.15-27-386

It is not the bug you have linked to.

@the others:

I am quite positive that this 144 C is not real but a software bug. The laptop is normally warm.

What is Mutex, somehow noone seems to know. I am quite positive the problem lies there, because this shut down thing happens always after this Mutex error.

Help me stay with Ubuntu.

---

### Post by xyz on 2006-09-24
> I am quite positive that this 144 C is not real but a software bug. The laptop is normally warm.

If it feels normally warm...why worry? I mean, are you sort of "making up" problems for yourself! No offence intended, ok?
At that temperature, you could fry an egg on if? Can you?  lol kidding...

---

### Post by uBo on 2006-09-24
it is not about the temperature itself, it is the random shutdowns, they make ubuntu almost unusable. it's like windows with some virus that is restarting it all the time.

seriously, people, there should be someone who knows what Mutex is???

---

### Post by xyz on 2006-09-24
Doesn't solve anything but now we know what it is...sort of...
> MUTEX
 (1) Short for mutual exclusion object. In computer programming, a mutex is a program object that allows multiple program threads to share the same resource, such as file access, but not simultaneously. When a program is started, a mutex is created with a unique name. After this stage, any thread that needs the resource must lock the mutex from other threads while it is using the resource. The mutex is set to unlock when the data is no longer needed or the routine is finished.

(2) When spelled MuTeX, a package of macros for the TeX typesetting system that supports musical notation. MuTeX was written by Andrea Steinbach and Angelika Schofer, as a master's thesis at Rheinische Friedrich-Wilhelms University. 

---

### Post by uBo on 2006-09-24
Hm, Mutex is something generic then. So it should be:

ACPI-0240

What is it?


It just happened again, this time 142 C. 

The laptop is not hot, not hotter than normal.

---

### Post by xyz on 2006-09-24
I found this thread:
[http://www.ubuntuforums.org/showthread.php?t=75227](http://www.ubuntuforums.org/showthread.php?t=75227)

---

