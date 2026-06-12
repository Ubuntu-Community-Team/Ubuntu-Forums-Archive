---
title: "Ubuntu 16.04 crashes approximately weekly"
date: 2016-12-14
forum: Hardware
---

### Post by liste on 2016-12-14
I didn't used to have any issues with 14.04, but since upgrading to 16.04, Ubuntu crash sporadically, more-or-less weekly on average.  The screen just freezes, but I can continue to use the mouse.  

I can switch TTYs using Ctrl+Alt+F1, but restarting lightdm brings me back to a frozen desktop screen.

I can also SSH into the machine and do what I want for there.

I have tried changing the graphics card, but to no avail.  I also tried the Nvida proprietary drivers (which I am no longer using), but the problem was pretty much the same (crashing once per week, able to SSH into the machine, etc.)

Today the machine acted as if it were going to crash (basically really slows down right before it crashes, the screen freezes temporarily and the returns to normal, and then normally ends of freezing permanently).  But this time it did not freeze permanently afterwards, and I got a "Crash report" dialog.  The Journal Error look interesting, but I'm not sure what to make of them:

```

Dec 14 13:53:42 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:43 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:44 username-ubuntu org.a11y.Bus[2055]: (process:2292): dconf-CRITICAL **: unable to create file '/home/username/.cache/dconf/user': Permission denied.  dconf will not work properly.
Dec 14 13:53:44
[...]

```

My username is not "username" so I'm not sure why anything should be trying to access it.  Where should I be debugging from here ?  It seems like I *might*&#8203; be close to finding a solution.

**EDIT: **this just happened again, for the second time today.  This time the JournalErrors still have the /username/ (which is not my username) in the path, but the error is somewhat different - apparently related to Nautilus this time.

```

Dec 14 15:10:44 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:44 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tree /home/username/.local/share/gvfs-metadata/home: open: Permission denied
Dec 14 15:10:45 username-ubuntu org.gnome.Nautilus[5946]: (nautilus:20724): GVFS-WARNING **: can't init metadata tr
[...]

```

---

### Post by l3v2 on 2016-12-16
hi,

was it really an upgrade or a fresh install?

had similar symptoms back in the day. i think it was on 12.04 or something. turned out my samsung drive was failing.

```
sudo apt-get install smartmontools
```
```
sudo smartctl -a /dev/sdX
```

what does smartctl report?

---

### Post by ajayzee on 2016-12-17
I have been having a similar issue. I thought this was the solution...
[https://ubuntuforums.org/showthread.php?t=2329709](https://ubuntuforums.org/showthread.php?t=2329709) but now I reckon these guys might have an explanation for it.. [http://hackaday.com/2016/12/16/reliably-exploiting-apport-in-ubuntu/](http://hackaday.com/2016/12/16/reliably-exploiting-apport-in-ubuntu/)

---

### Post by liste on 2017-03-01
Thank you so much for your reply, and sorry for taking so long to write back.

> **l3v2 said:**
> 
was it really an upgrade or a fresh install?

It was an upgrade from 14.04, which I'm pretty sure was the initial install.  I never had the problem on 14.04

> **l3v2 said:**
> 
what does smartctl report?

Here are the results from : [FONT=courier new]sudo smartctl -a /dev/sda[/FONT]

```

smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-62-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1002FAEX-00Z3A0
Serial Number:    WD-WMATR0933648
LU WWN Device Id: 5 0014ee 25c4449e7
Firmware Version: 05.01D05
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Mar  1 08:58:55 2017 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (16680) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 193) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   174   021    Pre-fail  Always       -       4158
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5808
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   047   047   000    Old_age   Always       -       39220
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       174
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       52
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5755
194 Temperature_Celsius     0x0022   107   096   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged

```

I have since managed to reduce the problem by keeping my RAM usage way down (trying not to use above 10GB out of 16), and the computer seems to be a lot less prone to crashing, so I'm wondering if it has something to do with my SWAP.

Nevertheless, I have had it crash a couple of time recently, and have managed to "restore" it (without rebooting) by using a combination of:

    1) Switching to TTY1 and back to 7, 
    2) Doing an rtcwake : [FONT=courier new]sudo rtcwake -m disk -s 60[/FONT]
    3) Logging out using, [FONT=courier new]export DISPLAY=:0[/FONT] and [FONT=courier new]gnome-session-quit


[/FONT]> **ajayzee said:**
> I have been having a similar issue. I thought this was the solution...
[https://ubuntuforums.org/showthread.php?t=2329709](https://ubuntuforums.org/showthread.php?t=2329709) but now I reckon these guys might have an explanation for it.. [http://hackaday.com/2016/12/16/reliably-exploiting-apport-in-ubuntu/](http://hackaday.com/2016/12/16/reliably-exploiting-apport-in-ubuntu/)

Thank you, I will definitely be looking into the logs and stuff in the future to see why this is happening.  Now I just have to have my computer crash at a convenient time when I have enough free time to look into the logs.  Maybe I'll just make a copy next time it crashes to have at least a backup from then.

---

### Post by betchern0t on 2017-03-02
In windows best practise is to reboot weekly. All our servers were setup to reboot early on monday morning. This was because Windows was notorious for memory leaks. It also tended to stop any other nasty crud building up. 

Was a time when I never experienced hangs, freezes or crashes on Linux. Today I am not as confident except on very dedicated boxes. My firewall running IPFire seems to run forever. My mythtv box is unstable enough that I am thinking about adding a cron job to reboot weekly. My openelec front ends sometimes also need a reboot. My desktop seems to be fairly unstable - of course today I have been loading and unloading drivers in a messy fashion. Equally I often get freezes in browser windows for some reason.

Bottom line is that if with the upgrade you have software either user or base OS that have memory leaks or other nasties, you may find you need to reboot on a regular basis. You could watch top and see if that gives you some clues - working set size of particular processes and if they increase for example.

HTH

Paul

---

