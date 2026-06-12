---
title: "CPU running at a 1/3 of its correct speed"
date: 2009-10-16
forum: Hardware
---

### Post by bgilbert on 2009-10-16
Hi,

I am currently running Ubuntu 9.04 on a Gateway T-1628 laptop. This laptop comes with a AMD 'Turion(tm) 64 X2 Mobile Technology TL-60' processor that should be clocked at 2.0 ghz. However, I recently installed an application CPU-G which displays hardware information and was surprised to find that it had my core speed listed as 800 mhz. 

Afterwards, I looked up how to check the cpu speed in Ubuntu and found several posts that recommended the following command: 'less /proc/cpuinfo'. After running this command this information was confirmed:

-------------------
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 104
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
-------------------

Can anyone tell me if this information is maybe incorrect? And if not any recommendations on how to get more use out of my CPU? This is the only computer I've ever run Ubuntu on so I have no way of gauging whether or not the cpu is actually running at full speed or not. However if it is not, I would really like to get full use out of my cpu rather than having it operate at just over 1/3 of its capacity.

Thanks in advance!
Bryan

---

### Post by madverb on 2009-10-16
Run some cpu intensive apps and check again.

---

### Post by bgilbert on 2009-10-16
Ok, I see...sorry stupid question. It apparently only shows the current speed the cpu is running at. After running some cpu intensive operations, I saw the value increase up to 2000.

Thanks for you help!

---

