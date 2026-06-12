---
title: "System detecting only half of RAM (4GiB) after chaging motherboard"
date: 2015-03-17
forum: Hardware
---

### Post by mohammed-moumen on 2015-03-17
Hello to all

I am a beginner on Ubuntu so please be patient with me

I have an Ubuntu 14.04 amd 64 bits Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz and BIOS A08 version. I had a total RAM size of 8 GiB before chaging my motherboard with the SAV after some problems and now the warranty has finished (they managed to give me back my laptop after warranty expires) so now I am having a motherboard : product: 0PHTY0
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: .       .CN129663BG01D2.
       slot: Type2 - Board Chassis Location

And the issue is that the system is only detecting 4GiB of RAM size now (even under win7 partition)! so I am confused if it is the motherboard that does not detect the second slot of RAM or this slot is on hardware failure or maybe there is some synchronization that is not good!

Oh, I have since this motherboard replacement the air FAN that is not stopping (I checked the CPU and other components temperature and it seemed that it is all ok since they are under the max values of allowed temperature).

Please to help me I am so lost!!!

---

### Post by QIII on 2015-03-17
I'm not finding that product designation to have a look.

Would you please issue the following command in the terminal and post back the results?

```

sudo dmidecode -t 2
```

---

### Post by tripp98 on 2015-03-18
Re-seat the memory.  
Boot to bios.  see what it reports.

---

### Post by mohammed-moumen on 2015-03-18
Hello
Thnx for reply guys,here is the return of the command line :

moumen@moumen-Inspiron-5537:/$ sudo dmidecode -t 2
# dmidecode 2.12
# SMBIOS entry point at 0x9aebef98
SMBIOS 2.7 present.

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
    Manufacturer: Dell Inc.
    Product Name: 0PHTY0
    Version: A00
    Serial Number: .       .CN129663BG01D2.
    Asset Tag: Not Specified
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Type2 - Board Chassis Location
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

@Trip : how to reseat the memory?

---

### Post by Yellow Pasque on 2015-03-19
Step 1: Update the BIOS. Your output shows A00 and that is probably not the latest. If the BIOS still reports 4GB of RAM after the update, then proceed to Step 2...

Step 2: Access the memory module(s) and make sure they're both present (and reseat them if they are present). You did not tell us what model Dell you have, but if it's the Inspiron 3537 or something similar, both memory modules are easily accessible under the battery. **Consult your manual** for instructions on accessing and reseating the RAM.

> I had a total RAM size of 8 GiB before chaging my motherboard with the SAV after some problems and now the warranty has finished (they managed to give me back my laptop after warranty expires) so now I am having a motherboard
If you sent your laptop in for repair under the warranty period and it came back with a missing RAM module, then the vendor should be responsible for sending you another memory module because they made a serious error. It should not matter to any reputable vendor if the warranty has since expired.

---

### Post by mohammed-moumen on 2015-03-19
Thank you all guys,

Inoticed something strange, I tries this morning to open my laptop to see if both memory cards are there and indeed they are present so I switched them (place one in the other's port and vice versa) and I boot my system so I went to System settings and details and the memory was 7.7 GiB (It has detected both of them) so I was glad and then I rebooted my system to be sure then there is only 3.7 GiB memory recognizable by the system!!!

Question 1 : how It could be like that => switching RAMs then system detects 8GiB then rebooting and only 4GiB is detected?
Question 2 : how can update my BIOS with Ubuntu 14.04 64 bits Dell Inspiron 5537?

---

### Post by Yellow Pasque on 2015-03-19
Boot to Windows for the BIOS update, and it will be very easy using the link: [http://downloads.dell.com/FOLDER02169988M/1/5537A08.exe](http://downloads.dell.com/FOLDER02169988M/1/5537A08.exe)

---

### Post by mohammed-moumen on 2015-03-19
[COLOR=#000000]thank you guys, It was really helpful![/COLOR]
[COLOR=#000000]I am going to let this thread opened while waiting for my laptop to be get back from the SAV (before I wrote this thread I had changed my motherboard because of some problems and now the same problem has appeared)! It seems that these days I am unfortunate![/COLOR]
[COLOR=#000000]So thank you guys, and I will get back to you as soon as I can![/COLOR]
[COLOR=#000000]best regards![/COLOR]

---

