---
title: "How Do I Increase Fan Interval?"
date: 2010-07-11
forum: Hardware
---

### Post by volobiz on 2010-07-11
My son's laptop is an Acer Extensa 4420-5237. It tends to run a little hot unfortunately, even with Ubuntu 10.04 LTS. Do you know how I can increase the fan interval (even with a cron job) so that the laptop can run a little cooler?

I'm worried it might become a fire hazard without this.

---

### Post by ov3rcl0ck on 2010-07-11
There may be a BIOS option, but theres a way to do it from within the OS, but it doesn't work for all hardware.

Theres to much to summarize so heres a link: [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

---

### Post by volobiz on 2010-07-11
> **ov3rcl0ck said:**
> There may be a BIOS option, but theres a way to do it from within the OS, but it doesn't work for all hardware.

Theres to much to summarize so heres a link: [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

Darn. Can't update the BIOS because I only have Linux installed. I would have to boot some kind of strange, custom-made Windows XP boot CD or something and then do a BIOS update.

Then, your link you suggested mentioned installing powersaved, but there is no powersaved for Ubuntu 10.04 LTS. The instructions are from the year 2008.

I then ran sensors and found this output:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +65.0°C  (crit = +95.0°C)                  
temp2:       +65.0°C  (crit = +110.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +62.0°C                                    
Core0 Temp:  +57.0°C                                    
Core1 Temp:  +62.0°C                                    
Core1 Temp:  +57.0°C 
```

From what I read on the web, 70 degrees Celsius is when the CPU runs "hot". Indeed, my son's keyboard gets sort of hot and the temp does get up to 70 degrees Celsius sometimes.

I installed the Sensors Applet package and enabled it on my gnome-panel. I set it to show me stuff in Fahrenheit and it sometimes says 170 degrees Fahrenheit. I set it to warn me around 180 degrees Fahrenheit and might experience this occasionally I imagine. (I'm brand new with Ubuntu 10.04 LTS, I mean. Previously I had this thing on Ubuntu 8.04 LTS. We'll have to see how this goes.)

I placed a fan near my laptop and held it over it to see how cold I could get it. It had a remarkable difference, dropping down to 127 degrees Fahrenheit and the keyboard being cool to the touch.

I noticed that fancontrol is in /etc/init.d, but I can't get it to run and it does not report a status except "not running". A "sudo ps -ef | grep -i fan" returns nothing. I am under the assumption that the BIOS is controlling the fan on/off as necessary, instead of the OS, but the BIOS is doing a lousy job of it. I mean, a laptop keyboard should be cool to the touch, don't you think?

---

### Post by mrdusty on 2010-07-11
[SIZE=3]Have you gone to the Asus page and checked with them for any updates?
Also, I used the temp monitor I installed on one of my panels.
Mine is now running a lo t cooler.[/SIZE]

---

### Post by volobiz on 2010-07-11
> **mrdusty said:**
> [SIZE=3]Have you gone to the Asus page and checked with them for any updates?
Also, I used the temp monitor I installed on one of my panels.
Mine is now running a lot cooler.[/SIZE]

Acer, not Asus. (Not being rude, just correcting the record.) Um, updating the BIOS appears only possible if I install Windows, which I don't have in this case.

I too also installed: "apt-get install sensors-applet" and enabled it. It only tells you about stuff, doesn't change the temp as far as I am aware.

Any other suggestions? I just found this athcool tool I can install, and indeed my son's laptop is an AMD processor.

---

### Post by volobiz on 2010-07-11
Just tried the athcool status command and it reports on that laptop that it doesn't have a supported chipset. So, can't even be helped by athcool.

---

