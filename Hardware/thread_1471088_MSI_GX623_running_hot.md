---
title: "MSI GX623 running hot"
date: 2010-05-03
forum: Hardware
---

### Post by cTn on 2010-05-03
Hi guys, i already had one thread about this a while back [http://ubuntuforums.org/showthread.php?t=1439820&highlight=gx623](http://ubuntuforums.org/showthread.php?t=1439820&highlight=gx623)

i was waiting for official release of Ubuntu 10.04 so i could speak little more "serious" about this problem

So some key info

1. I am dual-booting Windows 7 & Ubuntu 10.04 LTS (installed via wubi)
2. I am using "default" gpu drivers
3. This laptop includes ATI Mobility Radeon HD 4670 (m96) and Intel Core 2 Duo P7350 OC cpu ( i can post more info about specs, just ask)


My problem is that laptop runs "hot" its just my observation + laptop fun runs faster for the hole time when i am in ubuntu (in Windows 7 laptop is running cold and cooling fan is also running at much slower speed)
Also battery time is affected when i compare it to Windows 7 battery time.

CPU scaling works fine (checked in a cpu widget)

like i said in my previous thread

"my best guess is that there is some power-saving problem with gpu drivers (gpu is probably running in performance mode) and its not down-clocking properly to 2D mode, 

i am an advanced windows user but i have only "basic" knowledge of linux systems, so if anyone could share some light how to debug and fix this heating problem ill be really glad (i want to use ubuntu as main OS on my laptop, but this battery problem and "warm" case of my laptop is preventing me from using it)"

thanks for any ideas

---

### Post by cTn on 2010-05-05
bump

---

### Post by natarajmb on 2010-05-10
I am seeing the same issue with Thinkpad W500, I posted a question here - [https://answers.launchpad.net/ubuntu/+question/110312](https://answers.launchpad.net/ubuntu/+question/110312)

One thing i have observed is laptop starts heating when you are on AC with full charge. Can you confirm if its the same case with you?

---

### Post by cTn on 2010-05-10
> **natarajmb said:**
> I am seeing the same issue with Thinkpad W500, I posted a question here - [https://answers.launchpad.net/ubuntu/+question/110312](https://answers.launchpad.net/ubuntu/+question/110312)

One thing i have observed is laptop starts heating when you are on AC with full charge. Can you confirm if its the same case with you?

yes i think i can confirm this, also that proprietary drivers from ati gave me a big boost in battery life (1 hour and 10 mins on default "radeon" drivers that ubuntu ships with, about 2 hours and 20 minutes on ati "fglrx" drivers)
However laptop still remains hot like with radeon driver

---

### Post by natarajmb on 2010-05-10
> **cTn said:**
> yes i think i can confirm this, also that proprietary drivers from ati gave me a big boost in battery life (1 hour and 10 mins on default "radeon" drivers that ubuntu ships with, about 2 hours and 20 minutes on ati "fglrx" drivers)
However laptop still remains hot like with radeon driver

If i install ati drivers, entire system slows down, so i have gone back on opensource driver.

---

### Post by cTn on 2010-05-10
> **natarajmb said:**
> If i install ati drivers, entire system slows down, so i have gone back on opensource driver.

if you have problems with delay in maximize/minimize 
this can help you [http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/)

however the heating problem is still present and i don't think this is very good for hardware components inside =(

---

### Post by natarajmb on 2010-05-10
> **cTn said:**
> if you have problems with delay in maximize/minimize 
this can help you [http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/](http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/)

however the heating problem is still present and i don't think this is very good for hardware components inside =(

I forgot to mention before, after adding laptop-mode-tools package (faq - [http://samwel.tk/laptop_mode/faq](http://samwel.tk/laptop_mode/faq)), heat was relatively decreased, but not to an acceptable level. I read on ubuntu documentation yesterday that this package is no longer installed by default and its up to the user to install it, but I am not finding the link again once I find it will post it for your reference.

---

### Post by cTn on 2010-05-10
> **natarajmb said:**
> I forgot to mention before, after adding laptop-mode-tools package (faq - [http://samwel.tk/laptop_mode/faq](http://samwel.tk/laptop_mode/faq)), heat was relatively decreased, but not to an acceptable level. I read on ubuntu documentation yesterday that this package is no longer installed by default and its up to the user to install it, but I am not finding the link again once I find it will post it for your reference.

thank you for the info (i never heard of such packages) looks really interesting, currently i am considering, to reinstall my ubuntu (because i added many ppa repos, to get the latest radeon drivers) and also installed the latest dev kernel, however without any success in solving this heat problem :(

---

