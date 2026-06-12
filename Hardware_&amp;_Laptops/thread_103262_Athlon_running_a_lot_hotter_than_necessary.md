---
title: "Athlon running a lot hotter than necessary"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Vati-Khan on 2005-12-13
Hi 

I'm currently having troubles configuring my System to enable the Athlon powersaving (halt) modes when idling.

my system:
Athlon XP 2500+ (~1.8 GHz)
VIA KT400 Chipset on a MSI -Board

In Windows I used a program called cpuidle to lower the CPU's temperature, und that way lower the CPU's fanspeed (it is a thermo-controlled fan, so there is no possibility to set fanspeed via software, but reading the fans rpm is possible under Windows). 

Now my situation using Breezy is somewhat unsatisfactory. Although some people state that software like cpuidle is not necessary in linux, I can definitely hear the difference. (CPU fan is much louder) Here is the output of possibly interesting programs:

```
root@Leon:/proc# powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
```

```
root@Leon:/proc# acpi -t
No support for device type: thermal
```

```
root@Leon:/proc# lsmod | grep cpufreq
cpufreq_userspace       4380  0
cpufreq_stats           5316  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
```

thanks in advance for your help

VK

---

### Post by voltsy on 2007-03-29
One solution: Read the Athlon powersaving HOWTO in your HOWTOS folder (or online)

The command line hack worked very well for me running Dapper: CPU temperature drops from 48 deg.C to 28 deg.C during idle time

my hardware is Athlon XP 1600+ on a SOYO(!) mobo with KT133 VIA chipset so my syntax is 

setpci -v -H1 -s 0:0.0 52=$(printf %x $((0x$(setpci -H1 -s 0:0.0 52) | 0x80)))

I even tested that identical syntax works when invoked from the sh shell - and yes it did!. This gave me the confidence to put the command into a bootup script: I chose bootmisc.sh which lurks in a folder called /etc/init.d

the setpci line is added below the line "rm -f /tmp/.clean" so it is always executed, not being nested inside an if..endif conditional statement. The computer is about as stable/unstable as it was before. Your kilometre-age may vary. Specifically the site [http://www.jochem.name/Athlon-Powersaving](http://www.jochem.name/Athlon-Powersaving) says the command line hack for KT400 chips is "experimental" so you would be very brave to risk corrupting your hard disk with that hardware setup.

N.B. make sure you can boot to a CDROM or floppy rescue configuration with text editor, because if you muck up a bootup script, especially one that changes registers in the chipset, you might be in serious doggy-do!

---

### Post by kerry_s on 2007-03-29
Athcool is the best for amd processors.

sudo apt-get install athcool

Then you want to add it to /etc/rc.local to start at every boot.

sudo gedit /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exec athcool on &

exit 0

---

### Post by kerry_s on 2007-03-29
voltsy> I chose bootmisc.sh which lurks in a folder called /etc/init.d

You should be running any root scripts in /etc/rc.local that is the purpose of the rc.local file.

---

### Post by yabbadabbadont on 2007-03-29
> **kerry_s said:**
> Athcool is the best for amd processors.

sudo apt-get install athcool

Then you want to add it to /etc/rc.local to start at every boot.

sudo gedit /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exec athcool on &

exit 0
Wow!  That dropped the CPU temp 5 degress C **immediately**.  After just a couple of minutes, it is now 10 degrees C cooler.  I'll have to do some testing to see if any of the warned about dangers manifest themselves, but if none do, I'll be adding this to rc.local too.  Thank you for the pointer!

Edit: It's running 12 degrees C cooler as I finish this post.  Amazing.

---

### Post by kerry_s on 2007-03-30
> **yabbadabbadont said:**
> Wow!  That dropped the CPU temp 5 degress C **immediately**.  After just a couple of minutes, it is now 10 degrees C cooler.  I'll have to do some testing to see if any of the warned about dangers manifest themselves, but if none do, I'll be adding this to rc.local too.  Thank you for the pointer!

Edit: It's running 12 degrees C cooler as I finish this post.  Amazing.

I've used it for ages now, it always cuts my operating temp by half. With out it i'm in the 60's, with it i have only reached 40's my average temp is 33 when using my system, when the system is idle it will be around 28.

---

### Post by yabbadabbadont on 2007-03-30
> **kerry_s said:**
> I've used it for ages now, it always cuts my operating temp by half. With out it i'm in the 60's, with it i have only reached 40's my average temp is 33 when using my system, when the system is idle it will be around 28.

I had replaced the stock cooler on my Athlon XP 2800+ and used Arctic Silver thermal grease.  Those two things had dropped the average temp to 48~50C idle and 59C under longterm continuous load.  With athcool it now runs 36C idle.  It still gets to 59C under load, but that is to be expected as the processor isn't idle.  It cools back down a lot quicker now though.

---

### Post by kerry_s on 2007-03-30
Hmmm, it's weird even with a load(many apps open) my temp still barely moves. Pic->

---

### Post by yabbadabbadont on 2007-03-30
> **kerry_s said:**
> Hmmm, it's weird even with a load(many apps open) my temp still barely moves. Pic->
Fire up glxgears and let it run for a couple of minutes...  Short of recompiling glibc, or running one of the 3D benchmark programs, that will peg your processor.

---

### Post by kerry_s on 2007-03-30
> **yabbadabbadont said:**
> Fire up glxgears and let it run for a couple of minutes...  Short of recompiling glibc, or running one of the 3D benchmark programs, that will peg your processor.

Yep, that will get it up a bit. It brings it up to between 48->51.

---

### Post by voltsy on 2007-03-30
> **kerry_s said:**
> 

sudo gedit /etc/rc.local


[INDENT]exec athcool on &

exit 0[/INDENT]



Thanks kerry_s for the advice about correct way to implement bootup tweaks. Your bean pile is much bigger than mine, so I urge everybody to adopt the correct procedure, not my risky hack of bootmisc.sh. 

I suppose two extra scripts to process is a trivial price (=time delay) to pay before the login prompt appears!

;-)

---

### Post by kerry_s on 2007-03-31
> **voltsy said:**
> Thanks kerry_s for the advice about correct way to implement bootup tweaks. Your bean pile is much bigger than mine, so I urge everybody to adopt the correct procedure, not my risky hack of bootmisc.sh. 

I suppose two extra scripts to process is a trivial price (=time delay) to pay before the login prompt appears!

;-)

LOL, beans don't count, trust me, half the time i might be wrong. rc.local is just safer and won't get updated and mess up your start up setup. There's no difference in time, it would be the same amount if you have it in init.d. My system still boots in just over 20 sec's and i have a ton of start ups.->

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exec athcool on &
exec sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
exec sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
exec rm -r /usr/share/doc/* &
exec rm -r /usr/share/man/* &
exec rm /var/log/*.gz &
exec rm /var/log/*.0 &
exec rm /var/log/*.log &
exec rm /var/log/*.old &
exec rm /var/log/acpid &
exec rm /var/log/dmesg &
exec rm /var/log/syslog &
exec rm /var/log/udev &

exit 0

---

