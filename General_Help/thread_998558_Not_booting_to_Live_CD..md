---
title: "Not booting to Live CD."
date: 2008-11-30
forum: General Help
---

### Post by gasto on 2008-11-30
While trying to make the Live CD work before installation of Ubuntu 8.10 , I get a black screen (no video signal), of course I am using accelerated graphics (Nvidia Geforce 6200), so tried the motherboard's video but no go. I may try to disconnect the AGP video card but I wanted to hear from you great fellows, beforehand.

---

### Post by gasto on 2008-11-30
By the way, I already tried searching for similar problems on these forums, with no luck.

---

### Post by chewearn on 2008-11-30
A suggestion: did you try disabling the motherboard video in the BIOS?

---

### Post by falcon61102 on 2008-11-30
Also, have you tried to boot up the LiveCD in Safe Mode.  If you look at the menu options when you first start, you should see a series of F commands at the bottom of the screen.  Safe mode should be in there.  

If you can get the LiveCD to load using safe mode, you should be able to install through safe mode and fix the hardware/driver issue once Ubuntu is installed.

---

### Post by gasto on 2008-12-01
> **falcon61102 said:**
> Also, have you tried to boot up the LiveCD in Safe Mode.  If you look at the menu options when you first start, you should see a series of F commands at the bottom of the screen.  Safe mode should be in there.  

If you can get the LiveCD to load using safe mode, you should be able to install through safe mode and fix the hardware/driver issue once Ubuntu is installed.

¿Will it boot with motherboard video in safe mode?

---

### Post by gasto on 2008-12-01
OK, it tried Live CD with "Safe graphics mode", my monitor is connected to the videocard vga input, and it worked!... aparently.

---

### Post by gasto on 2008-12-01
Should internet work from the beginning? because it is not.

---

### Post by gasto on 2008-12-01
Screen resolution is stretched horizontally. Searching for 'desktop resolution somewhere'

---

### Post by gasto on 2008-12-01
Screen resolution was easy to solve:

System->Screen Resolution

Changed it to 1024x768

---

### Post by falcon61102 on 2008-12-01
What works right away will depend on your hardware configuration.  To fix the network problems look to see if you need any Restricted Drivers by going to System>Administration>Hardware Drivers and see if your network card is listed there.  If so, enable it and you'll probably be prompted to restart.  Remember on restart to use Safe Mode unless you were able to fix the graphics problem already.  Otherwise boot back up in Safe Mode and you should have a network connection to be able to fix anything else not working.

---

### Post by gasto on 2008-12-01
That is what I thought but, the network driver SiS900, seems to be installed:

sudo lshw -c netword

gave me a driver:

...
driver=sis900
...

---

### Post by gasto on 2008-12-01
I am quite frustrated, I thought I'd figure things out in one day, but one _entire_ day of frustration and vane troubleshooting has exhausted every bit of patience I could ever have.

God bless the developers of Ubuntu and its great community. To bad they announce something is not, like "Ubuntu will give you an alternate option", I can't have an option when internet is not ready available.

Great software. Too bad it doesn't work. Maybe if I get a PhD in computer networking will I be able to get some net-work out of Ubuntu.

---

### Post by gasto on 2008-12-01
I managed to ping localhost with no issues.

---

### Post by gasto on 2008-12-01
description: ethernet interface
product: SiS900 PCI Fast Ehternet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: xxxxxxx
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes

---

### Post by chewearn on 2008-12-02
hi gasto
If you have a problem which need assistance, you are welcome to post a question.  May I suggest, one specific question per thread.  That would get maximum exposure to the volunteers of this forum, and help would come in faster.

A possibly better option is to go to #ubuntu channel at freenode irc.  That would get instant support from thousands of volunteers there.

I am now unsubscribing from this thread, since you appeared to have turned it into a personal microblog, with rants and all.

---

### Post by gasto on 2008-12-02
I was banned for my schizofrenia at the Ubuntu forums. I now realize that it is most likely the NIC is not working at all in my PC. It didnt work on Windows XP SP2, I deduced a malware had caused it. But now that I've tried everything humanly possible to make internet work, I deduce that the NIC is bad, evil and sadist.

---

