---
title: "Tips for better power consumpsion?"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by neocookie on 2006-08-11
Hi guys

I'm new to Ubuntu (6.06) which I've installed on a brand new [Advent 7096](http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1617807157.1155289164@@@@&BV_EngineID=ccgfaddiiddfhiicflgceggdhhmdgmi.0&category_oid=&sku=007865&page=Product&fm=null&sm=null&tm=null).

A quick overview of the system:[LIST]
[*] AMD Sempron 3000+ Processor (1600 MT/s HyperTransport)
[*] 128 KB Cache
[*] 1024 MB RAM
[*] DVD ReWriter MultiDrive
[*] 15.4" Widescreen Display
[*] 128 MB ATI X200 Shared Graphics
[*] Integrated Wireless (b/g)[/LIST]
On install, I got quite poor batter-life out of it. I've now turned laptopmode on, and I'm using cpufreqd to manage CPU usage. I've installed the latest ATI drivers and WiFi drivers. Everything seems to be working as expected, and (surprisingly) was relatively pain-free, despite there being little on Google about this system.

However, battery life is still poor. Is there anything else I can do to help extend the battery life?

---

### Post by neocookie on 2006-08-11
Hmmm... after further investigation, it seems that I actually don't have cpufreq on there. cat /proc/cpufreq throws an error.

cat /proc/acpi/processor/CPU1/info returns:
processor id: 0
acpi id: 1
bus mastering control: yes
power management: no
throttling control: no
limit interface: no

Any suggestions on the best way to proceed?

---

### Post by oss_monkey on 2006-08-11
I am an Ubuntu newbie as much as the next guy, but I do recall being recommended to install gnome-power-manager. It's in the repos.

My own laptop uses it, but since I'm almost always connected to a wall socket, I really have no idea how much battery this thing consumes (and the fact that it's already 5 years old!).

---

### Post by neocookie on 2006-08-11
Cheers oss_monkey. I'll look into that.

Any other tips from ubuntu power-users? I'm quite keen on squeezing as much as I can out of this laptop. :)

---

### Post by David Corrales on 2006-08-11
There's an utility called **aticonfig** which you can use to see the current power scheme and change it at will :)
I'm very interested in seeing other ways to get similar battery life in linux compared to windows. I usually lose around 33% :(

---

### Post by spd106 on 2006-08-11
These may be more obvious but switching off the wifi card will save power and cpu cycles. As would using fewer programs simultaneously. 

If you have two 512 MB memory modules, removing one of them would save you power. Going into suspend on longer periods of inactivity might also save you some. Darken the display as far as you can. Reduce the screensaver/power off kickin times.  

Check the manufacturer for any bios or firmware updates.

Monitor the bootup process (or use top and ps) for unnessary services. Turn off postfix, bluetooth support etc. Maybe try init-ng to save time at startup.

---

