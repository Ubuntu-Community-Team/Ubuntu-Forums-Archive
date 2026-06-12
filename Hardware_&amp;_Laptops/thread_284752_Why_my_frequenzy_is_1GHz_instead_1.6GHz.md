---
title: "Why my frequenzy is 1GHz instead 1.6GHz"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by lugburz on 2006-10-26
My CPU seems working to 1 GHz instead 1.6 GHz, this a part of my /proc/cpuinfo:

model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000

Why?:???: [-(

---

### Post by aidanr on 2006-10-26
try turning off "CPU Frequency manager (powernowd)" in System -> Administration -> Services

---

### Post by lugburz on 2006-10-26
You are a genius!!!!

now the question is: where is(are) the configuration file(s) for powernowd? because my cpu now was working at low voltage when I'm wired but problably I want reduce the cpu speed when I use the battery.

---

### Post by girishv on 2006-10-26
Hi,
restart the powernow again. It will do what you are looking for. It will stepdown the CPU when not in use (mean, when you donot need its full power) and start using the full potential as and when the need arises.

Girish

---

### Post by lugburz on 2006-10-26
Uhm.... I would trust you but after the upgrade from dapper to edgy I have the sensation that my laptop was slower than before, stopping powernowd cancel this sensation.

In any case I will restart it as test.

---

