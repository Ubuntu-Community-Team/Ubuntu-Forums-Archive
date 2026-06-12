---
title: "Cpu temperature measure problem"
date: 2010-09-17
forum: Hardware
---

### Post by zeratull on 2010-09-17
I have Toshiba Satellite L505 13w, Core i5 M430 2.27 ghz, 4gb ram, 1gb ati display. OS: Ubuntu 10.04 

I tried every way but my problem is not solved.

What I tried is:

-I installed "sensors-applet and lm-sensors". I said everything yes but sensors could not found.
```
sudo sensors-detect
........
Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS. 
```

-I installed Conky.It shows many things except cpu temperature.

```
acpi -t 
``` returns empty.

```
acpi
Battery 0: Charging, 89%, 00:00:17 until charged

acpi -c
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 3
Cooling 3: Processor 0 of 3
Cooling 4: Processor 0 of 3 
```

-Gkrellm installed. no cpu temperature.

-Gdesklets installed.It did not work.

-Screenlets installed. It has many small modules in it.I tried them but still I could not measure cpu temp.

I did ```
sudo gedit  /usr/share/grub/default/grub 
``` I opened the file and changed it like this ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
``` then ```
sudo update-grub 
``` I restarted the system and tried ```
acpi -t
``` but nothing happened.

```
sensors
``` output is: ```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

```
cat /etc/modules 
``` output is: ```
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```

```
tosh@tosh-laptop:~$ apt-cache show sensors-applet
Package: sensors-applet
Priority: optional
Section: universe/gnome
Installed-Size: 656
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Sam Morris <sam@robots.org.uk>
Architecture: i386
Version: 2.2.3-2ubuntu1
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.23.2), libglib2.0-0 (>= 2.16.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.16.0), libice6 (>= 1:1.0.0), libnotify1 (>= 0.4.5), libnotify1-gtk2.10, liborbit2 (>= 1:2.14.10), libpanel-applet2-0 (>= 2.19.3), libpango1.0-0 (>= 1.14.0), libpopt0 (>= 1.14), libsensors-applet-plugin0, libsensors4 (>= 1:3.0.0-1), libsm6, libx11-6, libxext6, zlib1g (>= 1:1.1.4)
Recommends: hddtemp
Filename: pool/universe/s/sensors-applet/sensors-applet_2.2.3-2ubuntu1_i386.deb
Size: 104532
MD5sum: 1a7f9eb0898c94570c80e8b30b6f865e
SHA1: 726c8acc1a2fa17d56c70a62da6c9d277a512f79
SHA256: 3ce1d6d4604c383ad9258a806b7f32fa572b24ffea78a865f6b17ecb67d82740
Description: Display readings from hardware sensors in your Gnome panel
 GNOME Sensors Applet is an applet for the GNOME panel that displays
 readings from hardware sensors, including temperatures, fan speeds and
 voltage readings.
 .
 It can gather data from the following sources:
  * ACPI thermal zones, via the Linux kernel ACPI modules
  * Linux kernel i2c modules
  * lm-sensors (libsensors)
  * Linux kernel i8k module (for Dell Inspiron Laptops)
  * Linux kernel ibm-acpi module
  * Linux kernel PowerPC modules therm_adt746x and therm_windtunnel
  * Linux kernel iMac G5 Windfarm module
  * hddtemp daemon for reading temperatures from S.M.A.R.T. equipped hard disks
  * Linux kernel Omnibook module
  * NVIDIA graphics cards
  * Linux kernel sonypi module (for Sony Vaio laptops)
 .
 Alarms can be set for each sensor to notify the user once a certain high or
 low value has been reached, and can be configured to execute a given command
 at given repeated intervals.
Homepage: http://sensors-applet.sourceforge.net/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

tosh@tosh-laptop:~$ apt-cache show lm-sensors
Package: lm-sensors
Priority: extra
Section: utils
Installed-Size: 444
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Aurelien Jarno <aurel32@debian.org>
Architecture: i386
Source: lm-sensors-3
Version: 1:3.1.2-2
Depends: sed (>= 4.0.5-1), lsb-base (>= 3.2-13), libc6 (>= 2.3.4), libsensors4 (>= 1:3.1.1), perl
Recommends: fancontrol
Suggests: sensord, read-edid, i2c-tools
Filename: pool/main/l/lm-sensors-3/lm-sensors_3.1.2-2_i386.deb
Size: 115270
MD5sum: a8c79f12ee689a2028badd9e8462d083
SHA1: 0e38f0d19eb469c48f59783736d15d112cb38a49
SHA256: bdc9855f746583f745ff01a3121bfd6f83dd70e4a0416f5263afebbcbc6f7a9c
Description: utilities to read temperature/voltage/fan sensors
 Lm-sensors is a hardware health monitoring package for Linux. It allows you
 to access information from temperature, voltage, and fan speed sensors. It
 works with most newer systems.
 .
 This package contains programs to help you set up and read data from
 lm-sensors.
Homepage: http://www.lm-sensors.org
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, print-server, kubuntu-desktop, kubuntu-netbook, edubuntu-desktop, xubuntu-desktop, ubuntu-netbook

tosh@tosh-laptop:~$ sensors-detect
You need to be root to run this script.
tosh@tosh-laptop:~$ sudo sensors-detect
[sudo] password for tosh: 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: TOSHIBA Satellite L500 (laptop)
# Board: TOSHIBA NSWAA

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.
tosh@tosh-laptop:~$ sudo /etc/init.d/module-init-tools start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
module-init-tools stop/waiting
tosh@tosh-laptop:~$ 
 
```

I still can't measure cpu temperature. Is there any other way which I can try?

---

### Post by toffuuu on 2010-09-17
this is also something i would like to be at least included in with linux of any sort... how ever I am not using a notebook, and a more screamer gaming desktop is what i have.  lol i am really hoping someone out there is at least trying to make something that we all could use...

---

### Post by sikander3786 on 2010-09-17
lm-sensors work for me. I think your motherboard/cpu sensors are not supported by lm-sensors. See here.

[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

Also take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=687688](http://ubuntuforums.org/showthread.php?t=687688)

---

### Post by toffuuu on 2010-09-17
> **sikander3786 said:**
> lm-sensors work for me. I think your motherboard/cpu sensors are not supported by lm-sensors. See here.

[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

Also take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=687688](http://ubuntuforums.org/showthread.php?t=687688)

[LEFT]all Im saying is hopefully some one  will make the needed stuff for it to work, i would make it myself if I knew really how to do so,  and I am still in the learning phase so lol    cause I am also experiencing the no CPU temp readings but yes to my NVIDIA and HDD temp readings... and im using MSI 790XT-G45 motherboard and Phenom II 945 CPU, lets just hope maybe someone will make im-sensors support these  or make an entire different type of stuff that'll support what I got at least..
[/LEFT]

---

### Post by cbecker78 on 2010-10-13
@OP:  Did you ever get this resolved?  I know there were several threads getting this to work on toshiba laptops with V 9.10, you might try a search.  And don't limit to just the L505, as several models with toshiba share the problem with fan control.

Edit:  here, try the first few pages of [this search]("http://ubuntuforums.org/search.php?searchid=76608667")

---

### Post by Blasphemist on 2010-10-13
I also have a Toshiba Satellite L505 though older than yours. I ran across something that might have to do with your issue. Does your BIOS support ACPI and not APM? Search the Ubuntu software center for Toshiba and you'll see a number of items that may help you.

---

### Post by linuxaek on 2011-01-15
A useful site is [http://www.cyberciti.biz/faq/linux-laptop-battery-status-temperature/]("http://www.cyberciti.biz/faq/linux-laptop-battery-status-temperature/") I found when searching about this issue.

---

