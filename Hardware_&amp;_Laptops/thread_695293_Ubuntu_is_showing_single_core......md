---
title: "Ubuntu is showing single core....."
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by WebEyeX on 2008-02-12
Hi,
I have Intel Pentium D processor.I have to disable acpi (first when i installed Ubuntu 7.10,second when 60-70% CPU was being used by some process continuously).Now after disabling acpi in grub menu list Ubuntu is showing only one core of my Dual core processor.I searched a lot about this problem but could not found proper solution.I am looking forward to you guys...

Thanks and Regards.

---

### Post by PaulFr on 2008-02-12
In a command shell, please type the following command:```
dmesg | grep CPU
``` and post the output here so someone can take a look.

---

### Post by WebEyeX on 2008-02-13
Here is the output of  dmesg | grep CPU ---

[    0.000000] Initializing CPU#0
[   35.402589] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   35.482968] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   35.483057] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   35.483119] CPU: L2 cache: 2048K
[   35.483156] CPU: Physical Processor ID: 0
[   35.483193] CPU: Processor Core ID: 0
[   35.483230] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e49d 00000000 00000001
[   35.783531] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   35.998415] Brought up 1 CPUs
 

As you can see it is showing and using only one core of Dual core processor...

---

### Post by PaulFr on 2008-02-14
Some ideas for you:

1. Can you verify that your BIOS settings are okay ? In particular, look at the power management setup to ensure:> a. ACPI:              Disabled
b. POWER MANAGEMENT:  Disabled
c. PM CONTROL by APM: No2. Can you try "noapic acpi=no" boot options and see if that works ?

3. Are there any errors / failure messages in the dmesg output ?

Here's a link **[http://www.centos.org/modules/newbb/viewtopic.php?post_id=26073&topic_id=8233](http://www.centos.org/modules/newbb/viewtopic.php?post_id=26073&topic_id=8233)**.

---

### Post by WebEyeX on 2008-02-15
[QUOTE=PaulFr;4328183]Some ideas for you:

1. Can you verify that your BIOS settings are okay ? In particular, look at the power management setup to ensure:2. Can you try "noapic acpi=no" boot options and see if that works ?

Yes i have checked BIOS settings.ACPI is set to state3(I do not know what it is?)

3. Are there any errors / failure messages in the dmesg output ?

No i can not figure out any error.


As I mention above Ubuntu is showing single core only if i am using 'noapic acpi=no' parameter.I can boot without using 'acpi=no' then it shows both core now some process eat up 70% of valueable CPU.I think acpi is creating this problem...

In short my problem is 
1-If i boot with acpi=no,Ubuntu shows and use only one core of CPU.
2-If i boot without acpi=no,some process is using my 70% CPU.

And i can not work without acpi features,i can not work with only 30% CPU.And i can not live without Ubuntu.


So what shoul i do now...Need some suggestions and help from you champs..(I know we have lots of here.)


Thanks and Regards

WebEyeX

---

### Post by WebEyeX on 2008-02-17
I just used 'noapic' boot parameter and now i can see both core of my CPU.But here is another problem now i am unable to play any video or audio file.Whenever i try to play any  video or audio file('.mp3','.wmv','.dat' etc..) player just get hang. 

Ha.:).Problems..Problems..Problems..and our love to Ubuntu.........

Any help will be appreciated.

Thanks and Regards.

WebEyeX

---

