---
title: "Aspire 7720G Fan not working"
date: 2010-07-19
forum: Hardware
---

### Post by crova on 2010-07-19
Hi all! I have a problem with the new ubuntu lucid lynx..the fan of my laptop ( Acer Aspire 7720G ) isn't working. There's a way to fix this?

thank you in advance for the help :)

---

### Post by PresenceofMind on 2010-07-19
Hey!!!

Try this code. It tests the fan voltage controls and let's you know what's what:

```
sudo pwmconfig
```

---

### Post by crova on 2010-07-19
> **PresenceofMind said:**
> Hey!!!

Try this code. It tests the fan voltage controls and let's you know what's what:

```
sudo pwmconfig
```

hi, I did it and my result is

```
 
# pwmconfig revision 5770 (2009-09-16)
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

I think it isn't a good result ahah xD
thank you for the help :D

---

### Post by PresenceofMind on 2010-07-19
> **crova said:**
> hi, I did it and my result is

```
 
# pwmconfig revision 5770 (2009-09-16)
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

```I think it isn't a good result ahah xD
thank you for the help :D

Aww man!!!! No problem :D

I've posted a new thread asking for any method by which you can test and access the fan controls via a Terminal or a program...hope I get some answers there...

---

### Post by crova on 2010-07-20
ah..I want to add that I have Ubuntu 64 bit ..any other hint? ;_;

---

### Post by PresenceofMind on 2010-07-21
> **crova said:**
> ah..I want to add that I have Ubuntu 64 bit ..any other hint? ;_;

What's the problem?.... You have a fan issue too?

---

### Post by PresenceofMind on 2010-07-21
Ok....try this. Log in to a terminal and:

```
cd /proc/acpi/thermal_zone/
```I think you will find a single directory in there. Change into that directory by typing:

```
cd <directory_name>
```Replace <directory_name> with the name of the actual directory.

then enter:

```
cat cooling_mode
```Tell me what you see.

---

### Post by samibe on 2010-08-07
samibe@ubuntu:/proc/acpi/thermal_zone/TZ01$ cat cooling_mode
<setting not supported>

---

