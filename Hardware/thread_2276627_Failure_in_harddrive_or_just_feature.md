---
title: "Failure in harddrive or just feature:"
date: 2015-05-04
forum: Hardware
---

### Post by leopard2 on 2015-05-04
Hi, my small broblem is really slow disk io that started about 3 weeks ago, before that everyting runs normal

for example:
command 'htop' took about 30sec before I got info that is not installed and should use apt-get install etc.
'iotop' takes 12sec to start first time, but second start is instant (from cache?)
browser (ff/chrome) takes 1-2 minutes to start, but after start it runs smoothly. Same with games (diablo 3 /wow) those loads like 15min, but after loading, game itself runs nicely.


I don't know what information would be good to have, but [http://ubuntuforums.org/showthread.php?t=2264326](http://ubuntuforums.org/showthread.php?t=2264326) thread recommended to having those commands :p

```
 
leopard@leodesk:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=89a7a789-41e5-488a-9f63-f39a96415693 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d5aee6c-a596-4720-9f81-2c86edac41e9 none            swap    sw              0       0

```

```

leopard@leodesk:~$ head -n 5 /proc/meminfo
MemTotal:        8175700 kB
MemFree:         6602836 kB
Buffers:           73720 kB
Cached:           689140 kB
SwapCached:            0 kB

```


```

leopard@leodesk:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    8385532    0    -1

```


Some errors from ' egrep -i 'error|warning' /var/log/*log ' :
```

/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.12-0.2ubuntu1_amd64.deb ...
/var/log/bootstrap.log:Unpacking libgpg-error0:amd64 (1.12-0.2ubuntu1) ...
/var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.12-0.2ubuntu1) ...
/var/log/kern.log:May  4 07:20:33 leodesk kernel: [   78.102767] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PM2S 1 (20131115/utaddress-251)
/var/log/kern.log:May  4 07:20:33 leodesk kernel: [   78.102778] ACPI Warning: 0x00000000000004b0-0x00000000000004bf SystemIO conflicts with Region \GPO2 1 (20131115/utaddress-251)
/var/log/kern.log:May  4 07:20:33 leodesk kernel: [   78.102784] ACPI Warning: 0x0000000000000480-0x00000000000004af SystemIO conflicts with Region \GPO_ 1 (20131115/utaddress-251)
/var/log/kern.log:May  4 07:20:33 leodesk kernel: [   94.035911] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/nvidia-installer.log:WARNING: The NVIDIA GeForce 7900 GT/GTO GPU installed in this system is supported through the NVIDIA 304.xx legacy Linux graphics drivers.  Please visit http://www.nvidia.com/object/unix.html for more information.  The 337.25 NVIDIA Linux graphics driver will ignore this GPU.
/var/log/nvidia-installer.log:WARNING: You do not appear to have an NVIDIA GPU supported by the 337.25 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at www.nvidia.com.
/var/log/nvidia-installer.log:ERROR: The Nouveau kernel driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.  Please consult the NVIDIA driver README and your Linux distribution's documentation for details on how to correctly disable the Nouveau kernel driver.
/var/log/nvidia-installer.log:ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/syslog:May  4 07:20:33 leodesk kernel: [   78.102767] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PM2S 1 (20131115/utaddress-251)
/var/log/syslog:May  4 07:20:33 leodesk kernel: [   78.102778] ACPI Warning: 0x00000000000004b0-0x00000000000004bf SystemIO conflicts with Region \GPO2 1 (20131115/utaddress-251)
/var/log/syslog:May  4 07:20:33 leodesk kernel: [   78.102784] ACPI Warning: 0x0000000000000480-0x00000000000004af SystemIO conflicts with Region \GPO_ 1 (20131115/utaddress-251)
/var/log/syslog:May  4 07:20:33 leodesk kernel: [   94.035911] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/syslog:May  4 07:21:01 leodesk whoopsie[1073]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
/var/log/syslog:May  4 07:21:07 leodesk NetworkManager[1041]: <error> [1430713267.33847] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:May  4 07:21:09 leodesk dnsmasq[1107]: warning: no upstream servers configured
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.1.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.1.log:[  1923.840] (WW) Warning, couldn't open module nvidia
/var/log/Xorg.1.log:[  1923.843] (WW) Warning, couldn't open module nvidia

```


```

leopard@leodesk:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/sda1               222G   68G  143G  32% /
none                    4,0K     0  4,0K   0% /sys/fs/cgroup
udev                    3,9G   12K  3,9G   1% /dev
tmpfs                   799M  1,3M  798M   1% /run
none                    5,0M     0  5,0M   0% /run/lock
none                    3,9G   88K  3,9G   1% /run/shm
none                    100M   28K  100M   1% /run/user
/home/leopard/.Private  222G   68G  143G  32% /home/leopard

```

and smart data for extra (I think temperature thing has been there earlier too, not 100% sure):
```

leopard@leodesk:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE Serial ATA
Device Model:     WDC WD2500JS-00NCB1
Serial Number:    WD-WCANK5632038
Firmware Version: 10.02E02
User Capacity:    250 059 350 016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 (minor revision not indicated)
Local Time is:    Mon May  4 08:04:38 2015 EEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 8280) seconds.
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
recommended polling time:      (  96) minutes.
Conveyance self-test routine
recommended polling time:      (   6) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   190   186   021    Pre-fail  Always       -       5500
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3418
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   054   054   000    Old_age   Always       -       33835
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3370
190 Airflow_Temperature_Cel 0x0022   050   027   045    Old_age   Always   In_the_past 50
194 Temperature_Celsius     0x0022   100   077   000    Old_age   Always       -       50
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       16
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%     33721         -
# 2  Short offline       Completed without error       00%     33720         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

---

### Post by dino99 on 2015-05-04
check that at least 15 % of disk space is still free
maybe force a fsck

---

### Post by leopard2 on 2015-05-04
Yeah, I do have free space.  

I gave commands: 
sudo touch /forcefsck 
sudo reboot  

but files checkfs and checkroot in /var/log/fsck are empy.   

but in: /var/log/upstart/mountall.log has: 
 ```
 

leopard@leodesk:/var/log/upstart$ sudo cat mountall.log
fsck from util-linux 2.20.1
/dev/sda1: clean, 784054/14745600 files, 18532696/58952704 blocks
mountall: Plymouth command failed
mountall: Disconnected from Plymouth
fsck from util-linux 2.20.1
/dev/sda1: 784264/14745600 files (0.4% non-contiguous), 18520257/58952704 blocks
mountall: Plymouth command failed
mountall: Disconnected from Plymouth

```

---

### Post by kerry_s on 2015-05-04
from your log, you don't have the correct vid driver.

sudo apt-get install nvidia-304

---

### Post by leopard2 on 2015-05-04
I should have?


```

leopard@leodesk:~$ sudo apt-get install nvidia-304
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-304 is already the newest version.
The following packages were automatically installed and are no longer required:
  ca-certificates-java default-jre default-jre-headless firefox-locale-fi
  fonts-dejavu-extra gnome-terminal-data icedtea-7-jre-jamvm java-common
  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common
  libcublas5.5 libcudart5.5 libcufft5.5 libcufftw5.5 libcurand5.5
  libcusparse5.5 libgconf2-4 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomevfs2-0 libgnomevfs2-common libidl-common libidl0 libnppc5.5
  libnppi5.5 libnpps5.5 libnvtoolsext1 libnvvm2 liborbit-2-0 liborbit2
  libthrust-dev libvdpau-dev libvoikko1 linux-image-generic nvidia-cuda-doc
  nvidia-cuda-gdb opencl-headers openjdk-7-jre openjdk-7-jre-headless
  tzdata-java voikko-fi xul-ext-mozvoikko
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.



```
edit2: huh, there was a lot 'useless' stuff... started apt-get autoremove ~700MB

edit: I did remember that I tried install CUDA but it failed, it was 2-3 weeks before slow downs. but because I didn't boot after failed CUDA install, I can't say did it do something.

---

### Post by kerry_s on 2015-05-04
you got 15 updates to-> sudo apt-get dist-upgrade

so it looks like you have it installed, but you have some other version installed thats getting in the way.

my suggestion is install synaptic, so you can see better from a gui, then purge that other nvidia driver

sudo apt-get install synaptic

open it, click on status on the left, then on installed, in the center search type "nvidia", it should then show what you have.

---

### Post by dino99 on 2015-05-04
to get rid of all unnecessary nvidia stuff, purge them all before reinstalling the required one
> sudo apt-get purge nvidia*

---

### Post by leopard2 on 2015-05-04
started installing synaptic, just noticed that Firefox reads some bytes but uses more IO than apt-get? [http://i.imgur.com/jl7edKQ.png](http://i.imgur.com/jl7edKQ.png) does that look normal?  (same thing happens if it's chromium or some other software that uses disk) (and disk light flash nonstop even after apt-get has ended).

```

sudo apt-get purge nvidia*

```
I did that with 12.04 (or 12.10) my PC was so broken after that :D

---

### Post by leopard2 on 2015-05-04
> **kerry_s said:**
> you got 15 updates to-> sudo apt-get dist-upgrade
so it looks like you have it installed, but you have some other version installed thats getting in the way.
my suggestion is install synaptic, so you can see better from a gui, then purge that other nvidia driver
sudo apt-get install synaptic
open it, click on status on the left, then on installed, in the center search type "nvidia", it should then show what you have.

did apt-get update & upgrade

but that synaptic says: [http://i.imgur.com/Fu9iu8G.png](http://i.imgur.com/Fu9iu8G.png) nVidia settings seems to have different version? but other than that, everything seems to be ok?

---

### Post by kerry_s on 2015-05-04
settings is not a driver so should be okay.

completely remove "residual' & "local ..." stuff to make sure no junk is left.

should be clean like mine, no junk.

---

### Post by leopard2 on 2015-05-04
> **kerry_s said:**
> 
completely remove "residual' & "local ..." stuff to make sure no junk is left.


Looks like I'm going to do backup today and full install tomorrow, if fresh install is slow then I can be sure its hardware broblem. Too bad I have only 32b  (L/X)buntu DVDs atm. (computer doesn't boot from usb)

Anyway, thanks for answers, that synaptic was new to me I tought it was some touchpad driver before.

---

### Post by leopard2 on 2015-05-04
Ok... little after backups HD start keeping small "click hrrr click hrrr" noise... so I think its somewhat dead now... Tho, for positive thing, its good reason to upgrade SSD to it ^^

---

