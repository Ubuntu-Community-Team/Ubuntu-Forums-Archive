---
title: "CPU fan on full speed"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by dema on 2008-02-24
I've a laptop with a Dual Core CPU. The CPU fan are always on full speed - even if there are no working programs. How can I change this?

---

### Post by insanet on 2008-02-24
well first you want to get a program like cpu-z to test if your cpu is too hot maybe someone else would be able to point you too an ubuntu equivalent afterwards if you deem your cpu running at an ok temperature there is overclocking software which you can use to change the fan speed again i dont know much ubuntu software i am fairly new but you could go with NVClock [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

---

### Post by Existentialist on 2008-02-24
Actually cpu-z does not read cpu temps, but for linux you can run:

acpi -t 
or
acpi -V

You can also install and run lm-sensors by:

sudo apt-get install lm-sensors

Let us know what kind of cpu temps you are getting.

---

### Post by dema on 2008-02-25
> **Existentialist said:**
> Actually cpu-z does not read cpu temps, but for linux you can run:

acpi -t 
or
acpi -V

You can also install and run lm-sensors by:

sudo apt-get install lm-sensors

Let us know what kind of cpu temps you are getting.

I've now installed lm-sensors. How can I use is?

---

### Post by adrien214 on 2008-02-25
enter the following command in a terminal:

```
 sensors 
```

Besides, you should post the details of your hardware along with your question, otherwise you might be directed to wrong instructions/solutions. Do you have Intel or AMD ?

Forget NVclock and using acpi commands might give you the temps of your mobo and not CPU.

There are plenty of posts with your issue, better do a forum search, you have more chance of getting an answer...

---

### Post by dema on 2008-02-25
> **adrien214 said:**
> enter the following command in a terminal:

```
 sensors 
```

Besides, you should post the details of your hardware along with your question, otherwise you might be directed to wrong instructions/solutions. Do you have Intel or AMD ?

Forget NVclock and using acpi commands might give you the temps of your mobo and not CPU.

There are plenty of posts with your issue, better do a forum search, you have more chance of getting an answer...

I get this:
```
dennis@dennis-laptop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

I've tried to run sensors-detect, but how long time should it run before finishing?

Which commands can I post for you, to give you my laptops specifications?
I've seached this forum for posts about this problem - but I didn't find a solution.

---

### Post by Spxza on 2008-04-06
I am having a similar issues with my noisy fan. Output of acpi -t gives me:
```
Thermal 1: ok, 4294967040.0 degrees C
```
I am in africa, but that is a bit warm for even here. I'll poke around and put some more info here. 
Oh, and /proc/acpi/thermal_zone/temperature is -268 C. Hmmm...

---

