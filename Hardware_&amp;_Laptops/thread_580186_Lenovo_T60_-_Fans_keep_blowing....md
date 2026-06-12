---
title: "Lenovo T60 - Fans keep blowing..."
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by BombeNissen on 2007-10-18
Just installed Gutsy on my laptop and it all went very well, but theres one thing that worries me. Now, its been running for 2 hours without any problems, but the fans dosent stop blowing, its like something is very very wrong, and I cant figure out what it is. 

Any idears ?

---

### Post by the.ant on 2007-10-18
It would be kinda helpful to know anything about your laptop. 

Without that, my only idea would be that you have CPU and GPU running at full power, and the laptop thus overheats. 

On my T60, I usually have the CPU running at 50% and the ati powerstate 1 or 2. The fan is rather quiet or off.. 

Also, did you check Thinkwiki.org?

---

### Post by BombeNissen on 2007-10-19
The specs on it: 
T5600(1.83GHz), 1GB RAM, 80GB 5400rpm HD, 14.1in 1400x1050 LCD, 128MB ATI Radeon X1400, CDRW/DVDRW, Intel 802.11abg wireless, Bluetooth/Modem, 1Gb Ethernet, UltraNav, Secure chip, Fingerprint reader

---

### Post by raktarna on 2007-10-20
that problem may be due to the new cool trackerd deamon. After a couple of hours of indexing of all your files it appears to end the initial scan and the cpu cools down.

My only problem has been that I couldn't get  the internal wireless to work. It was working with feisty but during the upgrade I lost this. Any help would be appreciated.

---

### Post by Zetheroo on 2007-10-20
I also had the same problem with my RAM and CPU being gobbled up all the time, not just for 2 hours but for days after upgrading to Gutsy.

So I went to System > Preferences > Indexing Preferences and switched the indexing and watching services off. Then I killed the "trackerd" process in the System Monitor. I also stopped "Traker" from starting up with the session.

Viola ... all systems cool and calm and ready to work for me 100%.

My System: 
IBM Thinkpad T60 
Duo Core 2.0 GHZ
2 GB RAM
100 GB HDD
ATI Mobility Radeon X1400
WiFi - BT - WAN
DVD - DL - Multi-Drive

---

### Post by Whiffle on 2007-10-21
On my T43 it will blow the fan constantly if I don't run this:

[http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Comprehensive_bash_script_with_fine_control_over_fan_speed](http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Comprehensive_bash_script_with_fine_control_over_fan_speed)

---

### Post by Zetheroo on 2007-10-21
> **Whiffle said:**
> On my T43 it will blow the fan constantly if I don't run this:

[http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Comprehensive_bash_script_with_fine_control_over_fan_speed](http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Comprehensive_bash_script_with_fine_control_over_fan_speed)


Even with trakerd not working your fan will still be spinning?

---

### Post by Whiffle on 2007-10-21
For me trakerd doesn't seem to do anything, maybe i turned it off and forgot about it, but unless I'm doing actual computing work my t43 is nearly silent w/ tp-fancontrol enabled.  All tp-fancontrol does is take over control of the fans from the bios and uses a different calculation to determine how fast to run the fan.  Its worked great for me so far.

---

### Post by Zetheroo on 2007-10-21
> **Whiffle said:**
> For me trakerd doesn't seem to do anything, maybe i turned it off and forgot about it, but unless I'm doing actual computing work my t43 is nearly silent w/ tp-fancontrol enabled.  All tp-fancontrol does is take over control of the fans from the bios and uses a different calculation to determine how fast to run the fan.  Its worked great for me so far.

Sounds wonderful... I am just concerned that the fan is able to do its thing when it needs to without some sort of customized prohibition. 

Like I said, when I disabled trackerd from activating itself on Login, my fan has completely settled down because the CPU was no longer being run at 50% nonstop. 

If someone chooses to incorporate some sort of Fan-Speed manager they should first really make certain that there is no process which is using up CPU power and thereby causing the fan to spin in order to maintain a safe temperature. Otherwise one could end up with a melted CPU or worse.

Just a word of caution.... :KS

---

