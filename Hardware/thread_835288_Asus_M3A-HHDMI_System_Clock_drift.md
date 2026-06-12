---
title: "Asus M3A-H/HDMI System Clock drift"
date: 2008-06-20
forum: Hardware
---

### Post by am4c130d on 2008-06-20
Hi,

I have an ASUS M3A-H/HDMI motherboard, with an Athlon 64 X2 4200+ 65W CPU, 2 GB of DRAM and 2 TB of disk acting as a server.  The system runs Hardy 32 bit Server version.  I upgraded the motherboard from an ABit IS7, which was suffering some serious hardware stability issues - the upgrade was little more than swap the board in and tweak the network udev file to recognise the new Ethernet port as eth0 - Linux hotplug etc. took care of everything else (even as a Linux user of 8+ years, and an Ubuntu user since Hoary - I was pretty impressed).  

The problem I have is that the system clock appears to be very inaccurate.  I run ntpd (and have done for four or five years) which is configured to grab 6 ntp servers from pool.ntp.org, so I am very confident that the clock source is good, and with the abit board the system clock was rock solid.  Since the upgrade the clock drifts by 2.5 seconds every 15 to 16 minutes - syslog shows an ntpd driven clock reset of about 2.2-2.5 seconds every 15-16 minutes.  I have deleted /var/lib/ntp/ntp.drift and run ntptime -f 0 to clear the clock frequency settings that may have been left over from the old install.

I've checked system clock current and it shows that I am using hpet - which from everything I've read should be excellent.  I've forced the system to use acpi_pm instead, both by booting to that mode as well as simply switching it, these changes made no difference.

I've upgraded the BIOS to 0604, which is the latest.

I am pretty confident that the configuration is OK as it has worked for years, but of course I may have missed some key part when I upgraded, any ideas where to check would be greatly appreciated. The only difference in setup between the working abit version and not working asus version is that I have /var and /home on different partitions now.  Also, I have noticed that ntp, which is now started very early in the boot cycle doesn't have the external clock references when the system boots and requires a manual reset - I suspect it has to do with the Ethernet port not being up when NTP is first started and somehow not being stopped and restarted properly when the interface does come up.

Has anyone experienced the same clock issues with this chipset/board?  Equally, if people have not experienced this issue, and do have NTP and this board working well, please let me know - I can RMA the board.

This aside, as I have read elsewhere, the board appears to be very compatible with Hardy...

TIA,

Alan

---

### Post by am4c130d on 2008-06-29
Problem Solved - or at least worked around!

In the end I used adjtimex to change the ticks from 10000 to 10026.  NTP was then able maintain a steady state and finally dialed in the clock.  The clock has been very stable since and is within a few microseconds of the reference clocks - more than accurate enough for my needs.

The steps I used were as follows

1.  Checked /boot/config-XXX to confirm that the system was set to a 100 Hz clock.

2. Worked out the drift per second, by dividing the reset time step (in may case about 2.5 seconds) by the interval between the previous reset and the current reset (in my case about 15 minutes).  

3. Converted that in to ticks (which are at a frequency of 1 per 100 microseconds) 

4. As my system was jumping forward at each reset, thus losing time, I added the value I obtained, (about 26) to 10000 - this is the number of ticks per second!

5.  Stopped NTP 

6. Deleted /var/lib/ntp/ntp.drift (removes NTP's previous impressions of the clock drift)

7.  Issued sudo adjtimex -t 10026, 

8.  Restarted NTP and sat back.  

As I have iburst, an initial sync was quite quick, but the real sync, when it polls over 1024 seconds, took best part of day.  ntptime and adjtimex both show that the frequency correction is now -113 microseconds, and has been stable for five days.  The frequency correction does imply that I should change the ticks setting in adjtimex from 10026 to 10025 - but its not that important for me as I always have NTP available.

To be frank, I am not convinced that this is an appropriate solution.  It does imply that something is wrong with the clock source, and I have read of so many instances where a BIOS upgrade addresses the problem - but I am on the latest BIOS, so that may be for the future...

---

### Post by jape42 on 2008-11-08
Asus m3A78 pro motherboard has the same problem even with current bios.  Thanks for posting this.  This solution seems to work for me too

regards

jp

---

### Post by am4c130d on 2009-06-30
And lo and behold, upgraded my BIOS for other reasons to 1504, and NTP was resetting every 15 or so minutes by -2.5 seconds.  Reset adjtimex back to 10000 and am back in sync...  Just a BIOS upgrade issue!

---

### Post by cjstokyo on 2010-04-03
The */usr/sbin/adjtimexconfig* command will calculate an appropriate adjustment for you. This is run automatically when you install the adjtimex package, and should be run manually after any BIOS or hardware change. See my blog post [Making NTP Work on Hardware with Large Clock Drift]("http://www.starling-software.com/en/blog/sysadmin/2010/04/04.making-ntp-work-on-hardware-with-large-clock-drift.html") if you'd like more details.

---

