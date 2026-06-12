---
title: "Broadcom wireless STA driver on Meerkat"
date: 2010-10-28
forum: Hardware
---

### Post by pankaj5k on 2010-10-28
Hello, 

     I have Meerkat installed side-by-side with Lucid on a Dell 
Latitude laptop. I have noticed that in Meerkat, the wireless speed is lower whenever the laptop is on battery power.
This does not happen in Lucid so I was wondering if this is due
to some power saving option for wireless interface in Meerkat. 
I am using the Broadcom STA drivers in both installations. 

     I would be grateful to anyone who could point me to 
where I could change the settings so that I get maximum wireless
speed regardless of the power state. 

Best regards, 
   Pankaj

---

### Post by pankaj5k on 2010-10-29
OK - I have investigated a bit more (using wavemon) and 
found that in Meerkat, the wireless interface is put into 
power management mode when on battery power. I can override
this by issuing the following command :-

    sudo iwconfig eth1 power off

   However, this setting is not retained if power is attached or 
when resuming from suspend. The reason I want to be able to 
change or disable the wireless power management when on battery
power is that not only is the speed affected, the response time 
is slower too. It makes ssh sessions unresponsive for short 
periods of time.

Best regards, 
  Pankaj

---

