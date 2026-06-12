---
title: "does Ubuntu 9.04 take advantage of HyperThreading?"
date: 2009-05-20
forum: Hardware
---

### Post by KristinaK on 2009-05-20
does Ubuntu 9.04 take advantage of HyperThreading?

---

### Post by KristinaK on 2009-05-20
**[]("http://ubuntuforums.org/showthread.php?t=1165191")**[ ]("http://ubuntuforums.org/showthread.php?t=1165191")

---

### Post by Barry Carroll on 2009-05-21
Yes - as far as I know it is transparent to the OS so it just works.

---

### Post by R Clemons on 2009-05-21
Yes it does, that is handled by the linux kernel.

---

### Post by KristinaK on 2010-10-22
if it is so then why Ubuntu 10.10 doesn't take advantage of HyperThreading?

---

### Post by cascade9 on 2010-10-22
> **KristinaK said:**
> if it is so then why Ubuntu 10.10 doesn't take advantage of HyperThreading?

Why do you think 10.10 isnt using Hyperthreading?

---

### Post by KristinaK on 2010-10-22
Cause it doesn't, you can test yourself with atom N450. 

The intent of intel_idle is to allow Linux to take better advantage of Intel hardware and make Linux more immune to ACPI BIOS bugs and shorcomings of the ACPI implementation itself. 

But ubuntu 10.10 disabled this :mad:

---

### Post by cascade9 on 2010-10-22
> **KristinaK said:**
> Cause it doesn't, you can test yourself with atom N450. 

The intent of intel_idle is to allow Linux to take better advantage of Intel hardware and make Linux more immune to ACPI BIOS bugs and shorcomings of the ACPI implementation itself. 

But ubuntu 10.10 disabled this 

AFAIK 10.10 does have intel_idle, and from what I've seen around you can disable it- 

> This unfortunately appears to have an adverse affect on Lenovo S10-3 systems (Intel Atom N450 processor) rendering them incapable of booting. There currently exists a workaround. If one passes "intel_idle.max_cstate=0" as a kernel paremeter at boot, this will disable intel_idle

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/634702/+activity](https://bugs.launchpad.net/ubuntu/maverick/+source/linux/+bug/634702/+activity)

I have no idea if intel_idle is playing silly buggers with hyperthreading, and I dont have a N450 to test with. 

It would be nice to know why you think HT isnt working....it would be much nicer to put in a bug report if you've got any decent info.

---

