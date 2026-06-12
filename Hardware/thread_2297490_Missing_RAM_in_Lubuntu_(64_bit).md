---
title: "Missing RAM in Lubuntu (64 bit)"
date: 2015-10-04
forum: Hardware
---

### Post by lambertodellelce on 2015-10-04
Hello,

I have a problem with a fresh install of Lubuntu 15.04 (64 bit). I hope I can post this issue in this forum.

I used to have Ubuntu  15.04 (64 bit) on my laptop, and I replaced it with its Lubuntu counterpart. I chose the "erase disk and reinstall" option for this purpose.

In Ubuntu, the available memory was roughly 4 GB (both checked by means of free -m and MemTotal in meminfo), which is consistent with the installed memory in the laptop.


After installing Lubuntu I can just see about 2.5 GB.


I was thinking about a hardware issue, but the weird thing is that if now I boot the laptop with the live usb of Ubuntu, I can still see the 4 GB of ram (which is not the case if I boot with the live usb of Lubuntu).


Does anyone have an idea why it happens?

---

### Post by MartyBuntu on 2015-10-04
How much RAM is physically installed in the machine?

---

### Post by lambertodellelce on 2015-10-04
4 GB are installed.

---

### Post by MartyBuntu on 2015-10-04
How much RAM is dedicated to video (a setting in your BIOS)?

---

### Post by lambertodellelce on 2015-10-04
I think that I cannot access this information on my laptop (Thinkpad Twist S230u). The bios provides the installed memory only (4096 MB). In addition, I ran the lenovo "quick memory test" (available in the bios menu) which states: Total memory: 4063 MB, Available memory: 3728. Is the memory dedicated to video given by their gap?

If this can help, I post the outputs of "free -m" and "cat /proc/meminfo | grep MemTotal" in the two cases:

With Ubuntu (live usb):
```

 ubuntu@ubuntu:~$ free -m    total       used       free     shared    buffers     cached
Mem:                          3769       1835       1934        688        134       1184
-/+ buffers/cache:                        515       3254
Swap:                         2647          0       2647
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ cat /proc/meminfo | grep MemTotal
MemTotal:        3860448 kB
```

With Lubuntu (not the live usb, but the result is the same):
```

lamberto:~$ free -m    total       used       free     shared    buffers     cached
Mem:                    2527        927       1600         80         69        374
-/+ buffers/cache:                  483       2044
Swap:                   2647          0       2647
lamberto:~$
lamberto:~$ cat /proc/meminfo | grep MemTotal
MemTotal:        2588368 kB
```


If the problem is the memory dedicated to video, shouldn't I get the same available memory in the two cases?

---

### Post by Yellow Pasque on 2015-10-04
Did you update the Lubuntu install? If so, do you know how much memory it showed before updating? What kernel are you running on Lubuntu?
```
uname -a
```

You may want to compare memory maps on each install to see what changes:
```
dmesg | grep e820
```

> Is the memory dedicated to video given by their gap?

~1.2GB for integrated video memory? That seems farfetched.

---

### Post by lambertodellelce on 2015-10-05
>  [COLOR=#000000][FONT=Ubuntubeta]Did you update the Lubuntu install? If so, do you know how much memory it showed before updating? What kernel are you running on Lubuntu?[/FONT][/COLOR]

Yes, I did, the kernel I am running on is 
```

Linux lambertodellelce 3.19.0-30-generic #33-Ubuntu SMP Mon Sep 21 20:58:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I do not have the amount of memory before the update. However, if I boot with the Lubuntu live USB I still get ~2.5 GB. The Lubuntu live USB runs on kernel
```

Linux lubuntu 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

>  [COLOR=#000000][FONT=Ubuntubeta]You may want to compare memory maps on each install to see what changes:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR]By booting on the laptop's Lubuntu installation I get:
```

lamberto:~$ dmesg | grep e820[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000875f0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000875f1000-0x00000000dae9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dae9f000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ff000fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011e5fffff] usable
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x11e600 max_arch_pfn = 0x400000000
[    0.000000] e820: last_pfn = 0x875f1 max_arch_pfn = 0x400000000
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    1.059732] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    1.059735] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.059737] e820: reserve RAM buffer [mem 0x875f1000-0x87ffffff]
[    1.059739] e820: reserve RAM buffer [mem 0x11e600000-0x11fffffff]

```

On the contrary, by booting on the Ubuntu's live USB I get:
```

 ubuntu@ubuntu:~$ dmesg | grep e820[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000090000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x0000000089c2bfff] usable
[    0.000000] BIOS-e820: [mem 0x0000000089c2c000-0x0000000089e2dfff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000089e2e000-0x00000000d6813fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d6814000-0x00000000d6a13fff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000d6a14000-0x00000000dae9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dae9f000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db000000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f80f8000-0x00000000f80f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011e5fffff] usable
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x11e600 max_arch_pfn = 0x400000000
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] e820: [mem 0xdfa00000-0xf80f7fff] available for PCI devices
[    1.118851] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.118854] e820: reserve RAM buffer [mem 0x89c2c000-0x8bffffff]
[    1.118855] e820: reserve RAM buffer [mem 0xd6814000-0xd7ffffff]
[    1.118857] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    1.118859] e820: reserve RAM buffer [mem 0x11e600000-0x11fffffff]

```


However, understanding memory maps is beyond my skills, can you help me to get insight into these outputs?

For the sake of completeness, the command "[COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep e820[/FONT][/COLOR]" on the Lubuntu live USB yields:
```

lubuntu@lubuntu:~$ dmesg | grep e820[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000875f0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000875f1000-0x00000000dae9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dae9f000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ff000fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011e5fffff] usable
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x11e600 max_arch_pfn = 0x400000000
[    0.000000] e820: last_pfn = 0x875f1 max_arch_pfn = 0x400000000
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    1.075182] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    1.075184] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.075186] e820: reserve RAM buffer [mem 0x875f1000-0x87ffffff]
[    1.075188] e820: reserve RAM buffer [mem 0x11e600000-0x11fffffff]

```


which, again, seems to be consistent with the Lubuntu's laptop installation (I just checked by comparing the two outputs with meld :D).

---

### Post by Yellow Pasque on 2015-10-06
> However, if I boot with the Lubuntu live USB I still get ~2.5 GB

So the Lubuntu and Ubuntu Live iso's both use the same kernel and give different results? That's strange. I don't have any explanation for that.

---

### Post by lambertodellelce on 2015-10-06
I did not check the Ubuntu kernel, but it is more likely that it is the same of the Lubuntu desktop installation, since I generated the bootable Ubuntu usb after that I realized this issue.

Edit: I checked the Ubuntu Live kernel, it is 3.19.0-25-generic. Nonetheless, I never experienced this problem with Ubuntu before (and I used to have Ubuntu on this machine since two or three years) so I am quite confident that it is not a kernel related problem.

---

### Post by lambertodellelce on 2015-10-07
I possibly found the source of the problem. I post it here in case anybody has the same issue.

I used two different USB drives to generate the Lubuntu and Ubuntu Live installations. I found out that the Ubuntu's one was formatted as FAT, while the Lubuntu one was Ext4. Now I tried to make a new Lubuntu Live on a FAT drive. When I boot my laptop with this new drive the available memory is 3.7GB.

I will try to install Lubuntu on the laptop by means of this new key in the next days to see if the problem is completely solved.

Beside this potential fix, I am interested in knowing how the format of the bootable device affects memory maps and why this map persits after installing the distribution. Does anyone have an idea?

A final remark, I used the previous Lubuntu Live USB to install Lubuntu on another PC, but in that case I did not have this issue.




Edit: I confirm that I could fix the issue by reinstalling Lubuntu with the new live USB.

---

