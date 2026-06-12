---
title: "ubuntu 9.10 with Intel GMA 3100 = Low resolution?"
date: 2009-11-25
forum: Hardware
---

### Post by bl4ckl34d3r on 2009-11-25
Hello Ubuntu Forums

I've got a problem after installing ubuntu 9.10 on my desktop PC.
Everything works but my screen resolution is limited to 800x600 or 640x680.
Which is imo way too large. i've got an onboard videocard Intel GMA 3100
So... Anyone?

---

### Post by bgrohe on 2010-02-15
Have you tried to go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS

and select the most recent intel driver. I am building a pc and want to see if this chipset works.

---

### Post by URPradhan on 2010-03-24
No, I also did not find the driver for Ubuntu latest version :( The max I can select is 1152x864 but I can select 1280x1024 on my Windows XP. How can I have my XP resolution on Ubuntu ?

---

### Post by wildmacaw on 2010-04-05
Yup I am having the same issue (everything works, except I am stuck to 800x600 screen resolution and while booting up I get the error message "Running in low graphic resolution mode" or some thing similar ). 

To solve this current issue, which of the following shall I do:

1. Shall I format my desktop and install Ubuntu 9.04?
2. Buy a NVIDIA graphics card?
3. Buy a new motherboard?
4. Chuck everything and reinstall XP?
5. Something else! (no idea what I have to - considering I am complete linux newbie!)

Would it do any good if I were to post the Xorg.0.log file?

Please help me - I really don't want to have to choose choice 4! :(

P.S. I see a blank screen under SYSTEM > ADMINISTRATION > HARDWARE DRIVERS and my xorg.conf file is also empty (or does not exists?).

---

### Post by bgrohe on 2010-04-05
I do not believe that it exists anymore. I am not sure how but can you find out what driver you are using?

---

### Post by wildmacaw on 2010-04-09
Here are my driver details:

```
sjcsc@sjcsc-Nucura100Tems:~$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
sjcsc@sjcsc-Nucura100Tems:~$ sudo lshw -C video
[sudo] password for sjcsc: 
  *-display               
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:f140(size=8)

```

---

