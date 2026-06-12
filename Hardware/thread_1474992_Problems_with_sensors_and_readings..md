---
title: "Problems with sensors and readings."
date: 2010-05-06
forum: Hardware
---

### Post by teek5449 on 2010-05-06
I am still a little new to linux but have been plugging along. I recently installed Ubuntu 10.04 onto one of my HTPC machines and have been trying to get the onboard sensors to read properly. I have run a ```
sensors-detect
``` which picked up ```
Probing for `Winbond W83L771AWG/ASG'...                     Success!
    (confidence 6, driver `lm90')
``` I then chose to have the information saved to my "/etc/modules" (which I double checked and it is added) ```
# Chip drivers
coretemp
lm90

``` I reboot.... run a ```
sensors
``` and receive ```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +20.0°C  (crit = +90.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +19.0°C  (crit = +90.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +20.0°C  (crit = +90.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +19.0°C  (crit = +90.0°C) 
``` which is just waaaay too low.... ambient temperature is higher than that. I checked the readings in the BIOS and they read a far more reasonable mid to upper 30s C. (close to start up) 

I have read and searched endlessly for a fix for this and it was supposed to be fixed in this latest release so I had put off installing Ubuntu until 10.04 was released for this reason alone. This machine will be on 24/7 so I really need some control here. (my BIOS does not provide a way for this) I really would like fan speeds too which also show in my BIOS.

Any thoughts or ideas?

info:
fresh install of Ubuntu x86 10.04 ```
~$ uname -r
2.6.32-22-generic
~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l
```
system: Zotac IONITX-A-U Atom N330

Thanks for any help with this!

---

### Post by aamonster on 2010-05-07
The same trouble:
```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       -2.0°C  (crit = +90.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +8.0°C  (crit = +90.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       -2.0°C  (crit = +90.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +8.0°C  (crit = +90.0°C)

```

Intel Atom 330, mainboard Intel D945GCLF2D i945GC.

drivers, detected by sensors-detect:
```

Driver `smsc47m1':
  * ISA bus, address 0x680
    Chip `SMSC LPC47M15x/192/997 Super IO Fan Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

```

```

$ uname -r
2.6.32-22-generic

$ sensors -v
sensors version 3.1.2 with libsensors version 3.1.2

```

---

### Post by dino99 on 2010-05-07
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure lm-sensors

---

### Post by aamonster on 2010-05-07
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure lm-sensors
No effect.
Maybe I must edit sensors3.conf file? (there is no coretemp-isa-* section in that file)

---

### Post by teek5449 on 2010-05-07
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure lm-sensors
Same here, no joy after following instructions and a reboot. Still only detecting:```
Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

Driver `lm90':
  * Bus `SMBus nForce2 adapter at 4d00'
    Busdriver `i2c_nforce2', I2C address 0x4c
    Chip `Winbond W83L771AWG/ASG' (confidence: 6)

``` ...same as before.

Any other thoughts or suggestions? This seems like it might be related to the Atom 330 chipset? Anyone else with that chipset showing correct information? like I said before I had waited to the release of Lucid Lynx because I had read that it had an updated lm-sensors that fixed this issue. I guess it is only partially fixed. Also, am I wrong thinking that ~20C is just waaaaay too low for a temperature reading? Again I compared with BIOS readings and I get a CPU reading ~15C higher.

---

### Post by dino99 on 2010-05-07
> **teek5449 said:**
> Same here, no joy after following instructions and a reboot. Still only detecting:```
Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

Driver `lm90':
  * Bus `SMBus nForce2 adapter at 4d00'
    Busdriver `i2c_nforce2', I2C address 0x4c
    Chip `Winbond W83L771AWG/ASG' (confidence: 6)

``` ...same as before.

Any other thoughts or suggestions? This seems like it might be related to the Atom 330 chipset? Anyone else with that chipset showing correct information? like I said before I had waited to the release of Lucid Lynx because I had read that it had an updated lm-sensors that fixed this issue. I guess it is only partially fixed. Also, am I wrong thinking that ~20C is just waaaaay too low for a temperature reading? Again I compared with BIOS readings and I get a CPU reading ~15C higher.

into /etc/modules add W83L771 (maybe with AWG or ASG)

---

### Post by dino99 on 2010-05-07
googling around, its seem that chipset has been added to the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

install: first "linux source all.deb" then "header all.deb", then header, then image (choose i386 or amd64)

sudo update-initramfs -u
sudo grub-mkconfig && update-grub

---

### Post by teek5449 on 2010-05-07
> **dino99 said:**
> googling around, its seem that chipset has been added to the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

install: first "linux source all.deb" then "header all.deb", then header, then image (choose i386 or amd64)

sudo update-initramfs -u
sudo grub-mkconfig && update-grub

Just want to double check what you are asking me to do. (like I said I'm somewhat new to Linux). I should download and install the .deb packages from the link that you provided in this order:

(running 32bit so i386?)
```
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-source-2.6.34_2.6.34-999.201005061008_all.deb
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-headers-2.6.34-999_2.6.34-999.201005061008_all.deb
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-headers-2.6.34-999-generic_2.6.34-999.201005061008_i386.deb
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-image-2.6.34-999-generic_2.6.34-999.201005061008_i386.deb
```
then run ```
sudo update-initramfs -u
sudo grub-mkconfig
sude update-grub
``` or is that supposed to be ```
sudo grub-mkconfig && update-grub
```....after I have downloaded and installed the updated kernel? Fingers crossed that this will fix the issue since this is a deal breaker for me if I can not get the sensors working correctly.

Thanks again for all your help.

---

### Post by teek5449 on 2010-05-07
Well I went ahead and updated the kernel and there is a little progress: ```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +21.0°C  (crit = +90.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +21.0°C  (crit = +90.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +21.0°C  (crit = +90.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +21.0°C  (crit = +90.0°C)                  

w83l771-i2c-0-4c
Adapter: SMBus nForce2 adapter at 4d00
temp1:       +31.0°C  (low  = -40.0°C, high = +70.0°C)  
                      (crit = +85.0°C, hyst = +75.0°C)  
temp2:       +39.0°C  (low  = -40.0°C, high = +70.0°C)  
                      (crit = +110.0°C, hyst = +100.0°C)
```
So an improvement... temps look to be much closer to actual temps although still a  bit low in my opinion but who knows it is an Atom processor and meant to run passive even though I am actively cooling the system right now. 

Now any idea on how to get the fans reading? (yea, they are four wire fans that show a reading in the BIOS)

Progress is progress and I won't complain about that :)

UPDATE: I'm now receiving a "UDEVD-WORK[303]failed..... /dev/null" upon boot. Not affecting system that I can tell but it is showing when booting up. Any ideas? Only appeared after updating the kernel.

---

### Post by teek5449 on 2010-05-08
I'm having no luck finding any more information on this. It looks as though lm-sensors just does not support this at the moment.... hoping for future support but until then it looks like I have to go with Windows which does have software that supports this chip fully. Hate to do it so if anyone has any additional information please let me know. 

Thanks again for the help that was provided.

---

### Post by Ron O on 2010-05-29
Sensor issue may be bigger than your specific system. My system had sensors on 3 prior installations before Lucid.
[http://ubuntuforums.org/showthread.php?p=9364281#post9364281](http://ubuntuforums.org/showthread.php?p=9364281#post9364281)

---

### Post by teek5449 on 2010-05-29
> **Ron O said:**
> Sensor issue may be bigger than your specific system. My system had sensors on 3 prior installations before Lucid.
[http://ubuntuforums.org/showthread.php?p=9364281#post9364281](http://ubuntuforums.org/showthread.php?p=9364281#post9364281)Thanks for the update. I hate to say but I had to go with Windows where all of my issues that I have been having with the Linux are nonexistent. I will reconsider a Linux distro is this issue is addressed in the future. Linux better suits my needs for every other aspect of the unit. 

I'm not saying that Windows is better then Linux, but in my case where the unit is being left on 24/7, fan monitoring is essential and not an option.

---

