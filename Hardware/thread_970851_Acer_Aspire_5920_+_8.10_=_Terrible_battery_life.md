---
title: "Acer Aspire 5920 + 8.10 = Terrible battery life"
date: 2008-11-04
forum: Hardware
---

### Post by bhashadi on 2008-11-04
Hi
I have just installed Ubuntu 8.10 (fresh installation). I have been using Ubuntu on my Acer Aspire 5920 laptop since I purchased it in March 2008. I have so far used Ubuntu 7.10 followed by 8.04 and now 8.10 on "as and when released" basis (everytime fresh installation). No doubt Ubuntu is great!

 However, I have noticed a drastic drop in battery lifetime with successive releases on my laptop which does not seem to correlate with the battery life. With the new laptop with 7.10 release (in Mar '08 ), battery runtime used to be 3hrs 15min...... on 8.04 release (which was just one month after I purchased my laptop), immediately after installing 8.04, the runtime dropped to 2hrs 10min but as if it was not enough.. with 8.10...the battery runtime is just 1hr 20min. So within 8 months I have lost 115min of battery stamina. 

I am not sure whether it is because of battery getting aged or what. For almost entire duration when my laptop is on (which is usually 12-14 hrs per day on weekdays and 6-8 hrs per day on weekends) I use AC power supply rarely depending on battery power. It is only sudden power cuts (which don't last for more that 2 min) when battery comes into play. So I think battery ageing is not a problem here.

I haven't tried windows Xp on this machine neither Vista for that matter since I don't have a copy of these.

I was just wondering if somebody else too has noted similar drop in battery runtime with successive versions of Ubuntu.

As far as hardware configuration of my laptop is concerned, I have Intel Core2 Duo processor T5450 (1.66GHz, 667MHz FSB, 2MB L2C) 15.4" WXGA LCD, 2GB DDR2 RAM, 160 GB HDD, Mobile Intel Graphic Media Accelerator X3100, 802.11 a/b/g WLAN etc.

---

### Post by joebodo on 2008-11-04
From my experience, this is probably due to battery age.

Powertop may be helpful in finding out what is draining the battery.

---

### Post by joshis on 2008-11-21
> **joebodo said:**
> From my experience, this is probably due to battery age.

Powertop may be helpful in finding out what is draining the battery.

Well, I would say this is probably not the case - something seems to be pretty much messed up with Ubuntu 8.10 - is the acpi working as it should? Can someone else confirm the behavior (poor battery life with 8.10, maybe on Acer laptops...)?

I have Acer Aspire 1350 (yes, it is older model), the battery life was somewhere around 50 minutes on 8.04, but after I updated to 8.10, it is about 20 minutes!!! It was pretty remarkable drop down. This totally does not correlate to battery life, IMO.

I found it strange - this is why I was searching if someone experiences the same behavior... and here it is... I am not alone...

---

### Post by Dao984 on 2008-11-25
hello
I have your same problem 
with Ubuntu 8.10 and aspire 5920 my battery time is 1:30 min. With Hardy more than 2 hours...
Whit Vista 2 hours in energy saving mode

What can we do? Help :confused:

---

### Post by binbash on 2008-11-25
[http://www.lesswatts.org/](http://www.lesswatts.org/)

---

### Post by 1902 on 2008-11-26
Mine is Aspire 4930G with dual boot vista and ubuntu 8.10, with vista i got 3 hours 39 minutes in full charge, in ubuntu i got only 2 hours :-k

---

### Post by tonymaro on 2009-01-04
I've never tried to run mine down, but install powernowd using Synaptic or apt-get and add the CPU Frequency Scaling Monitor to your panel.  It will make a huge difference.  By default mine is set to provide CPU performance on demand, but when I'm running on battery I can manually set it to a lower setting to maximize operating time.

There's probably a few other power management tweaks I did.  Also check out **[http://www.lesswatts.org/tips/cpu.php](http://www.lesswatts.org/tips/cpu.php)** for more.  I not only have a much cooler laptop now, but use less battery power.

For more of my Acer 5920 exploits with 8.04 and 8.10 check out: [http://ossramblings.com/taxonomy/term/136](http://ossramblings.com/taxonomy/term/136)

---

