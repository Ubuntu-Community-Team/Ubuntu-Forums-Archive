---
title: "Do I have 32 bit or 64 bit?"
date: 2010-12-09
forum: Hardware
---

### Post by Megaptera on 2010-12-09
Just run

lscpu
cat /proc/cpuinfo


 and this was the line that puzzled me (it's a cut & paste) 


CPU op-mode(s):        32-bit, 64-bit


so what do I have here? 32-bit or 64-bit? 

Thanks.

---

### Post by WienerWuerstel on 2010-12-09
Open a Terminal and enter the Command *uname -a* and you will see what Kernel and Architecture you run.

---

### Post by Megaptera on 2010-12-09
Thanks:

Linux Home 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

but what does that entry I originally posted signify please?

---

### Post by Decatf on 2010-12-09
Your CPU supports 64-bit and 32-bit. You are running the 32-bit version of Ubuntu.

---

### Post by I'mGeorge on 2010-12-09
post all the output of 
```

lscpu

```

---

### Post by amauk on 2010-12-09
You have a 64bit CPU (x86_64)

---

### Post by Megaptera on 2010-12-09
To:
WienerWuerstel
Decatf
I'mGeorge
amauk

Thanks to all of you for solving that for me, much appreciated.

---

### Post by karthick87 on 2010-12-09
Run this in terminal to know whether you have 32 bit or 64 bit

```
getconf LONG_BIT 
```

[B]Sample output:
[/B]```
karthick@Ubuntu-desktop:~$ getconf LONG_BIT 
32

```

---

### Post by Megaptera on 2010-12-10
> **I'mGeorge said:**
> post all the output of 
```

lscpu

```

Here it is:

lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               2167.000
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K

---

### Post by Megaptera on 2010-12-10
> **karthick87 said:**
> Run this in terminal to know whether you have 32 bit or 64 bit

```
getconf LONG_BIT 
```

[B]Sample output:
[/B]```
karthick@Ubuntu-desktop:~$ getconf LONG_BIT 
32

```

and the answer there was 32    so now I'm very confused, what have I misunderstood please?

Thanks.

---

### Post by racie on 2010-12-10
i686 is in the 32-bit family.

If you were running 64-bit, you would get an output like 'x86_64.'

---

### Post by karthick87 on 2010-12-10
Mine is 32 bit,so it returned 32.If your system is 64 bit then it will return 64.Check yours by running the following command in terminal.
```

getconf LONG_BIT
```

---

### Post by Megaptera on 2010-12-10
> **karthick87 said:**
> Mine is 32 bit,so it returned 32.If your system is 64 bit then it will return 64.Check yours by running the following command in terminal.
```

getconf LONG_BIT
```

As per #10 above, double-checked and I get:

getconf LONG_BIT
32

So I guess it's 32 bit but still puzzled why some also read it as 64 bit.

Once again, thanks.

---

### Post by Megaptera on 2010-12-10
Thanks karthick87 and racie !!

---

### Post by racie on 2010-12-10
> **Megaptera said:**
> So I guess it's 32 bit but still puzzled why some also read it as 64 bit.

Well, I'm assuming that the output of CPU op modes just means that you can run either 32-bit or 64-bit operating systems on your computer.  Although it seems a bit strange because my only output is 64-bit, but I am able to run 32-bit operating systems.

---

