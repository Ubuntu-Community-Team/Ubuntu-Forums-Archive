---
title: "Multiple CPUs not recognised"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by twofruits on 2007-02-14
Hi All,

I've just installed 6.06 on a three year old dual xeon 2.8ghz server, then upgraded it to 6.10.

I've noticed that it doesn't seem to be using both CPUs, if I have a look in /proc/cpuinfo it reports only one processor, with the following details

processor :0
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xenon(TM) CPU 2.80ghz
stepping : 9
cpu MHZ : 2799.658
... plus other details

Is there anything I need to do to enable multiple CPU support, pass in a boot parameter to the kernel ?

I've also just noticed the same problem on a dual core laptop I've just installed 6.10

Thanks

---

### Post by Motoxrdude on 2007-02-14
Do you have the generic kernal right now?
Did you install from 6.06 to 6.10 or a fresh install of 6.10?
You need a kernal with SMP support, but the generic kernal that edgy uses should have that included.

---

### Post by maxamillion on 2007-02-14
```
uname -r
```

paste the result of that command when run in the terminal

---

### Post by twofruits on 2007-02-14
> **maxamillion said:**
> ```
uname -r
```

paste the result of that command when run in the terminal

result (from dual Xenon Server) = 2.6.17-11-386

result (from dual core laptop) = 2.6.17-10-386

On the Xenon, I installed from 6.06, then upgraded to 6.10.
On the laptop I installed directly from 6.10

---

### Post by Motoxrdude on 2007-02-14
Yeah, there is your problem. You need to install the 686 kernal which has SMP support. Go into the synaptic package manager and look up "686" and install the 686 kernel and it should install all the dependacies for it.

Sorry, i am kinda in a rush and i haven't done this in awhile so i can't remember details. If you need more help, i will be back in two hours.

---

### Post by twofruits on 2007-02-14
Thanks guys,

Installing the 686 kernel fixed it. My Xenon server is now report 4 cpus. Awesome.

---

### Post by paddydd on 2007-12-04
Do you need the 686 with two processors where it states that they are dual core?
I have the same config with only 2 procs.

Thanks
Paddy

---

