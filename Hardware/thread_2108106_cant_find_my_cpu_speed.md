---
title: "cant find my cpu speed"
date: 2013-01-23
forum: Hardware
---

### Post by randywolf244 on 2013-01-23
i tried using cat /proc/cpuinfo and under model name where i usually find it on my other machines i see 

AMD Athlon(tm) 64 X2 Dual Core Processor 4000+

is the 4000+ my cpu speed or what im used to seeing it like 1.3 ghz or 2.0 ghz or something

---

### Post by Lightning Dragon on 2013-01-23
Hello,

Nope, I do believe that is part of the name of your CPU. [If I have the right CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103774"), this is the speed of your CPU "2.1" ghz. Install "sysinfo" to be able to see all of your hardware details, including CPU details. :)

To download via the terminal, sudo;

sudo apt-get install sysinfo

Yours should read off as "2100.000 MHz" in sysinfo.

---

### Post by randywolf244 on 2013-01-23
right-o thanks mate

---

### Post by randywolf244 on 2013-01-23
although it is only a 2.1 ghz sigh lol

---

### Post by Yellow Pasque on 2013-01-23
Paste the output from lshw:
```
sudo apt-get install lshw
sudo lshw -C CPU
```

> is the 4000+ my cpu speed
No, there were a few AMD chips to use this model name and some of them had different speeds. At the time, '4000' meant it was the equivalent of a Pentium4/D 4.0GHz (to help consumers that couldn't grasp the concept of CPU performance being based on factors besides clock speed).

---

### Post by Lightning Dragon on 2013-01-23
Hello,

> **randywolf244 said:**
> although it is only a 2.1 ghz sigh lol

I am not sure of the model you have, so it might be higher (or if the brand is correct, it can at least be overclocked to 2.8Ghz). Or did the sysinfo say it was "2.1" ghz?

---

### Post by Yellow Pasque on 2013-01-23
> **Lightning Dragon said:**
> sudo apt-get install sysinfo

It's probably better to have users use lshw or some lightweight text tool. Installing sysinfo will grab a bunch of mono packages that are not present on Lubuntu (as well as X/K/ubuntu?) by default.

---

### Post by Lightning Dragon on 2013-01-23
> **Temüjin said:**
> It's probably better to have users use lshw or some lightweight text tool. Installing sysinfo will grab a bunch of mono packages that are not present on Lubuntu (as well as X/K/ubuntu?) by default.

Oh, you are right! I completely forgot about the lshw command. It is a better choice. 

I recommend sysinfo a lot to people looking fur GUI system information on the entire system, so I guess it is now a habit to only suggest it and assume would be preferred. :lol:

---

### Post by Yellow Pasque on 2013-01-23
Yeah, I actually remembered that Ubuntu dropped mono from all default installs since 12.04. sysinfo is good for those allergic to terminals, but I hate that annoying bug where it says "Unknown Graphics" and the user freaks out about video drivers.

---

### Post by Lightning Dragon on 2013-01-23
I hate that bug, especially when the distro detects what it is through its Detail page. And he would probably get the "exec: 9: mono: not found" problem in Xubuntu too, so your step should definitely be taken. 

Although, if I remember correctly, he could try going into the System Monitor if he does prefer a GUI. It should display there the way he was originally looking for. It should be in Menu > System > System Monitor. 

That should display the same thing sysinfo does, and will also have a GUI.

---

### Post by Cheesemill on 2013-01-23
> **Temüjin said:**
> but I hate that annoying bug where it says "Unknown Graphics" and the user freaks out about video drivers.

If this is the same bug that affects System Settings > Details it can be easily fixed by installing the mesa-utils package.

---

### Post by Lightning Dragon on 2013-01-23
> **Cheesemill said:**
> If this is the same bug that affects System  Settings > Details it can be easily fixed by installing the  mesa-utils package.

In sysinfo it displays it as "Unknown" even with the mesa-utils  installed. At least in Ubuntu 12.04 it doesn't help any, so I only assume it won't in Xubuntu. But instead of  sysinfo, it would probably be best to check System Monitor or use the  recommend terminal command.

---

