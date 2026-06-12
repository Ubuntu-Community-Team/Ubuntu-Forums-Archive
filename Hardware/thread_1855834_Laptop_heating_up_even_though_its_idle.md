---
title: "Laptop heating up even though its idle"
date: 2011-10-07
forum: Hardware
---

### Post by marshall1349 on 2011-10-07
I am using **ubuntu** natty.And i have a dell xps 14 with 4 gigs of ram,2gb graphics card and a core i7-740qm proc.The thing is whenever i use windows 7 the laptop works at a normal temperature but whenever i use xubuntu it heats up so drastically that the cpu temp reaches at around 75C even though its idle.At idle state there are 154 processes running with cpu usage of 2-3%,memory 11%,swap 0% but still heats up.please help.

---

### Post by Redblade20XX on 2011-10-07
Hey, can you enter these commands into the terminal and post the output of the  bold commands in your reply?

```
[B]acpi -V
[/B]sudo apt-get install lm-sensors
**sensors**
```

---

### Post by 2F4U on 2011-10-07
What graphics card is installed and what driver are you using?

---

### Post by [S|G] on 2011-10-07
A number of people have been suffering from a regression in the linux kernel that messed up power management ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)). This has been mostly noticed as a reduction in the battery lifetime on linux, but I think it might also impact on the laptop's temperature.

You might want to check if you have the latest upgrades installed and you can also try adding "pcie_aspm=force" to the kernel command line on grub, as suggested on phoronix ([http://www.phoronix.com/scan.php?page=article&item=ubuntu_linux_epb&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_linux_epb&num=1)).

---

### Post by marshall1349 on 2011-10-13
The first command gave this output:

Battery 0: Charging, 60%, 00:40:58 until charged
Battery 0: design capacity 414 mAh, last full capacity 280 mAh = 67%
Adapter 0: on-line
Cooling 0: LCD 0 of 15
Cooling 1: LCD 0 of 15
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10
Cooling 7: Processor 0 of 10
Cooling 8: Processor 0 of 10
Cooling 9: Processor 0 of 10

the second one installed some software named sensors
and the third one gave this output:No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

---

### Post by marshall1349 on 2011-10-13
I am using a Nvidia gt 425m.And i don't know about the drivers i am using.How do i find that out?

---

### Post by meatytaco on 2011-10-13
> **marshall1349 said:**
> 
the second one installed some software named sensors
and the third one gave this output:No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Try running ```
sudo sensors-detect
```
And hit yes on all of them. Run the sensors command again and see if that helps.

---

### Post by marshall1349 on 2011-10-15
I did that.hit yes on all of them.It said:

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

did it work??

---

