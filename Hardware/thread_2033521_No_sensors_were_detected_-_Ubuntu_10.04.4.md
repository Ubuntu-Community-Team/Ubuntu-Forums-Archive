---
title: "No sensors were detected - Ubuntu 10.04.4"
date: 2012-07-26
forum: Hardware
---

### Post by NikTh on 2012-07-26
Hello , 
first of all , i know that 10.04.4 its an old ubuntu version , but its still supported. 
I want to use it until the end. (April 2013). 

My laptop is an Acer Aspire 5733 . 

I also have Ubuntu 12.04 LTS , and there everything work ok. Sensors detected correctly and run. 

In 10.04 i have the known problem "Sorry , no sensors were detected " when i run **sudo sensors-detect** . 

I only want to know my cpu temp.. nothing more. I tried acpi , but acpi -v returns this 
```
Battery 0: Discharging, 53%, 01:23:54 remaining
Battery 0: design capacity 4400 mAh, last full capacity 4017 mAh = 91%
Adapter 0: off-line
Cooling 0: LCD 7 of 9
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
```I even copied all the hwmon library from 3.2 kernel to 2.6 , but coretemp.ko refuses to load ```
sudo modprobe -v coretemp 
insmod /lib/modules/2.6.32-41-generic/kernel/drivers/hwmon/hwmon/coretemp.ko 
FATAL: Error inserting coretemp (/lib/modules/2.6.32-41-generic/kernel/drivers/hwmon/hwmon/coretemp.ko): Invalid module format
```**same message showed up _before_ the copy**.. (form 3.2 kernel) . 

I also installed linux-backport-modules.. i managed to fix the wireless issue  , but not sensors issue. 
If you want additional info , let me know. 

I will be grateful to anyone help me to manage this out. 

Thanks

---

### Post by NikTh on 2012-07-26
Hi , 

Success !! 

Ok , i came back for some correction . 
I  downloaded the package of lm-sensors from here --> [http://packages.ubuntu.com/precise/lm-sensors](http://packages.ubuntu.com/precise/lm-sensors) . 
Installed with dpkg -i 
```
sensors -v
sensors version 3.3.1 with libsensors version 3.1.2
```After some research and tests , i realized that its not only the package you must install. 
I tested some newer kernels and i came to the conclusion that need to install latest mainline kernel 3.5.0 , from here --> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.5-quantal/") 
at least this worked for me. 

Everything running smoothly , sensors detected correctly and are up and running. 

Thanks

---

