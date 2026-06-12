---
title: "Cannot return from Standby mode..."
date: 2009-07-26
forum: Hardware
---

### Post by ossian27 on 2009-07-26
Hi,

I'm a complete newb to Ubuntu. I installed yesterday and know next to nothing about Linux. I really like everything so far, and I'm working out the kinks one by one. My next conquest is to fix this problem with Standby. 

I'm using an HP Inspiron laptop with an Nvidia graphics card. I've installed all the drivers for it and everything. Whenever I go into Standby, however, I cannot come back. The screen remains black. I've seen a few other threads pertaining to this, but the proposed solutions don't seem definitive, and in any case I wouldn't be able to implement them if I tried because I'm just a beginner with Linux.

Could someone please give me a step by step on how to fix this problem? You wouldn't only be helping me, but all the other newbs as well. Thanks a million.

---

### Post by ossian27 on 2009-07-26
*bump*

---

### Post by 67GTA on 2009-07-26
You might have a look here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051) There have been a lot of HP's affected by this.

---

### Post by ossian27 on 2009-07-27
Thanks. I'll try to find something in all that that makes sense. I must admit, it looks like Greek to me. I don't know what a dsdt file is.

---

### Post by 67GTA on 2009-07-27
It's not hard. The DSDT file is hard coded into your BIOS and contains instructions for the operating system on how to interact with your hardware. You can just copy and paste the commands in a terminal. 

```
sudo apt-get install iasl
``````
sudo cat /proc/acpi/dsdt > dsdt.dat
``````
iasl -d dsdt.dat
```Then find the dsdt.dsl file in your home folder and post it as an attachment(have to zip it first). Then I will look to see if it is what is causing your wake problem and fix it. Then just finish copying/pasting the rest of the commands in the how to. This is a big problem with newer HP laptops with Nvidia chipsets. Nvidia is using a Microsoft program to create the DSDT and it breaks compatability with Linux/Mac operating systems. Most people think Linux is crap because it doesn't work right and Windows does, but most people don't understand that Microsoft is controlling them to this degree. Even if you get rid of Windows and install another OS, your still not free from Microsoft. Not nice:evil: Iasl is an open source DSDT compiler jointly made by Intel, HP, Phoenix, Toshiba, and Microsoft. Now Microsoft has created their own (MSFT) that doesn't conform to the industry standard and causes problems for every other operating system.

---

### Post by dmrkonjic on 2009-08-07
I'm also new with Linux. I instaled Ubuntu (desktop & netbook) 904 on my Acer as3810tg 354g32n and can't wake it up after going on standby.
 
I allready tried to copy/paste sudo apt-get install iasl, but it seems there is no such file... 
 
Did I miss something. Need help, please.
 
Darko

---

### Post by 67GTA on 2009-08-07
Make sure to refresh your package list. Open synaptic package manager and hit the reload button. Then search for iasl.

---

