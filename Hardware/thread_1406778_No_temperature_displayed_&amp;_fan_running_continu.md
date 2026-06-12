---
title: "No temperature displayed &amp; fan running continuously"
date: 2010-02-14
forum: Hardware
---

### Post by emma_peel on 2010-02-14
Hello.

I have noticed that the temperature is not displayed when logging into my fesh installed server.

After a couple of searches, I have found that my MB, an ASUS P6T, has some compatibility issues with lm-sensors (at least the version provided by the stable repository).

I have checked in a previous installation on another computer, the temperature is displayed and lm-sensors is not installed.

So I'm a little bit confused. Do I have to install the last lm-sensors version ? That seems to help, but if it works without it on a previous install, there should be another way to fix this point.

Does anybody experience the same problems ? Thank's for the support.

PS : this is probably related, the fans are running continuously. There are low noise fans, so I can live with that, I would also appreciate if they could stop or slow down from times to times.

---

### Post by kio_http on 2010-02-14
Same problem here. Temporary solution is to enable ASUS Q-FAN in computer bios.

---

### Post by emma_peel on 2010-02-15
> **kio_http said:**
> Same problem here. Temporary solution is to enable ASUS Q-FAN in computer bios.

Thank you for the hint.

The installation has been done on a headless server ... changing the BIOS set-up is not easy. Without any other solution, I will have no choice.

---

### Post by emma_peel on 2010-02-15
Last news. Based on information from the forum, I managed to read the CPU temperature. I had to install the last version of lm-sensors from the source :

```
emma@Leucine:~$ sudo -i
root@Leucine:~# svn checkout http://lm-sensors.org/svn/lm-sensors/trunk lm-sensors
root@Leucine:~# aptitude install make gcc bison flex rrdtool perl
root@Leucine:~# cd lm-sensors
root@Leucine:~/lm-sensors# make all
root@Leucine:~/lm-sensors# make install
```

And now, a magic moment :

```
root@Leucine:~/lm-sensors# sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +0.94 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.02 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.08 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1917 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed: 948 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM)
CPU Temperature:    +33.5°C  (high = +60.0°C, crit = +75.0°C)  
MB Temperature:     +30.0°C  (high = +45.0°C, crit = +75.0°C)  
```

Unfortunatly, the fan control has failed :

```
emma@Leucine:~$ sudo pwmconfig
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

/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

Any idea to go further ?

---

### Post by emma_peel on 2010-02-18
> **kio_http said:**
> Same problem here. Temporary solution is to enable ASUS Q-FAN in computer bios.

That looks definitively the faster and only solution. Tried yesterday, and gives me pretty good results. I will close this thread, but will keep an eye on the following one :

[http://ubuntuforums.org/showthread.php?t=1245562](http://ubuntuforums.org/showthread.php?t=1245562)

---

