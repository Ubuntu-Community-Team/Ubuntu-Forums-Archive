---
title: "Harddisk Spindown without laptop-tools"
date: 2009-07-02
forum: Hardware
---

### Post by phiamo on 2009-07-02
Hi i'm having a serious problem with my brand new Lenovo T500 7SG
I made a fresh Jaunty installation and disconnect power AC ... immediatly the hard drive "claks" 
and then it "claks" every 10 to 40 seconds ....
if i use smartctl:

sudo smartctl -a /dev/sda | grep 'Load_Cycle_Count'

the counter rises...
also if i make that request the hard drives spins up and about 10 to 20 sec later it spins down again.
the hard drive is a WDC WD3200BEVS-08VAT2


as mention in the topic i had no laptop-tools enabled tools in acpi.conf

now i said to myself why not enable laptop tools (shoud disable acpi for some settings) and try deactivating spin down,it does not work at all..

only thing working atm is 

hdparms -B 254 /dev/sda 

any value less than -B254 starts going to spindown in seconds

the -S parameter is ignored i think because it doesnt matter whatever i enter ....

has anyone an idea ?
the laptop is only 6 day old and i have:

1451 spin downs (Load_Cycle_Count)

system is fresh ubuntu installation, no matter weather 2.6.28 or 2.6.30 kernel ....

---

### Post by zepita on 2009-07-02
I do have a 1yr old lenovo with a hitachi HD and I got:

193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       24287

Is that bad?

I hope someone else replies to your concern.

---

### Post by phiamo on 2009-07-03
Hi, its only bad if it raises to fast afaik...
100 a day should be ok ... but less is better ... 

have a look here
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

pehabs its my problem too ...

but now after return from suspend problem isnt there .. only directly after reboot .... strange
any information would be pleasent

---

### Post by Sealbhach on 2009-07-14
Ever since I installed Jaunty this has not been a problem. However today, I noticed it was back, that horrible clicking every 10 seconds or so. I hate that sound, it's the sound of my hard drive dying.

So, I did

```
sudo gedit /etc/acpi/ac.d/90-hdparm.sh
```and changed the values for both battery and mains to 254. I don't carry my laptop around anywhere much, so I'm not really concerned about bumps and damage.

So the sound has stopped, but my question is have I done a bad thing?

.

---

