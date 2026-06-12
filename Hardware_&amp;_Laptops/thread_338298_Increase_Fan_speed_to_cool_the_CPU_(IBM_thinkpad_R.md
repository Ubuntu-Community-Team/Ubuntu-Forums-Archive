---
title: "Increase Fan speed to cool the CPU (IBM thinkpad R52)"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by puneit on 2007-01-14
I am using Ubuntu Edgy on an IBM Thinkpad R52, (Model 1847-NQ2)
Centrino Processor 1.7 Ghz
RAM 512 MB
ATI Card

I rarely turn off my thinkpad, and many a time I feel the machine to be considerably warm.
```
puneit@puneit:/proc/acpi/ibm$ cat thermal 
temperatures:   89 63 45 74 41 -128 33 -128

```
At the time of writing this post, the temperatures were as above and the fan speed is as follows
```
puneit@puneit:/proc/acpi/ibm$ cat fan
status:         enabled
speed:          4488
commands:       enable, disable

```
The CPU details are 
```
puneit@puneit:/proc/acpi/processor/CPU$ cat info 
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

```
```
puneit@puneit:/proc/acpi/processor/CPU$ cat limit 
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0

```
```
puneit@puneit:/proc/acpi/processor/CPU$ cat power 
active state:            C1
max_cstate:              C8
bus master activity:     00000000
states:
   *C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00000000] duration[00000000000000000000]
    C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[00000000] duration[00000000000000000000]

```
```
puneit@puneit:/proc/acpi/processor/CPU$ cat throttling 
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

```

```
puneit@puneit:/proc/acpi/processor/CPU$ lsmod | grep ibm
ibm_acpi               28672  0 

```
How do I cool my machine down? Will increasing the fan speed help? If yes, then how do I do it?
I have read about lm-sensors not being compatible with Thinkpads. And was not able to install  them in Dapper. 
Even if I install lm-sensors, the sensors will only display the temperatures and fan speed, right! It won't help me change it


PS.  I use the thinkpad on a wodden table. Its winter in India, room temperature with heating on would be 25-26C.
So, I cannot even blame the temperature on Indian heat.
Should I be worrying since the temperatures are around 89C
Can someone guide me how to get the temperature on a cooler side?

---

### Post by dcherryholmes on 2007-04-17
Bump.  And thanks for the informative post detailing the problem.  It at least gave me more things to look at on my R52 and values for comparison (mine are roughly similar to yours).

---

### Post by puneit on 2007-04-17
Well I could increase the fan speed... 
I found a way (with the help of thinkwiki.org) to run the fan in dis-engaged mode, where it runs at its maximum speed. After some days, the fan started giving a buzzing sound, so I switched back to normal mode. Now, with summers set in and with air-conditioners and fans running, I guess there is a better circulation of air around the notebook which is keeping the temperatures around 60C.

```

echo 0x2F 0x00 | sudo tee /proc/acpi/ibm/ecdump  #(fan off) 
 echo 0x2F 0x02  | sudo tee /proc/acpi/ibm/ecdump #(low speed) 
 echo 0x2F 0x04  | sudo tee /proc/acpi/ibm/ecdump #(medium speed) 
 echo 0x2F 0x07  | sudo tee /proc/acpi/ibm/ecdump # (maximum speed) 
 echo 0x2F 0x80  | sudo tee /proc/acpi/ibm/ecdump #(automatic - default) 
 echo 0x2F 0x40  | sudo tee /proc/acpi/ibm/ecdump #(disengaged) 

```
Now you may use this at your own risk. Kindly do not try to turn off the fan. The processor will fry in a matter of minutes. Moreover, you need to run these commands at the terminal everytime you reboot because the system restores it back to default. 
I hope this helps

---

