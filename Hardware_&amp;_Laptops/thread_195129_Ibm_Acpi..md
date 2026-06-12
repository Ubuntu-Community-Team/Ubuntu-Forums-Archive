---
title: "Ibm Acpi."
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by BoomAM on 2006-06-12
Hi.
Im seeing alot of guides to get everything working on my IBM TP Z60M saying that i need to get and them add to the kernal, something called IBM ACPI.
Can someonet tell me where i can get it from and what it is i need to do to install it.
I asume that after thats installed that sensor programs will then pick up fan speeds, temps, voltages, ect; ?

Thanks in advance all.

---

### Post by jrei on 2006-06-12
The module ibm_acpi comes with dapper.

Try "lsmod |grep ibm" to find out if its loaded.
If not use "modprobe ibm_acpi" to load it.

---

### Post by rabidphage on 2006-06-12
if you can't load it or find it (the ibm acpi module), then you'll have to recompile the kernel to turn it on..
compiling the kernal is not as difficult as it appears.. there are a lot of ubuntu specific guids elsewhere in the forum

---

### Post by BoomAM on 2006-06-12
Typing in lsmod |grep ibm just comes up with some numbers as a result?

Are there any tell tale signs that its working?
For example, the CPU does throttle according to load.
But, i cant access any temperature or fan sensors at all?

---

### Post by kroiz on 2006-06-12
I bet you already have acpi.
you probably read some old info.
here is an important link for ibm laptop owners:
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by BoomAM on 2006-06-12
So is there a way to tell if its 'on' or not?
Typing in the above commands just comes up with this:
```
boomam@boomam-laptop:~$ lsmod | grep ibm
ibm_acpi               26080  0

```

So does that mean its on or off?

If its on, how come no sensor apps will work? And how come that the fan hardly ever spins up. It used to come on every few mins in windows.

Thanks in advance again all. :)

---

### Post by spotman on 2006-06-12
open up a terminal.

cd /proc/acpi/ibm
cat fan

This should output what your fan is doing right now.  If it works, then ibm_acpi is fully functional.

Also, if you havent installed 'linux-686' then the dualcore and processor scaling is still disabled.  (you can obtain thru sudo apt-get install linux-686)

Otherwise, to check that, type cat /proc/cpuinfo, and you should see both cores.

---

### Post by spotman on 2006-06-12
also if your worried about overheating, check this out:

[http://zzrough.free.fr/emifreq.php](http://zzrough.free.fr/emifreq.php)

---

### Post by BoomAM on 2006-06-12
I'll have a look at that app tomorrow. :)

I did 
'cd /proc/acpi/ibm
cat fan'

And it came up with status=enabled, speed=2786.

Des that mean that the IBM ACPI is on and working?

---

### Post by spotman on 2006-06-12
Yup, its working!

if you want to disable it (probably a bad idea, because I think it already knows when to shut off/on)

you can type:
sudo echo "disable" > /proc/acpi/ibm/fan

then if you type:
cat /proc/acpi/ibm/fan

you will see its disabled.  and the reverse is true if you want to enable it.

I don't mess with my fan settings, but I noticed it is definitely more audible when the a/c is NOT plugged in.. strange...

---

### Post by BoomAM on 2006-06-12
So why do no temperature sensor programs work? Or any sensor programs (voltage, temperatures, fan speeds, ect; )?

---

### Post by spotman on 2006-06-12
its possible they are expecting a reading from a different source, maybe something like lmsensors.

ibm_acpi and other newer methods use acpi/proc/sysfs to get temperature and motherboard data back to the operating system.

most motherboards also have other sensors built in, and programs like lm_sensors monitor these and its possible the utilities you are trying are expecting something like lm_sensors to be in place...

you should try that app i posted a few posts ago in this thread, and do a search on the forums for lm_sensors

cheers
-spot

---

### Post by BoomAM on 2006-06-13
I have noticed on startup that:
'Setting Sensor Limits' fails.

Could that be the cause of the lack of sensors in programs?

I'll have a look at that app now. :)

---

### Post by BoomAM on 2006-06-13
Ive had a look at the program at [http://zzrough.free.fr/emifreq.php](http://zzrough.free.fr/emifreq.php), but i cant get it to install. 
And ive tryed using this guide to enable lm_sensors:
[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors)
But the guide isnt particularly clear, so im stuck.


Ideas ppl? :)

---

