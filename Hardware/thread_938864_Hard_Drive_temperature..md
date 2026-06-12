---
title: "Hard Drive temperature."
date: 2008-10-05
forum: Hardware
---

### Post by Soupcan on 2008-10-05
I recently had to use the Hardy Heron "Ugly fix" for the Load Cycle Count bug. I was told I should monitor my HD temperature, so I installed hddtemp. When I use: ```
sudo hddtemp /dev/sda
``` it says my drive has no sensor. However, when I use ```
sudo smartctl -a /dev/sda | grep Temperature 
``` it outputs this: ```
190 Temperature_Celsius     0x0022   063   049   000    Old_age   Always       -       621871141
```
The number at the end, which I assume is the temperature, varies from 600000000-750000000. Can anyone explain what is happening?

---

### Post by BrigTSD on 2008-10-05
It seems like your hard drive sensor is not supported by hddtemp and smartctl. Do you have S.M.A.R.T enabled in the bios settings?

---

### Post by Soupcan on 2008-10-05
I'm not sure. How do I enable it in the BIOS?

---

### Post by amiller2571 on 2008-10-05
What kind of computer do you have. Dell, hp...
If you built it then what is the motherboard?

---

### Post by BrigTSD on 2008-10-05
> **Soupcan said:**
> I'm not sure. How do I enable it in the BIOS?

Usually the bios settings are accessed by pressing "del" or "F2" during the bios boot. The best (and safest) way is to consult the motherboard manual before any settings are changed. All bios parameters are described there.

But I think you already have S.M.A.R.T enabled. Otherwise I think smartctl does not return anything. Does the other data smartctl returns make sense?

---

### Post by Soupcan on 2008-10-05
> **BrigTSD said:**
> Usually the bios settings are accessed by pressing "del" or "F2" during the bios boot. The best (and safest) way is to consult the motherboard manual before any settings are changed. All bios parameters are described there.

But I think you already have S.M.A.R.T enabled. Otherwise I think smartctl does not return anything. Does the other data smartctl returns make sense?

Yes, everything else makes sense. 
The number that grep Temperature puts out also seems to be measuring something, showing a higher number when the computer feels hotter. But it doesn't actually make sense.

In response to amiller2751:
I have a HP dv6000. I don't know the exact number; something like 6933cl.

---

### Post by Soupcan on 2008-10-06
Bump, in case anyone has any ideas.

---

### Post by tgalati4 on 2008-10-06
Yes, it does look like SMART is measuring temperature.  You need to get the exact model number of your drive (should be near the top of the smartctl -a /dev/sda output).  Do a google search to see if you can find any insight into the SMART decoding.  There is typically a mapping between the SMART values and real temperature.  I have a desktop computer that simply puts out a 2 digit code that represents real C degrees (44).

You can also monitor battery temperature (do a forum search).  Sometimes the battery gets too hot and shuts down causing disk problems.

---

### Post by Soupcan on 2008-10-06
> **tgalati4 said:**
> Yes, it does look like SMART is measuring temperature.  You need to get the exact model number of your drive (should be near the top of the smartctl -a /dev/sda output).  Do a google search to see if you can find any insight into the SMART decoding.  There is typically a mapping between the SMART values and real temperature.  I have a desktop computer that simply puts out a 2 digit code that represents real C degrees (44).

You can also monitor battery temperature (do a forum search).  Sometimes the battery gets too hot and shuts down causing disk problems.

Thank you. It seems that my HD has a temperature of either 49 or 60C at the moment. Is that too hot? I don't know the tolerances of my drive, and I haven't been able to find them.

Also, does anybody have any idea as to why smartctl returns a value for temp, but hddtemp does not?

---

### Post by tgalati4 on 2008-10-09
My high-performance drives (Western Digital Raptors) run between 40C and 54C.  
I wouldn't be happy with 60C--that's toasty.

SMART parameters not standardized so each drive manufacturer makes up there own measurements.  Both smartctl and hddtemp are written by smart folks that can capture most of what is out there.  If you find some exceptions, work with the developers--get on the forums for those programs and capability may be added.

Because hard drive reliability is key to reputation, drive makers are not willing to release either reliability statistics or detailed descriptions of SMART parameters.

Google did an interesting study on hard drive reliability in 2005.  They eat a lot of hard drives every year so they know who makes decent drives.  You can yahoo their white paper.  It makes for interesting reading.

Temperature is not a strong correlator for reliability, but high temps can cause other problems (like warped motherboards) which do lead to reliability issues.

---

### Post by dabl on 2008-10-09
> **Soupcan said:**
> 

Also, does anybody have any idea as to why smartctl returns a value for temp, but hddtemp does not?



hddtemp is the package, and the daemon that runs.  It is not, AFAIK, a valid command to do anything other than start the daemon.

I use gkrellm to monitor the temperatures of my 5 hard drives.  It picks up the output of the hddtemp daemon and shows it in a window. After installing it, run gkrellm and right-click on top of the monitor, then on temperatures you choose the disk(s) to show.

I didn't know SMART included thermal output -- that's news to me, if it's true.  I use smartctl to periodically check the health (but not the temperature) of my hard drives.

HTH.  :)

---

### Post by cariboo on 2008-10-09
When setting up hddtemp make sure you set it up to run at start up. I had a look a the temps with smartctl, but they never made any sense. Right now my 4 drives 1 ide 1 sata and 2 esata are running at between 38 to 40C. Earlier this summer during +35C temps, I did see hd temps as high as 58C.

Jim

---

### Post by erigazio on 2009-02-07
try:
```
smartctl -a /dev/sda | grep 194
```

---

