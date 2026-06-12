---
title: "Acer Timeline X 3820TG Hard Drive noise"
date: 2010-10-22
forum: Hardware
---

### Post by zemex34 on 2010-10-22
I recently installed Ubuntu 10.10 x86 in my Acer 3820TG. The laptop comes with the hard drive disk WDC WD3200BEVT-22A23T0. My problem is that it makes lots of noise when accessing data, like clicking really hard. The thing is that nothing of this happen in Windows 7.

Help would be appreciated ;)

---

### Post by jerrrys on 2010-10-23
thats got to be bad.  if it was mine (a fresh install) i would wipe the install and go with 10o4.  also got a few hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=hdd+noise+10.10&as_qdr=all&sa=Google+Search&lang=en#1207](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=hdd+noise+10.10&as_qdr=all&sa=Google+Search&lang=en#1207)

---

### Post by dallasg on 2011-02-15
Hi everyone.  Not sure if anyone has resolved this issue before but it's been really causing a lot of stress in my life so I figured I'd post a solution.

This clicking is due to the APM feature in the kernel's ACPI settings causing the drive heads to constantly park and re-park, which is hell on the disk's health.  While there is no way to adjust the settings through the system, at least that I'm aware of, there is a solution.

What I did to disable the APM feature:

1. Create a bash script called "spindownsata.sh" w/o the quotes

2. spindownsata.sh should consist of the following:
```
#!/bin/sh
hdparm -B 255 /dev/sda
```

3. place the newly created script into the /etc/init.d directory
```
sudo cp spindownsata.sh /etc/init.d
```

4. Then you'll need to add the scrip to the system startup:
```
sudo update-rc.d spindownsata.sh defaults
```

5. Finally, you'll need to make the script executable:
```
sudo chmod +x /etc/init.d/spindownsata.sh
```

Reboot and enjoy a perfectly quiet hard drive.

---

