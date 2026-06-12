---
title: "High CPU usage"
date: 2008-08-16
forum: General Help
---

### Post by gamergeek10 on 2008-08-16
I hope this is the right place for this...

So, recently I noticed that while I was playing some music through rhthmbox that it was skipping a little.  Just out of curiosity I ran top and noticed that there were three things taking up between 85-98% cpu >.<. 

Next, I checked the system monitor but it doesn't show a large chunk of cpu being used on any of the processors.  I've looked everywhere and no one else seems to have had this problem.

```
 

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  1475 root     -51  -5     0    0    0 R   93  0.0   2851:29 IRQ-16             
 1610 root     -51  -5     0    0    0 R   89  0.0   2730:03 IRQ-17             
 1792 root     -51  -5     0    0    0 S   88  0.0   2679:29 IRQ-18             
17833 gabriel   20   0  213m  23m  13m S    5  1.2   0:04.23 gnome-system-mo    
 5670 root      20   0  511m  75m  23m S    5  3.8  28:06.26 Xorg               
17563 gabriel   20   0  507m 105m  25m S    1  5.3   0:28.05 firefox            
    6 root     -51  -5     0    0    0 S    0  0.0   9:25.12 softirq-timer/0    
   19 root     -51  -5     0    0    0 S    0  0.0   3:38.80 softirq-timer/1    
   32 root     -51  -5     0    0    0 S    0  0.0   7:06.76 softirq-timer/2    
 5569 root      20   0 24156 1276 1072 S    0  0.1   0:08.11 hald-addon-stor    
17859 gabriel   20   0  258m  23m  11m S    0  1.2   0:00.38 gnome-terminal     
17879 gabriel   20   0 18992 1320  932 R    0  0.1   0:00.03 top                
    1 root      20   0  4020  880  592 S    0  0.0   0:00.88 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/0  


```

The problem is those 3 roots at the top.  I don't know what they are or what they're doing.  System monitor shows them as sleeping and I've tried to end and kill them but they don't respond.  And even though the system monitor shows little cpu usage they're definitely slowing my computer down.

Help plz =D

---

### Post by elasto1mania on 2008-08-16
Go to your bios and change irq numbers of devices that might help.

---

### Post by Diabolis on 2008-08-16
> PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  **1475** root     -51  -5     0    0    0 R   93  0.0   2851:29 **IRQ-16**             
 **1610** root     -51  -5     0    0    0 R   89  0.0   2730:03 **IRQ-17**             
 **1792** root     -51  -5     0    0    0 S   88  0.0   2679:29 **IRQ-18**    

You can try to kill them with the kill command using their PIDs. Example:
```
kill -9 1475
```

Interrup requests (IRQ) are used by hardware devices to tell the CPU that they need it.

Maybe you can see what is causing this problem with this command:
```
dmesg | grep irq
```

---

### Post by tgalati4 on 2008-08-16
Examine or post the output of:

cat /proc/interrupts

You may have a hardware problem or a conflicting interrupt (for example the network card and sound card are sharing an interrupt).  This would cause an issue when listening to streaming music from the net.

---

### Post by gamergeek10 on 2008-08-16
I've tried to kill them before and that didn't work.  If I do a complete shutdown and then restart my computer they go away.  So I'm not having any problems with it right this moment.  So, I'll have to wait now to try some of the other suggestions everyone has mentioned.  But thank you very much for the help thus far...I at least have some new things to try should it happen again.

---

