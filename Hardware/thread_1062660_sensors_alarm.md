---
title: "sensors alarm"
date: 2009-02-07
forum: Hardware
---

### Post by pacman401 on 2009-02-07
witch one device has that warn ?

```
~$ sensors
adm1025-i2c-0-2d
Adapter: SMBus I801 adapter at e480
+2.5V:       +1.50 V  (min =  +0.00 V, max =  +3.32 V)   
VCore:       +1.47 V  (min =  +0.00 V, max =  +2.99 V)   
+3.3V:       +3.28 V  (min =  +0.00 V, max =  +4.38 V)   
+5V:         +5.03 V  (min =  +0.00 V, max =  +6.64 V)   
+12V:        +0.00 V  (min =  +0.00 V, max = +15.94 V)   ALARM
VCC:         +3.30 V  (min =  +0.00 V, max =  +4.38 V)   
CPU Temp:    +25.0°C  (low  =  +0.0°C, high = +127.0°C)  
M/B Temp:    +26.0°C  (low  =  +0.0°C, high = +127.0°C)  
cpu0_vid:   +1.500 V

smsc47m1-isa-0680
Adapter: ISA adapter
fan1:       2857 RPM  (min =  640 RPM, div = 8)
fan2:          0 RPM  (min =  640 RPM, div = 8)


```

---

### Post by Yashiro on 2009-02-10
It cannot read your +12V reading on your PSU.

---

### Post by pacman401 on 2009-02-10
oh yes i probable have a little panic :P I am sorry I will look harder in log for a next time.

---

