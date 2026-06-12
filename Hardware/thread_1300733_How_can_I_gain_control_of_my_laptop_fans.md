---
title: "How can I gain control of my laptop fans?"
date: 2009-10-25
forum: Hardware
---

### Post by VXxed on 2009-10-25
Note: I'm now 90% sure that it's an acpi/dsdt issue, but please read all my posts to see if I missed something.


Hi guys, I'm running on an old Fujitsu T4020D,and installed a full Ubuntu 9.04 (updated it to 9.10 already, in attempt to fix the fan-heat issue) and the fans just aren't spinning until it gets really hot, and then only for a second or two at seemingly even intervals.  I can't check the fans in windows xp, because I have no way to install it.  No DVD/CD drive, and no floppy disks to install it via win98 off of itself. xSensors tells me that the "temp" and "remote_temp" are both 0C

ALSO! Should I have files in /proc/acpi/fan and /proc/acpi/thermal_zone ? Because I know I'm supposed to be able to retrieve the temperature via "cat /proc/acpi/thermal_zone/... temperature" but I don't even have anything in the thermal_zone directory, nor do I have anything in the /fan/ directory.

Help please?

Also, if anyone can tell me this info, it would be awesome.  What's a general minimum speed for fans in laptops, and what's a general maximum?

---

### Post by VXxed on 2009-10-25
Someone has recommended me to try doing something with [this]("http://memebeam.org/toys/ToshibaAcpiDriver") to try to get it running, but I'm wondering if it will work.  I DO have the phoenix bios, though.  What do you guys think?

---

### Post by VXxed on 2009-10-25
before following the directions of post #1, with the acpi thing, I did what the directions in [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737) started telling me to do by setting up lm-sensors.  The problem is that when following the directions for setting up lm-sensors found here ( [http://ubuntuforums.org/showthread?t=2780](http://ubuntuforums.org/showthread?t=2780) ) my output for "sensors was:
```
ronen@vxtablet:~$ sensors
lm84-i2c-5-19
Adapter: SMBus I801 adapter at 14e0
Board Temp:   +0.0°C  (low  =  +0.0°C, high =  +0.0°C)  
CPU Temp:     +0.0°C  (low  =  +0.0°C, high =  +0.0°C)  
```

I don't know if this has anything to do with it, but when I did the "sudo sensors-detect" I got the following:
```
To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
adm1021
#----cut here----

```
I then followed the directions in the second guide for doing lm-sensors right, and two commands did not work.  This is what I ran:
```
ronen@vxtablet:~$ sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
ronen@vxtablet:~$ sudo modprobe i2c-i801
ronen@vxtablet:~$ sudo modprobe smartbatt
FATAL: Module smartbatt not found.
ronen@vxtablet:~$ sudo modprobe adm1021
ronen@vxtablet:~$ sudo depmod -a
ronen@vxtablet:~$ sudo update-modules
sudo: update-modules: command not found
```
Am I doing something wrong by not having a i2c-sensors?  What am I still doing wrong?

---

### Post by VXxed on 2009-10-25
I've tried doing a command in GRUB that forces ACPI but to no avail.  The exact thing I entered in the console was:```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=force"
```
Just in case the quotes are incorrect and unnecessary, I also did it without quotes. If there's a redundancy issue..well, I have no idea how to go and edit it. No clue how to edit Grub.

---

### Post by Sylslay on 2009-10-25
in linux apt-get install fancontrol
in winxp speedfan is ok if motherboard have sensors (3 pin on fan, instead 2pin)
if yours fun have only 2 pin-cable than you can't control its speed by manual

---

### Post by VXxed on 2009-10-25
Here are my results for that
```
ronen@vxtablet:~$ sudo apt-get install fancontrol
[sudo] password for ronen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fancontrol
```

---

### Post by VXxed on 2009-10-25
During boot up into Grub to edit its control of acpi, I noticed that in Grub, the fan works fine.  Works exactly the way it's supposed to, rather.  But as soon as Ubuntu boots up, fan control dies out and I'm shafted.  So I dropped that idea which was proposed in #ubuntu-bugs.

While looking around, I realized that there's .c files for several major brand names, some of them labeled [name]-acpi.c or [name]_acpi.c under a drivers folder in linux-source which I think is in /src/usr/

Looking at a toshiba one first, I found out that it has control over backlight and fans, and took a look at the fujitsu one, noticing that it has only backlight things, but no fan control.  I tried loading them by way of a guide found [here]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script").  Unfortunately that didn't work, and a friend advised me that that's not an executable file, but since it didn't even have fan control I didn't much continue to bother with it.

Realizing that it may be more of a brandname-linux interaction issue rather than a bios-linux issue I looked up "Fujitsu Fan Control" and stumbled upon [this]("http://bbs.archlinux.org/viewtopic.php?id=53702"), which also led to [this]("http://wiki.archlinux.org/index.php?title=DSDT&redirect=no"), and the ubuntu version, [this.]("https://help.ubuntu.com/community/ACPIBattery")

By the way, is this an adventurers journal?  I could really use some help before I start changing that DSDT.  One lasting thought on my mind is "should I try the UNR since it's geared for laptops and netbooks?"

---

### Post by VXxed on 2009-10-26
I'm going to bed now, so this ends my escapades for today, but once tomorrow starts I'm going to do and look over these links.  I'll edit this specific post once I've actually done it, need a place to store links until then.

[How to get fancontrol up and running]("http://ubuntuforums.org/showthread.php?t=42737")
--[How to install and config lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780")
[Various config's for tablets in Ubuntu]("http://ubuntuforums.org/showthread.php?t=563736") (irrelevant to issue on hand)
[Patch for the Fujitsu Driver file in linux-source?]("http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg08700.html") (Doesn't look like it has any fan control either)
[Linux ACPI project page]("http://www.lesswatts.org/projects/acpi/applying-patches.php") (May be useful for something later)
[http://sourceforge.net/projects/acpi/files/]("http://sourceforge.net/projects/acpi/files/") (Same as above)
[Text file all about ACPI's]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt")
[Phoenix Bios, looking for ACPI info]("http://www.phoenix.com/en/OEM-ODM/Customer+Services/White+Papers-Specs/Platform+System+Software+Documents/default.htm")
[ACPI component download page, except has unix source code]("http://www.acpica.org/downloads/unix_source_code_cont.php")
[Giant Ubuntu guide, has mostly same config directions for fanspeed]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29")
[fnfxd .3-14, update for Toshiba ACPI, but may have same fan control as Fujitsu?]("http://packages.debian.org/unstable/utils/fnfxd")
[Another Toshiba thing]("http://memebeam.org/toys/ExperimentalToshibaAcpiDriver")

[ACPI search on bug report area]("https://answers.launchpad.net/ubuntu/+questions?field.sort=by+relevancy&field.language-empty-marker=1&field.actions.search=Search&field.status=Open&field.status=Needs+information&field.status=Answered&field.status=Solved&field.search_text=acpi")
[Make a bug report (Most likely will need to actually resort to this)]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect")

Links in previous post:
[Fan control in .c files]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script")
[Another man's self discovery]("http://bbs.archlinux.org/viewtopic.php?id=53702")
[DSDT in ArchWiki]("http://wiki.archlinux.org/index.php?title=DSDT&redirect=no")
[DSDT in Ubuntu]("https://help.ubuntu.com/community/ACPIBattery")

ACPI Documentation: [1]("http://www.acpi.info/DOWNLOADS/ACPIspec40.pdf") [2]("http://www.acpica.org/download/aslcompiler.pdf") [3]("http://www.acpica.org/download/acpica-reference.pdf")

---

### Post by VXxed on 2009-10-27
Sorry to bump, but I really need an answer...I can't use my laptop safely without help

---

### Post by VXxed on 2009-10-27
To any who may view this thread in the near or far future with issues of the same sorts, I ended up filing an official bug report, found here: [https://bugs.launchpad.net/ubuntu/+bug/461675/](https://bugs.launchpad.net/ubuntu/+bug/461675/)

---

