---
title: "Fan control with HP 6710b, need help plz"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by Dalai Llama on 2008-03-11
Hi there,

I need some help with controlling the fan of my HP 6710b Notebook. The fan starts to spin at high levels already when the CPU is at low temperature. This issue is well known in many other forums, but nowhere is a solution posted, at least none that worked for me.

To describe the situation in detail:
I am running Ubuntu Hardy Alpha 6 on my Laptop, with Intel Mobile 965GM Chipset and T7500 Core 2 Duo. So far there are no problems, everything works fine, except this problem.
The BIOS is up-to-date and it seems to be a problem with ACPI. The fan cannot be controlled via software because lm-sensors for example doesn't support this chipset (it only finds Thermal Senors for CPU 1 and 2).

So far I found 2 possible solutions for changing the fan policy:

1.: changing the dsdt-table
2.: changing temperature-values in "/proc/acpi/thermal_zone/TZ0/trip_points"

With point 1, I had multiple errors when doing the following steps:
- extracting the dsdt-table with "sudo cat /proc/acpi/dsdt > dsdt.dat"
- disassembling it with "iasl -d dsdt.dat"
- reassembling it with "iasl -sa dsdt.dsl"
This produces severel errors which can be found here (No-Paste Service from another forum): [Error Messages]("http://ubuntuusers.de/paste/73671/")
And I don't know how to fix these errors in the dsdt.dsl
Would be great if I got this to work because in there exists a passage which says:
```
Name (C393, Package (0x06)
{
0x64, => fan speed in % in Hex
0x50,
0x41,
0x32,
0x00,
0x00
}) 
```
And where I could change fan speeds used

With point 2, there exists a reported bug in launchpad: [Link]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/126447")
So I looked what "cat /proc/acpi/thermal_zone/TZ0/trip_points" says for me (because values here indicate at which temperature which fan speed will set in):
```
critical (S5):           256 C
active[0]:               82 C: devices=C3C1
active[1]:               74 C: devices=C3C2
active[2]:               66 C: devices=C3C3
active[3]:               45 C: devices=C3C4
active[4]:               30 C: devices=C3C5 
```
So what I want to do is to replace the degree values with like 45 to 85 steps of 10.
This would be great to change for the fan not to start spinning at high speeds when the CPU temperature is still quite low.

So I would be really happy :-) if someone here can help me with solving these problems,

Gerald

P.S.: I hope everything is understandable because I'm german and don't always know the best english ;-)

---

### Post by Dalai Llama on 2008-03-12
Plz, I really need help with this!!! No-one out there who can just tell me how to change the trip_points-file?

---

### Post by Dalai Llama on 2008-03-12
still nobody?

---

### Post by Dalai Llama on 2008-03-13
*bump*

---

### Post by zeller on 2008-03-13
I'm sorry, I wish I could help you out. I wouldn't have even gotten as far as you did. I want to be able to control my fans as well though.

---

### Post by cudjoe on 2008-05-22
Hi there,

I have exactly the same problem, with the same laptop under Hardy.

I tried many suggestions, but none worked so far.

**edit:**
```

cat /proc/acpi/thermal_zone/TZ0/trip_points
critical (S5):           256 C
active[0]:               80 C: devices=C3BC 
active[1]:               65 C: devices=C3BD 
active[2]:               50 C: devices=C3BE 
active[3]:               40 C: devices=C3BF 
active[4]:               30 C: devices=C3C0 

```

```

 cat /proc/acpi/thermal_zone/TZ0/polling_frequency
<polling disabled>

```


Most of the time, the fan speed is at 65 (quite noisy), unless I close everything and wait for a long time...
```

load average:  0.19, 0.26, 0.25

acpitool 
  AC adapter     : on-line
  Thermal zone 1 : activ, 55 C
  Thermal zone 2 : ok, 51 C
  Thermal zone 3 : ok, 45 C
  Thermal zone 4 : ok, 20 C
  Thermal zone 5 : ok, 65 C

```

Any news from your side ?

Thanks !

PS:
Do you guyz know if switching to another distro would help ? (I have been with ubuntu for soooo long, if only I could avoid this !)

---

### Post by gideonsmolders on 2008-05-25
I need this info too, anybody?

---

### Post by cudjoe on 2008-06-19
It looks like HP replaces the motherboard for this problem :
[http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1134500](http://forums12.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1134500)

Don't know at what cost/delay.

---

