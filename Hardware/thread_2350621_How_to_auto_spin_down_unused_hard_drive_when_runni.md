---
title: "How to auto spin down unused hard drive when running from SSD?"
date: 2017-01-26
forum: Hardware
---

### Post by efflandt on 2017-01-26
With people often running from SSD there may be cases when you want to automatically spin down an unused hard drive. In my case I am using mSATA SSD card (from failed laptop) in a SATA adapter as sdb for Ubuntu 16.10 and wanted to spin down (standby) sda (Win7 and previous 14.04) when not using that drive.

Not sure if there is a way to automatically have a modern drive automatically spin down (standby) when running from another drive. I forget how I did that on an old PC in my basement that has been running SuSE 8.2 - 24/7 as an experiment since 2003 (only shut down during power failures of unknown duration), but maybe the **hdparm -B** arg worked on older (20 & 30 GB) drives and I may have set the 2nd & 3rd drives to default to that. My current Western Digital 1 TB drive does not seem to support the -B arg:```
$ sudo hdparm -B 127 /dev/sda
/dev/sda:
 setting Advanced Power Management level to 0x7f (127)
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 51 40 7f 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 APM_level    = not supported
```And **sudo hdparm -S 120 /dev/sda** which I thought should put it into standby after 10 minutes seems to do nothing ever, **sudo hdparm -C /dev/sda** always showed it **active/idle**.

So I wrote a shell script to put in /etc/cron.hourly:
[LIST]
[*]If any partition on drive is mounted, do nothing, no logging. 
[*]If active/idle and NOT mounted, put into standby and log. 
[*]If already in standby, log only. 
[/LIST]
The script will do nothing if you are actually using the drive (if any partition on the drive is mounted). So it will do nothing for a drive you are running from, which is a bad idea anyway because logging would keep waking it up.```
#!/bin/sh
# Spin down drive(s) when idle and not mounted
# Put script in /etc/cron.hourly
drives="/dev/sda" # drive(s) to spin down (space separated)
IFS="$(printf '\n\t')" # remove newline from hdparm output
for hd in $drives
do
  dstate=$(/sbin/hdparm -C $hd | /bin/grep -B 1 standby)
  if [ $? -ne 0 ] # if not in standby
  then # active/idle
    /bin/grep $hd /etc/mtab 2>&1 > /dev/null
    if [ $? -ne 0 ] # do standby if not mounted
    then dstate=$(/sbin/hdparm -y $hd 2>&1)
    fi 
  fi
  if [ "$dstate" != '' ] # log unless mounted (null)
    then echo $dstate | /usr/bin/logger -e
  fi
done
```The **drives** variable can be a space separated list if you want to standby more than one drive. Apparently there is a smartd that monitors SMART data on drives (just don't believe temperature, because that is not actual degrees C), but ignores a drive in standby to not wake it up. Typical /var/log/syslog entries putting the drive into standby and once it is in standby:```
Jan 24 21:17:01 msata512-1610 CRON[25579]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 24 21:17:02 msata512-1610 root: /dev/sda:  issuing standby command
Jan 24 21:25:59 msata512-1610 smartd[678]: Device: /dev/sda [SAT], is in STANDBY mode, suspending checks
Jan 24 21:25:59 msata512-1610 smartd[678]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 70 to 72
Jan 24 21:55:59 msata512-1610 smartd[678]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 72 to 73
Jan 24 22:17:01 msata512-1610 CRON[25962]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 24 22:17:01 msata512-1610 root: /dev/sda:  drive state is:  standby
```This only saves about 5 watts (~48-49 watts at idle vs. ~54-55 watts measured in my case), but also minimizes wear of an unused drive for a computer on for long hours or 24/7.

---

### Post by Bucky Ball on 2017-01-26
Another way to get around this is to buy a Western Digital Green drive or one of the other 'eco-drives' which spin themselves down without user intervention.

When it comes to cutting your power bill, first place to start is the power supply unit as they can be the biggest waste of energy, but any saving anywhere is a good thing. ;)

---

### Post by Bruce_MAYO on 2017-04-05
Here's a different solution for Xubuntu 16.04; other distros may require locating files elsewhere. I wanted to keep an old IDE drive quiet, one that I only use for backup and for a second operating system. Even though it's not listed in /etc/fstab, this drive gets started at system start. "sudo hdparm -y  <device>" puts the IDE drive into the standby state (what I want), but after a resume from suspend (sleep) state it gets started again (audible, and shown by "sudo hdparm -C"). So I wanted two actions,
 
 -  one to call hdparm -y automatically at startup and 
 -  one to call hdparm -y at resume from suspend. 

For SATA drives, it seems you must use the option -S with a delay time; see man hdparm.


Simple enough, but there are two big problems: First, hdparm has to be called with root priviledges, but the Linux kernel won't give root privileges to a shell script called by some non-root user, even if it's owned by root and with the setuid bit ("chmod u+s") set. Second, Xubuntu 16.04 is no longer using the mechanism that was called pm-suspend; instead, it runs scripts in /lib/systemd/system-sleep/, contrary to what you find in most of the suspend/hibernate documentation (like man pm-suspend). (Many thanks to [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1455097](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1455097) .)

So first I wrote a little C program to call hdparm. Linux *will* honor the setuid bit in a binary file, so I used this like a shell script to call hdparm via the system command function, system(). All the same, you have to explicitly set the user to root (0).

[INDENT]/*           Sleep-sdc.c
  Put /dev/sdc in standby state, via hdparm
  compile: cc Sleep-sdc.c -o sleep-sdc
  copy to: /usr/local/bin
  then: 
     $sudo chown root: sleep-sdc
     $sudo chmod u+s  sleep-sdc
  For SATA drives, use hdparm -S 1         */

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
    [/INDENT]
[INDENT=2]setuid( 0 ); 
    system( "hdparm -y /dev/sdc" );
    system( "touch /home/bruce1/SDCSLEEP"); // to verify call; delete eventually
    return 0;[/INDENT]
[INDENT]  }
[/INDENT]

A preferred place for home-made utilities like this is /usr/local/bin. *After* copying the binary from where you compiled it, change the owner to root and set the s-bit.

To spin down the disk at start-up, add this executable to the list of tasks to start; in Xfce, from Applications > Settings > Session and Startup.

To spin down the disk after a resume from suspend/sleep, place this script in /lib/systemd/system-sleep. On wake-up, everything in this sub-directory gets called with the parameter "post".

[INDENT]#!/bin/sh
#                  sleep-sdc.sh
# puts /dev/sdc back into standby mode after wake-up (resume)
# place in  /lib/systemd/system-sleep
#
touch /home/bruce1/SLEEP-SDC-$1   # just for verification; delete eventually
case "$1" in
    [/INDENT]
[INDENT=2]post)
        [/INDENT]
[INDENT=2]   /usr/local/bin/sleep-sdc
[/INDENT]
[INDENT=2]         ;;
[/INDENT]
[INDENT] esac
[/INDENT]

Note that some disks may not respond to the hdparm commands correctly. If the drive gets written to now and then by any running processes, of course it makes little sense to spin it down. You can check this by issuing "sudo hdparm -S 1 <device>". With "sudo hdparm -C  <device>" watch for it to go into standby, then see if it changes back to active/idle. Laptop drives are meant to be stopped and started, but 3.5" drives should run continuously if they're accessed even infrequently.

---

