---
title: "Is my CPU faulty?"
date: 2014-02-01
forum: Hardware
---

### Post by carterclan2 on 2014-02-01
I recently replaced my dual core cpu for a quad core. as my mobo is a little old now the processors for an AM2+ socket are no longer made so I had to buy second hand.

The processor is an AMD Phenom X4 HD9850WCJ4BGH which is supposed to have a clock speed of 2500Mhz, but the results I'm getting from varying terminal commands are confusing me.

[I]carter@carter-desktop:~$ lscpuArchitecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 2
Stepping:              3
**CPU MHz:               1250.000**
BogoMIPS:              5000.52
Virtualisation:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
L3 cache:              2048K
NUMA node0 CPU(s):     0-3



[/I]But with:

*carter@carter-desktop:~$ sudo dmidecode -t processor | grep "Speed"**[sudo] password for carter: *
*    Max Speed: 2500 MHz*
[I]    Current Speed: 2500 MHz

[/I]
Which is what I would expect to see.

Now with:
*carter@carter-desktop:~$ cat /proc/cpuinfo | grep "MHz"*
*cpu MHz        : 1250.000*
*cpu MHz        : 2500.000*
*cpu MHz        : 1250.000*
[I]cpu MHz        : 1250.000


[/I]&#8203;Only 1 core is at full speed, I'm not sure if this is all normal or not so any advice would be appreciated.

---

### Post by tgalati4 on 2014-02-01
Install *htop* and see how the cores are loaded.  If only one core is working the others are idle, it's possible that they are throttled when idle to either reduce core temperature or to reduce power consumpution.  Install *cpuburn* and load it two, three and 4 times and then see how fast your cores are running.  Monitor your temps because your motherboard may not be rated for 4 cores.  AMD chips have a way of going pooof!

---

### Post by carterclan2 on 2014-02-01
> **tgalati4 said:**
> Install *htop* and see how the cores are loaded.  If only one core is working the others are idle, it's possible that they are throttled when idle to either reduce core temperature or to reduce power consumpution.  Install *cpuburn* and load it two, three and 4 times and then see how fast your cores are running.  Monitor your temps because your motherboard may not be rated for 4 cores.  AMD chips have a way of going pooof!


Thanks, I just ran the same commands whilst running something a little more cpu intensive than a web browser and sure enough all 4 cores are now showing 2500Mhz speed, so I guess you correct when saying they are being throttled when Idle. It's good to know that it's working as it should be :)

here is a handy command for monitoring cpu speed in real time.

sudo watch -n 1  cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq

---

### Post by tgalati4 on 2014-02-01
That is a cool script.  Thanks for sharing.  Keep an eye on your temperatures.  Make sure your heat paste is correctly applied and your fan and heat sink is clean.  A quad-core can melt down faster than you can say "What happened?".

---

### Post by carterclan2 on 2014-02-02
First thing I done was to install Psensor, all looking good. £40 well spent

---

### Post by Yellow Pasque on 2014-02-02
"It's a feature (not a bug)." The ability to adjust core speeds independently is new to the K10/Phenom architecture, so if one is coming from an older K8 chip, it can definitely be confusing.

The technical name for the feature was "Dynamic Independent Core Engagement" (DICE). Now, it's just called "Enhanced PowerNow!" technology.

Please mark thread solved.

---

### Post by mastablasta on 2014-02-03
> **carterclan2 said:**
> First thing I done was to install Psensor, all looking good. £40 well spent


wow only 40? do they make these with AM2 socket? i guess not, huh?

---

### Post by carterclan2 on 2014-02-03
> **mastablasta said:**
> wow only 40? do they make these with AM2 socket? i guess not, huh?

AM2 & AM2+ are compatible but you would have to check with the manufacturer of your motherboard as to what cpu's it can handle. I had to flash the bios on my board to the latest version to enable this one to work.

> **Temüjin said:**
> "It's a feature (not a bug)." The ability to adjust core speeds independently is new to the K10/Phenom architecture, so if one is coming from an older K8 chip, it can definitely be confusing.

The technical name for the feature was "Dynamic Independent Core Engagement" (DICE). Now, it's just called "Enhanced PowerNow!" technology.

Please mark thread solved.

Thanks for the explanation (I was never suggesting it was a bug though) I have noticed you can lock the cores to full speed by disabling AMD cool `n` quite  technology in the bios but it's a feature I like and it must surely help prolong the life of it.

---

