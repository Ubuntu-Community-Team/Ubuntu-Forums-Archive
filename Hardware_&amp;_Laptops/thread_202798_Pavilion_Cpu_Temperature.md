---
title: "Pavilion Cpu Temperature"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by Feanor on 2006-06-24
First of all, sorry for my ignorance in english :o 

I've a notebook hp pavilion dv1250ea with a Pentium M @ 1,6GHz processor. The problem is that it burn like hell in this period, or I don't know if is normal a temperature of 63°C @ 1400MHz :-? And also in idle state it runs at about 58~60°C. Now I'm using a fan, that blows air against the laptop and temperature is at 42°C...

So I guess if is normal in summer period, or I must beware of a possibility of overheating...

---

### Post by david_e on 2006-06-27
Did you installed the right kernel?

You should install the 686 kernel with:

```
sudo apt-get install linux-686
```

---

### Post by Hellkeepa on 2006-06-27
HELLo!

I would also like to point out the following issue, which I reckon you may be affected by:
[http://www.ubuntuforums.org/showthread.php?t=204100](http://www.ubuntuforums.org/showthread.php?t=204100)

Happy codin'!

---

### Post by Feanor on 2006-06-27
```
fabio@pavilion:~$ uname -r
2.6.15-25-686
```

Yes, I've the i686 kernel installed and running... 
I'm not affected of that issue cause my cpu doesn't work at top frequency for all the time, the scaling works fine... I can't understand why I can use my laptop to cook a dish of spaghetti #-o 

Anyway many thanks for the answers! :eek:

---

### Post by Feanor on 2006-06-27
However Hellkeepa, reading the thread I've been caught by the curiosity and I've executed the following lines too see my cpu's state:

```
fabio@pavilion:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no
fabio@pavilion:~$ cat /proc/acpi/processor/CPU0/limit
<not supported>
fabio@pavilion:~$ cat /proc/acpi/processor/CPU0/power
active state:            C2
max_cstate:              C8
bus master activity:     48889110
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[03130525]
    C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[00007884]
fabio@pavilion:~$ cat /proc/acpi/processor/CPU0/throttling
<not supported>                                   

```

Onestly, I'm not so happy of the result! :-k 
But, because of my low knowledge in this, I can't understand if is all ok anyway, or this shows a problem in my cpu...

---

### Post by Hellkeepa on 2006-06-27
HELLo!

Hmm.. Looking at the output from the "power" file, I'd say you're probably affected by the bug as well, though to a lesser degree. Also, the fact that you seem to be lacking "throttling" and "limiting" support suggest there's something else at odds in your ACPI setup, something that needs a closer look.
Unfortunately, my experience of Linux is somewhat limited to administrating server daemons, so I'm afraid I can't be of much help there. Try the workaround in my thread though, as it should reduce the temperature regardless as it forces the CPU to use less power.

Happy codin'!

---

