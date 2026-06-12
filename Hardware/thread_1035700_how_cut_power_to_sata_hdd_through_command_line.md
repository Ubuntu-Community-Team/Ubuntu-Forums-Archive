---
title: "how cut power to sata hdd through command line"
date: 2009-01-10
forum: Hardware
---

### Post by say2sky on 2009-01-10
I have 8 hdd in my desktop pc and I need to access files inside these hdd but I also hope to save power(hdd with 12-15w/pc)

so I try to power off all the sata hdd which I don't want to access but not disconnect them.

my question is
how I can use linux command to do this and let my box become green.

for old pata hdd, hdparm have some switch to let hdd into sleep mode. how about sata hdd?


your advice and suggestion age greatly appreciated and thanks

---

### Post by IcarusR on 2009-01-10
You can use sdparm to control sata drives. Check out the man page
```
man sdparm
```

---

### Post by say2sky on 2009-01-10
> **IcarusR said:**
> You can use sdparm to control sata drives. Check out the man page
```
man sdparm
```


```

sudo sdparm -e --all /dev/sda|grep power -i
  po   0x1a       Power condition
  poo  0x0d       Power condition - old version
  P_P        [0x0a:7:8 ]  Power/performance
Power condition - old version [0xd] mode page:
Power condition [0x1a] mode page:
  DISP       [0x04:1:1 ]  Disable (unavailable) until power cycle
  SWPP       [0x04:0:1 ]  Software write protect until power cycle

```
no option for power off hdd

in fact now sata hdd is hotswap
why no simple command in ubuntu just achieve the same function of hotswap

---

