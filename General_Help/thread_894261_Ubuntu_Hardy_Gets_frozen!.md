---
title: "Ubuntu Hardy Gets frozen!"
date: 2008-08-19
forum: General Help
---

### Post by rakan_dr on 2008-08-19
Hi folks,
My ubuntu system got frozen 3 times through the past 2 days!!!
I feel that the problem is from the processor. When i got it frozen this day i pressed the restart button and checked the Temperature in BIOS and it was over 70C! Is that normal???
But after some seconds the temp decreased to 66C.
Is the freeze from the Heating??
Also the Motherboard Temp was 50C.
I have 2 fans, one for the processor "ASUS one" and a BIG one inside the Power Supply Unit.

I have another two doubts:
1-I use a PCI dialup modem, which of course use a properitory driver. I got it from linmodems.org
I think that the problem might be from it cuz i faced some freezes "which i had to reboot" while i was installing a driver for another PCI dialup modem.

2-I haven't got a driver for my nvidia 8500GT yet. I haven't downloaded any driver yet. I use the driver from Ubuntu "I didn't download anything"
Also the card doesn't has fan, it has just a heatsink. I'm afraid that the card makes the problem either from the Heating or from not installing the proper driver.

What do u think???

---

### Post by Sycron on 2008-08-19
> **rakan_dr said:**
> Hi folks,
My ubuntu system got frozen 3 times through the past 2 days!!!
I feel that the problem is from the processor. When i got it frozen this day i pressed the restart button and checked the Temperature in BIOS and it was over 70C! Is that normal???
But after some seconds the temp decreased to 66C.
Is the freeze from the Heating??
Also the Motherboard Temp was 50C.
I have 2 fans, one for the processor "ASUS one" and a BIG one inside the Power Supply Unit.

I have another two doubts:
1-I use a PCI dialup modem, which of course use a properitory driver. I got it from linmodems.org
I think that the problem might be from it cuz i faced some freezes "which i had to reboot" while i was installing a driver for another PCI dialup modem.

2-I haven't got a driver for my nvidia 8500GT yet. I haven't downloaded any driver yet. I use the driver from Ubuntu "I didn't download anything"
Also the card doesn't has fan, it has just a heatsink. I'm afraid that the card makes the problem either from the Heating or from not installing the proper driver.

What do u think???

LOL, for a desktop computer 70C is VERY HOT .... the normal temperature should be between 37C and 45C ...

Also your motherboard is HOT like hell... Your computer may burn one day if you don't fix the problem as soon as posible.

---

### Post by rakan_dr on 2008-08-19
OHHHHH!!! GOD HLEP ME!!!!!

What should i do for the processor and MOBO heating???????
Are u sure that the problem is from the heating??

---

### Post by rakan_dr on 2008-08-19
What is the normal temp for the MOBO??

---

### Post by Ryadt on 2008-08-19
Can you post the output of ```
acpi -V
```
and then```
top
```

---

### Post by rakan_dr on 2008-08-19
rockyrock@rockyrock-desktop:~$ acpi -V
No support for device type: thermal
rockyrock@rockyrock-desktop:~$ top

top - 13:36:58 up 11 min,  2 users,  load average: 0.59, 0.74, 0.39
Tasks: 119 total,   5 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.0%us,  5.0%sy,  0.0%ni, 82.8%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2075364k total,   431968k used,  1643396k free,    14976k buffers
Swap:  2931820k total,        0k used,  2931820k free,   232252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5539 rockyroc  20   0 58044  23m  10m S   11  1.2   0:18.24 python                                                                                          
 5088 root      20   0  296m  16m 6692 R    6  0.8   0:08.32 Xorg                                                                                            
 5505 rockyroc  20   0 18504 9920 7024 R    2  0.5   0:00.58 metacity                                                                                        
 5474 rockyroc  20   0 39952   9m 7960 S    1  0.5   0:00.48 gnome-settings-                                                                                 
13051 rockyroc  20   0 65764  18m  10m R    1  0.9   0:00.36 gnome-terminal                                                                                  
13577 rockyroc  20   0  2308 1128  852 R    1  0.1   0:00.02 top                                                                                             
 5506 rockyroc  20   0 45636  20m  12m R    1  1.0   0:01.87 gnome-panel                                                                                     
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.14 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   46 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0                                                                                       
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  141 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
  181 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  183 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                         
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 1413 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1414 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 1584 root      15  -5     0    0    0 S    0  0.0   0:00.10 ata/0                                                                                           
 1585 root      15  -5     0    0    0 S    0  0.0   0:00.02 ata/1                                                                                           
 1586 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 2281 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
 2306 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 2325 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                       
 2326 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                       
 2385 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                       
 2386 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                       
 2416 root      15  -5     0    0    0 S    0  0.0   0:00.28 scsi_eh_6                                                                                       
 2417 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_7                                                                                       
 2554 root      15  -5     0    0    0 S    0  0.0   0:00.00 kjournald                                                                                       
 2757 root      16  -4  2408  952  380 S    0  0.0   0:00.32 udevd                                                                                           
 4588 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty                                                                                           
 4589 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty                                                                                           
 4591 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty                                                                                           
 4594 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty

---

### Post by rakan_dr on 2008-08-19
What should i do for the MOBO heat?

---

### Post by Ryadt on 2008-08-19
Can you post the output of ```
uname -r
```

---

### Post by rakan_dr on 2008-08-19
rockyrock@rockyrock-desktop:~$ uname -r
2.6.24-19-generic
rockyrock@rockyrock-desktop:~$

---

### Post by rakan_dr on 2008-08-19
I also updated my BIOS today to ensure that it reads the numbers correct.

---

### Post by angryfirelord on 2008-08-19
First, check your airflow. Make sure all of your fans are working, the heatsink is latched on correctly, and if you used thermal paste, you have just the right amount.

Next, go to System-->Administration-->System Monitor and check your CPU usage. Do some of your daily tasks. If it's reading close to 100%, you may have an app that's eating up resources.

In addition...
> 2-I haven't got a driver for my nvidia 8500GT yet. I haven't downloaded any driver yet. I use the driver from Ubuntu "I didn't download anything"
Also the card doesn't has fan, it has just a heatsink. I'm afraid that the card makes the problem either from the Heating or from not installing the proper driver.
...the default nvidia driver that comes with ubuntu is called nv. For some reason, this driver seems to put a lot of extra work on your CPU. Open up Hoardware Drivers and download the nvidia driver. (nvidia-glx-new)

---

### Post by rakan_dr on 2008-08-20
> **angryfirelord said:**
> First, check your airflow. Make sure all of your fans are working, the heatsink is latched on correctly, and if you used thermal paste, you have just the right amount.

Next, go to System-->Administration-->System Monitor and check your CPU usage. Do some of your daily tasks. If it's reading close to 100%, you may have an app that's eating up resources.

In addition...

...the default nvidia driver that comes with ubuntu is called nv. For some reason, this driver seems to put a lot of extra work on your CPU. Open up Hoardware Drivers and download the nvidia driver. (nvidia-glx-new)

Thanx man,
I checked System monitor and the usage is normal.
I don't think that the driver has any relation with the heat, cuz it's over 70c!!!! and the motherboard's heat is over 50!!!

---

### Post by rakan_dr on 2008-08-20
Any new ideas?

---

### Post by rakan_dr on 2008-08-21
I've removed the Hard drive. I turned on the PC and enterd BIOS, and guess what? The CPU's temp is always over 60c! The mobo's temo is over 50c!

I tried another CPU "Intel Core 2 Duo 2.4GHz 2MB L2". The CPU's temp was 50c and Mobo's temp was 50c, but when i removed the heatsink and the processor they were so cold! I think the temp was about 10 or something!

I have ASUS P5B SE mobo, and i updated the BIOS but i get the same result!!

what should i do?

---

### Post by Sycron on 2008-08-21
> **rakan_dr said:**
> I've removed the Hard drive. I turned on the PC and enterd BIOS, and guess what? The CPU's temp is always over 60c! The mobo's temo is over 50c!

I tried another CPU "Intel Core 2 Duo 2.4GHz 2MB L2". The CPU's temp was 50c and Mobo's temp was 50c, but when i removed the heatsink and the processor they were so cold! I think the temp was about 10 or something!

I have ASUS P5B SE mobo, and i updated the BIOS but i get the same result!!

what should i do?

The 60C may be the internal CPU temperature and should not affect your system. The motherboard is very hot... Do you have your system overclocked ?

---

### Post by rakan_dr on 2008-08-22
> **Sycron said:**
> The 60C may be the internal CPU temperature and should not affect your system. The motherboard is very hot... Do you have your system overclocked ?

First, i don't think that 60 degree in BIOS without entering the OS is normal!!!! AS i said my ubuntu gets frozen!

Second, i don't have my Mobo overclocked.

---

