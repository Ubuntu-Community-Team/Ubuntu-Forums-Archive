---
title: "LIRC Infrared on Thinkpad t60"
date: 2008-08-31
forum: Hardware
---

### Post by flacone on 2008-08-31
I installed the lirc package like in [http://www.lirc.org/html/install.html](http://www.lirc.org/html/install.html)
I selected io=2f8 and irq=3. But dmesg gives following:
```

[   46.169297] lirc_dev: IR Remote Control driver registered, at major 61 
[   46.207793] lirc_dev: lirc_register_plugin: sample_rate: 0
[   46.207822] lirc_sir: I/O port 0x03e8, IRQ 4.
[   46.207839] lirc_sir: Installed.

```
So I get nothing with
```
sudo mode2 -d /dev/lirc0 
```

I tried the cmd 
```
modprobe lirc_sir io=0x02f8 irq=3
```

But this had no effect.

I hope anyone has an idea what else I can try.
thx

---

### Post by flacone on 2008-08-31
okay; i removed the module with
```
sudo rmmod lirc_sir
```

and added again with
```
sudo modprobe lirc_sir io=0x2f8 irq=3
``` 

It says device is busy
so i tried 
```
setserial /dev/ttyS0 uart none
```

but this does not help.
so i removed the nsc-ircc
```
sudo rmmod nsc-ircc
```

and added lirc-sir
```
sudo modprobe lirc_sir io=0x2f8 irq=3
``` 

this worked but no signal with
```
sudo mode2 -d /dev/lirc0 
```

Now i really do not now what to do. Please help.


[http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA#LIRC_and_IrDA](http://www.thinkwiki.org/wiki/How_to_make_use_of_IrDA#LIRC_and_IrDA)

---

### Post by Blaimi on 2008-12-11
I have the same Problems on a X60t

There's no output at *mode2* or *irw*

Blaimi

---

