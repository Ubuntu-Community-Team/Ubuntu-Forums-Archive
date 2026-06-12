---
title: "Can't figure out cpu fan speed"
date: 2012-07-16
forum: Hardware
---

### Post by sudo smith on 2012-07-16
Ok so my cpu fan is really loud and I wanted to see how fast it's going. I am running Ubuntu 12.04 64-bit with the default unity. I looked around on the internet and found that I should install lm-sensors and then run sudo sensors-detect. I did so and answered yes on all the questions. I then ran service module-init-tools restart and also service module-init-tools start. Finally, I ran sudo sensors, but it only told me my cpu temp. Is there any way I can get it to show my cpu fan speed? Or is there another application which will show me my cpu fan speed (already tried Psensors, but it only showed me cpu usage and temp)? Thanks in advance.

---

### Post by ajgreeny on 2012-07-16
I think lmsensors is totally dependent on your hardware; it never works or finds any sensors on my machine either.

I did use mbmon in terminal in the past and that gave a reading of various things including voltages and fan speeds with output like this:-
```
Temp.= 32.0, 25.0, 26.0; Rot.= 6250, 3901,    0
Vcore = 1.65, 1.65; Volt. = 3.36, 4.89, 11.49, -10.51, -4.54
```
but I am not truly certain how accurate it is, nor which of the Rot figures refers to the cpu fan speed.

OK:, An update.

The command ```
mbmon -A
``` shows the temp of cpu third in the listed temps, according to /usr/share/docs/mbmon/README.gz

---

### Post by sudo smith on 2012-07-16
> **ajgreeny said:**
> I think lmsensors is totally dependent on your hardware; it never works or finds any sensors on my machine either.

I did use mbmon in terminal in the past and that gave a reading of various things including voltages and fan speeds with output like this:-
```
Temp.= 32.0, 25.0, 26.0; Rot.= 6250, 3901,    0
Vcore = 1.65, 1.65; Volt. = 3.36, 4.89, 11.49, -10.51, -4.54
```
but I am not truly certain how accurate it is, nor which of the Rot figures refers to the cpu fan speed.

OK:, An update.

The command ```
mbmon -A
``` shows the temp of cpu third in the listed temps, according to /usr/share/docs/mbmon/README.gz

Ok I installed and tried mbmon. Unfortunately it doesn't give me the cpu fan speed or any other data. Here is the output.

```
 
sebastian@sebastian-DX4300:~$ sudo mbmon
No Hardware Monitor found!!
InitMBInfo: Success
sebastian@sebastian-DX4300:~$ sudo mbmon -A
InitMBInfo: Success
This program needs "setuid root"!!

```

I am new to Ubuntu and do not understand what this means, or how I can fix it. Thanks though for the reply.

---

### Post by ajgreeny on 2012-07-18
I think that means that you do not have hardware monitors to run mbmon;  it does not work with all mothermoards, and even my old laptop gives me no output.

Sorry, but I can't think of any other ways to deal with this for you.

---

### Post by sudo smith on 2012-07-18
Well thanks for the replies. Guess my motherboard simply doesn't have any sensors installed and theres no software way to fix it.

---

### Post by Icarus315 on 2012-07-18
I have this hardware sensors indicator installed:

[Here](http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html)

It shows all my temperatures and fan speeds.  Perhaps it is worth a try for yourself?

---

### Post by ajgreeny on 2012-07-19
> **Icarus315 said:**
> I have this hardware sensors indicator installed:

[Here]("http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html")

It shows all my temperatures and fan speeds.  Perhaps it is worth a try for yourself?
It is also hardware dependent and does not show anything on my machine,  just like lm-sensors, in fact I think it uses the same MB sensors, so that isn't surprising.

---

### Post by sudo smith on 2012-07-20
> **Icarus315 said:**
> I have this hardware sensors indicator installed:

[Here](http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html)

It shows all my temperatures and fan speeds.  Perhaps it is worth a try for yourself?

Just as ajgreeny said its probably hardware dependant (I don't see how you can have a non-hardware dependant hardware monitor. In addition. It says package is unable to be found (and yes I did install the repository first, then ran update, then tried to install package).

---

### Post by Icarus315 on 2012-07-20
> **ajgreeny said:**
> It is also hardware dependent and does not show anything on my machine,  just like lm-sensors, in fact I think it uses the same MB sensors, so that isn't surprising.

Yeah, I don't have lm-sensors installed, just this package and it works fine for myself.

> **sudo smith said:**
> Just as ajgreeny said its probably hardware dependant (I don't see how you can have a non-hardware dependant hardware monitor. In addition. It says package is unable to be found (and yes I did install the repository first, then ran update, then tried to install package).

Which version of Ubuntu are you running?  I'm running 12.04 and I installed the repository and then the package just fine.

---

### Post by sudo smith on 2012-07-22
> **Icarus315 said:**
> 
Which version of Ubuntu are you running?  I'm running 12.04 and I installed the repository and then the package just fine.

I have Ubuntu 12.04 too, but since it probably won't work anyway (because of my hardware) its not as important.

---

