---
title: "HOWTO: Acer Aspire 502x wireless config"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by equilibrium on 2006-03-05
**acer aspire 502x series wireless config:**

first you will need to download the linux headers
```
uname -r
2.6.12-9-amd64-generic
sudo apt-get install linux-headers-2.6.9-10-amd64-generic

```

***AMD64* download and install GCC-3.4**
gcc-3.4-base_3.4.4-6ubuntu8_amd64.deb
cpp-3.4_3.4.4-6ubuntu8_amd64.deb
gcc-3.4_3.4.4-6ubuntu8_amd64.deb

next you need to download the ndiswrapper source and compile it
```
wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz
tar xvzf ndiswrapper-1.7.tar.gz
cd ndiswrapper-1.7
make
sudo make install

```
next download the acer broadcom win64 drivers
```
wget ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip
unzip 80211g.zip

```
next you will need acer_acpi
```
wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install

```

ok now all the needed packages should be compiled and installed ok, next thing to do is initialise them.

install win64 drivers using ndiswrapper
```
cd 80211g
su
ndiswrapper -i bcmwl5.inf
```
check driver is installed:
```
ndiswrapper -l
```
if it is installed you should get:
```
Installed drivers:
bcmwl5      driver present, hardware present
```
next initialise the module
```
modprobe ndiswrapper
```
check it loaded
```
dmesg | grep ndis
```

next initialise acer_acpi
```
su
modprobe acer_acpi
cd /proc/acpi/acer
chmod 777 .wireless
echo "enabled: 1" >/proc/acpi/acer/wireless
```
check it worked
```
dmesg | grep acer_acpi
```
now it has initialised you should be able to scan for wireless networks.
```
iwlist wlan0 scan
```
you should get some info back.


**Create Init Script**
It is working for now but you don't want to initialise the modules on every boot. So you need to create a init script.
```
su
cd /etc/init.d
gedit wirelessAcerAcpi
```
add this text to the file, save and exit
```
#!/bin/sh

case "$1" in

        start|"")

                modprobe ndiswrapper

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo "enabled: 1" >/proc/acpi/acer/wireless

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                ;;

esac
```
make the file executable
```
chmod 755 /etc/init.d/wirelessAcerAcpi
```
add the script to startup
```
cd /etc/rc2.d
ln -s ../init.d/wirelessAcerAcpi S99wirelessAcerAcpi
```
now it should initialise ok.

One problem I had was as soon as I rebooted, the drivers initialised ok but didn't connect to any wireless networks. I tried a few things with init scripts to no avail, instead I ended up writing a init script to start with gnome.

**Gnome Init Script**
here's my little gnome script, it basically stops eth0 (I did this as gnome seemed to default to it, ignoring wlan0) and restarts the wlan, scanning and connecting to the nearest wireless AP.

```
cd ~
gedit wlan.sh
```
add the following text, save and exit.
```
# written by: equilibrium - news.equk.co.uk
# wireless init script for acer aspire 502x series
# disable eth0 and restart wireles link
sudo ifdown eth0
sudo ifdown wlan0
sudo ifup wlan0
```
make the file executable
```
chmod +x wlan.sh
```
next go to System -> Preferences -> Sessions ->(tab)Startup Programs -> (button)Add
```
/home/user/wlan.sh
```
Now it should start once you login. If you don't have sudo setup it will ask for a passwd tho

Set it so it doesn't ask for a password:
```
su
visudo
```
add to the bottom
```
user ALL=NOPASSWD: /sbin/ifup
user ALL=NOPASSWD: /sbin/ifdown
```
make sure you save and exit (CTRL+X)

That should be it.

---

### Post by equilibrium on 2006-03-05
I thought I'd post this as loads of people seem to be posting about problems with the broadcom driver etc, there are a few sources of info but I noticed some had errors and also didn't provide a full guide, resulting in the wireless driver initialising but not connecting to anything.

I hope I put it in the right section anyway, I just did all this on AMD64 on my 5024wlmi.
Hope it helps some people.

Cheers

:D

---

### Post by equilibrium on 2006-03-05
one tweak I've found to speed up the wlan dhcp:

```
nano -w /etc/dhcp3/dhclient.conf
```
find #timeout 60;
add below:
```
timeout 20;
```
it also speeds up boot a little aswell, where before it was stuck on "Configuring Network Interfaces" :-k

---

### Post by kaks on 2006-03-21
I know this is kind of funny as i modified your HOWTO for the 32bit version.

But thing is i cant get it to work on Dapper.

Followed the instructions, and nothing.

Any ideas? Should i do anything else?

Thanks in advance

---

### Post by ovimunt on 2006-06-25
Sorted it.

---

### Post by ovimunt on 2006-06-25
Got it.

---

### Post by ovimunt on 2006-06-29
Hi,

I've finally managed to sort out my wireless but there's still a little glitch.

Every time I restart Ubuntu the wireless won't connect automatically. I have to go to the properties and deactivate and then activate to get it to connect.

I did try the script provided in here, the one with *ifdown*, *ifup* but it doesn't seem to work. I did each and every step suggested but it won't work. It looks like the script it's not being run at startup...

Any ideas? Thanks

---

### Post by bmhm on 2007-03-24
[FONT="Verdana"]Hi,

My Chipset: bcm43xx
Brand: Acer
Model: Aspire 5024WLMi

I'm using Ubuntu amd64. I downloaded the drivers from: [ftp://ftp.support.acer-euro.com/notebook/aspire_5020/driver/xp64](ftp://ftp.support.acer-euro.com/notebook/aspire_5020/driver/xp64) 
Seems to have moved.

Anyway. Ndiswrapper -i bcmwl5.inf works.

ndiswrapper -l gives:
```
bcmwl5          driver installed, hardware present 
```

Now my dmesg | grep ndiswrapper gives me this:
```
[  837.007386] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[  837.015856] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[  837.016991] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[  837.021177] ndiswrapper (NdisWriteErrorLogEntry:241): log: 1C0779B0, count: 1, return_address: ffffffff884f913e
[  837.021181] ndiswrapper (NdisWriteErrorLogEntry:244): code: 267
[  837.021243] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[  837.021249] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[  837.021261] ndiswrapper (miniport_halt:327): device ffff81003bd6a500 is not initialized - not halting
[  837.021267] ndiswrapper: device eth%d removed
[  837.021291] ndiswrapper: probe of 0000:06:05.0 failed with error -22
[ 1113.272361] ndiswrapper (free_all_objects:354): object ffff81003b9dc428 type 2 was not freed, freeing it now
```

Its about this part:
couldn't initialize device: C0000001
(pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)

Any Ideas? Any other usable drivers?

The bcm43xx script taken from the other thread won't work at all - His drivers are reported by ndiswrapper not to work.[/FONT]

---

