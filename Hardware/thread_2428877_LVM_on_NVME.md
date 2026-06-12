---
title: "LVM on NVME"
date: 2019-10-10
forum: Hardware
---

### Post by w1t3c on 2019-10-10
Hello,
One of my friends (java developer) get random OS freezes on his new workstation.
I gues it can be ssd issue, but I'm not sure how to interpret smartctl output.
Please check those outputs.

PC spec:
RAM [COLOR=#1C1C1B][FONT=Verdana]ADATA 16GB DDR4 3200MHZ CL16
CPU [/FONT][/COLOR][COLOR=#1C1C1B][FONT=Verdana]AMD [/FONT][/COLOR][COLOR=#1C1C1B][FONT=Verdana]RYZEN[/FONT][/COLOR][COLOR=#1C1C1B][FONT=Verdana] 5 3600
[/FONT][/COLOR][COLOR=#1C1C1B][FONT=Verdana]GPU PALIT CUDA GT710 2GB
SSD [/FONT][/COLOR]ADATA 256GB M.2 PCIe NVMe XPG GAMMIX S5[COLOR=#1C1C1B][FONT=Verdana]
[/FONT][/COLOR]MB MSI B450M PRO-VDH PLUS
PSU SilentiumPC Zephyr 120

root@Workstation-TT:~# lsb_release -a
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic


```

root@Workstation-TT:~# df -h
```
System plików               rozm. u&#380;yte dost. %u&#380;. zamont. na
udev                         7,8G     0  7,8G   0% /dev
tmpfs                        1,6G  2,1M  1,6G   1% /run
/dev/mapper/ubuntu--vg-root  233G   30G  192G  14% /
tmpfs                        7,9G  127M  7,8G   2% /dev/shm
tmpfs                        5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        7,9G     0  7,9G   0% /sys/fs/cgroup
/dev/loop1                    55M   55M     0 100% /snap/core18/1192
/dev/loop2                   150M  150M     0 100% /snap/gnome-3-28-1804/71
/dev/nvme0n1p1               511M  6,1M  505M   2% /boot/efi
/dev/loop3                    55M   55M     0 100% /snap/core18/1144
/dev/loop5                   4,2M  4,2M     0 100% /snap/gnome-calculator/406
/dev/loop4                   218M  218M     0 100% /snap/wine-platform-runtime/30
/dev/loop0                    74M   74M     0 100% /snap/wine-platform-3-stable/6
/dev/loop6                   3,8M  3,8M     0 100% /snap/gnome-system-monitor/100
/dev/loop7                   150M  150M     0 100% /snap/gnome-3-28-1804/67
/dev/loop8                    15M   15M     0 100% /snap/gnome-characters/296
/dev/loop10                   15M   15M     0 100% /snap/gnome-characters/317
/dev/loop9                   218M  218M     0 100% /snap/wine-platform-runtime/37
/dev/loop11                   90M   90M     0 100% /snap/core/7713
/dev/loop12                   89M   89M     0 100% /snap/core/7270
/dev/loop13                   43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop14                  1,0M  1,0M     0 100% /snap/gnome-logs/81
/dev/loop15                  147M  147M     0 100% /snap/slack/17
/dev/loop16                  3,9M  3,9M     0 100% /snap/notepad-plus-plus/212
/dev/loop17                  4,3M  4,3M     0 100% /snap/gnome-calculator/501
/dev/loop18                  1,0M  1,0M     0 100% /snap/gnome-logs/73
tmpfs                        1,6G   12K  1,6G   1% /run/user/121
tmpfs                        1,6G   56K  1,6G   1% /run/user/1000
/dev/loop19                  147M  147M     0 100% /snap/slack/18
tmpfs                        1,6G     0  1,6G   0% /run/user/1001



```


root@Workstation-TT:~# smartctl -a /dev/nvme0n1
```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.0.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Number:                       XPG GAMMIX S5
Serial Number:                      2J2320002639
Firmware Version:                   V9001c19
PCI Vendor/Subsystem ID:            0x10ec
IEEE OUI Identifier:                0x00e04c
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          256&#8239;060&#8239;514&#8239;304 [256 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Thu Oct 10 14:06:09 2019 CEST
Firmware Updates (0x02):            1 Slot
Optional Admin Commands (0x0006):   Format Frmw_DL
Optional NVM Commands (0x0014):     DS_Mngmt Sav/Sel_Feat
Maximum Data Transfer Size:         32 Pages
Warning  Comp. Temp. Threshold:     118 Celsius
Critical Comp. Temp. Threshold:     150 Celsius


Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     8.00W       -        -    0  0  0  0        0       0
 1 +     4.00W       -        -    1  1  1  1        0       0
 2 +     3.00W       -        -    2  2  2  2        0       0
 3 -   0.0128W       -        -    3  3  3  3     4000    8000
 4 -   0.0080W       -        -    4  4  4  4     8000   30000


Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0


=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


SMART/Health Information (NVMe Log 0x02, NSID 0x1)
Critical Warning:                   0x00
Temperature:                        36 Celsius
Available Spare:                    100%
Available Spare Threshold:          32%
Percentage Used:                    0%
Data Units Read:                    703&#8239;878 [360 GB]
Data Units Written:                 998&#8239;067 [511 GB]
Host Read Commands:                 4&#8239;588&#8239;622
Host Write Commands:                5&#8239;763&#8239;985
Controller Busy Time:               0
Power Cycles:                       23
Power On Hours:                     20
Unsafe Shutdowns:                   9
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0


[COLOR=#ff0000]Error Information (NVMe Log 0x01, max 8 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0          1     0  0x0000  0x0000  0x000            0     0     -
  6 1219368206019409473     0  0x0000  0x0000  0x000            0     0     -[/COLOR]


```
root@Workstation-TT:~# nvme --smart-log /dev/nvme0n1
```
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 36 C
available_spare                     : 100%
available_spare_threshold           : 32%
percentage_used                     : 0%
data_units_read                     : 703&#8239;883
data_units_written                  : 998&#8239;825
host_read_commands                  : 4&#8239;588&#8239;883
host_write_commands                 : 5&#8239;770&#8239;518
controller_busy_time                : 0
power_cycles                        : 23
power_on_hours                      : 20
unsafe_shutdowns                    : 9
media_errors                        : 0
num_err_log_entries                 : 0
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0



```
root@Workstation-TT:~# nvme --error-log /dev/nvme0n1
```
Error Log Entries for device:nvme0n1 entries:8
.................
 Entry[ 0]
.................
error_count  : 1
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 1]
.................
error_count  : 0
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 2]
.................
error_count  : 0
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 3]
.................
error_count  : 0
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 4]
.................
error_count  : 0
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 5]
.................
error_count  : 0
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 6]
.................
error_count  : 1219368206019409473
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................
 Entry[ 7]
.................
error_count  : 0
sqid         : 0
cmdid        : 0
status_field : 0(SUCCESS)
parm_err_loc : 0
lba          : 0
nsid         : 0
vs           : 0
.................



```

---

### Post by TheFu on 2019-10-10
So get useful smartctl output, you have to run some tests first.

```
sudo smartclt -t long /dev/sda
```
    or
```
sudo smartclt -t short /dev/sda
```
Then you ask for the report with 
```
sudo smartclt -a /dev/sda
```

smart works on the entire disk, not any specific partition.  I don't know NVMe devices names, but if /dev/nvme0n1 is for partition1, then /dev/nvme0n is probably the device name you want - or /dev/nvme0  IDK.

---

### Post by TheFu on 2019-10-10
What does LVM have to do with anything here?  It is in the title, but I don't see any mention of it.  I came to help with LVM.

---

### Post by w1t3c on 2019-10-11
> **TheFu said:**
> So get useful smartctl output, you have to run some tests first.


```
sudo smartclt -t long /dev/sda
```
or
```
sudo smartclt -t short /dev/sda
```
Then you ask for the report with 
```
sudo smartclt -a /dev/sda
```


smart works on the entire disk, not any specific partition. I don't know NVMe devices names, but if /dev/nvme0n1 is for partition1, then /dev/nvme0n is probably the device name you want - or /dev/nvme0 IDK.


Thanks for reply, but please check output of my df -h in previous post. There is no sda/b/c/... Root is installed on LVM2 partition


```
root@Workstation-TT:~# ls /dev/autofs           cuse      fuse       hugepages  i2c-15  initctl   loop12  loop20  loop-control      network_throughput  psaux   snapshot  tty11  tty2   tty28  tty36  tty44  tty52  tty60      ttyS1   ttyS18  ttyS26  ttyS6      userio  vcsa1  vcsu3        zero
block            disk      gpiochip0  hwrng      i2c-2   input     loop13  loop21  lp0               null                ptmx    snd       tty12  tty20  tty29  tty37  tty45  tty53  tty61      ttyS10  ttyS19  ttyS27  ttyS7      vcs     vcsa2  vcsu4
btrfs-control    dm-0      gpiochip1  i2c-0      i2c-3   kmsg      loop14  loop3   mapper            nvme0               pts     stderr    tty13  tty21  tty3   tty38  tty46  tty54  tty62      ttyS11  ttyS2   ttyS28  ttyS8      vcs1    vcsa3  vcsu5
bus              dm-1      hidraw0    i2c-1      i2c-4   lightnvm  loop15  loop4   mcelog            nvme0n1             random  stdin     tty14  tty22  tty30  tty39  tty47  tty55  tty63      ttyS12  ttyS20  ttyS29  ttyS9      vcs2    vcsa4  vcsu6
char             dri       hidraw1    i2c-10     i2c-5   log       loop16  loop5   mem               nvme0n1p1           rfkill  stdout    tty15  tty23  tty31  tty4   tty48  tty56  tty7       ttyS13  ttyS21  ttyS3   ubuntu-vg  vcs3    vcsa5  vfio
console          ecryptfs  hidraw2    i2c-11     i2c-6   loop0     loop17  loop6   memory_bandwidth  nvme0n1p2           rtc     tty       tty16  tty24  tty32  tty40  tty49  tty57  tty8       ttyS14  ttyS22  ttyS30  udmabuf    vcs4    vcsa6  vga_arbiter
core             fb0       hidraw3    i2c-12     i2c-7   loop1     loop18  loop7   mqueue            parport0            rtc0    tty0      tty17  tty25  tty33  tty41  tty5   tty58  tty9       ttyS15  ttyS23  ttyS31  uhid       vcs5    vcsu   vhci
cpu              fd        hidraw4    i2c-13     i2c-8   loop10    loop19  loop8   net               port                sev     tty1      tty18  tty26  tty34  tty42  tty50  tty59  ttyprintk  ttyS16  ttyS24  ttyS4   uinput     vcs6    vcsu1  vhost-net
cpu_dma_latency  full      hpet       i2c-14     i2c-9   loop11    loop2   loop9   network_latency   ppp                 shm     tty10     tty19  tty27  tty35  tty43  tty51  tty6   ttyS0      ttyS17  ttyS25  ttyS5   urandom    vcsa    vcsu2  vhost-vsock





```


Following Your advice I ran 
```
root@Workstation-TT:~# smartctl -t long /dev/nvme0
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.0.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org




NVMe device successfully opened




Use 'smartctl -a' (or '-x') to print SMART (and more) information

```


But not much changed 
```
root@Workstation-TT:~# smartctl -a /dev/nvme0
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.0.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org




=== START OF INFORMATION SECTION ===
Model Number:                       XPG GAMMIX S5
Serial Number:                      2J2320002639
Firmware Version:                   V9001c19
PCI Vendor/Subsystem ID:            0x10ec
IEEE OUI Identifier:                0x00e04c
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          256&#8239;060&#8239;514&#8239;304 [256 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Fri Oct 11 11:16:58 2019 CEST
Firmware Updates (0x02):            1 Slot
Optional Admin Commands (0x0006):   Format Frmw_DL
Optional NVM Commands (0x0014):     DS_Mngmt Sav/Sel_Feat
Maximum Data Transfer Size:         32 Pages
Warning  Comp. Temp. Threshold:     118 Celsius
Critical Comp. Temp. Threshold:     150 Celsius




Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     8.00W       -        -    0  0  0  0        0       0
 1 +     4.00W       -        -    1  1  1  1        0       0
 2 +     3.00W       -        -    2  2  2  2        0       0
 3 -   0.0128W       -        -    3  3  3  3     4000    8000
 4 -   0.0080W       -        -    4  4  4  4     8000   30000




Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0




=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED




SMART/Health Information (NVMe Log 0x02, NSID 0xffffffff)
Critical Warning:                   0x00
Temperature:                        38 Celsius
Available Spare:                    100%
Available Spare Threshold:          32%
Percentage Used:                    0%
Data Units Read:                    704&#8239;892 [360 GB]
Data Units Written:                 1&#8239;024&#8239;205 [524 GB]
Host Read Commands:                 4&#8239;615&#8239;028
Host Write Commands:                5&#8239;996&#8239;943
Controller Busy Time:               0
Power Cycles:                       23
Power On Hours:                     22
Unsafe Shutdowns:                   9
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0




[COLOR=#ff0000]Error Information (NVMe Log 0x01, max 8 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0          1     0  0x0000  0x0000  0x000            0     0     -
  6 1219368206019409473     0  0x0000  0x0000  0x000            0     0     -[/COLOR]





```

---

### Post by w1t3c on 2019-10-11
> **TheFu said:**
> What does LVM have to do with anything here?  It is in the title, but I don't see any mention of it.  I came to help with LVM.

I'm not sure. Just considering possibility that LVM2 partition can have some issues on M.2 NVME drive...

---

### Post by TheFu on 2019-10-11
A "long" test usually requires a few hours to complete.  Then run the "report" command.

Looking at that huge error count, which I've never seen before, I'm surprised the storage works at all.

I knew you didn't have an sda.  It was an example for lurkers with an explanation.

---

### Post by w1t3c on 2019-10-11
> **TheFu said:**
> A "long" test usually requires a few hours to complete.  Then run the "report" command.

Looking at that huge error count, which I've never seen before, I'm surprised the storage works at all.

I knew you didn't have an sda.  It was an example for lurkers with an explanation.

It proof that I do something wrong.
In my case 
smartctl -t long /dev/nvme0
takes less than 1s.

---

### Post by oldfred on 2019-10-11
Have you updated UEFI. Others say that solves lots of issue. And if SSD, update SSD firmware, (even if new system).

AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates last week as a "beta" though without explicitly acknowledging the Linux fix. 
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)

---

### Post by w1t3c on 2019-10-11
> **oldfred said:**
> Have you updated UEFI. Others say that solves lots of issue. And if SSD, update SSD firmware, (even if new system).

AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates last week as a "beta" though without explicitly acknowledging the Linux fix. 
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)

Thanks for Your post.
In my case i had to update BIOS because Stock BIOS did not work with Ryzen 3000 series. Now this PC had 7A38v96 (2019-09-02). I will try update this BIOS to latest-greatest in Monday...

---

### Post by TheFu on 2019-10-11
sudo?
Is SMART enabled in the BIOS/firmware?

Completely unrelated, but I updated my Asus B450 ROG firmware over the weekend.  That process wiped all the prior custom settings, including disabling AMD-v so my VMs wouldn't come up automatically.  Took way too long for me to figure that out after it was stuck in a reboot cycle. I wasted tiem tweaking storage, secure boot, OC and a bunch of other futile settings in the middle of an afternoon. At least it was a Sunday.  I was not happy.  I have a Ryzen 5 2600.

---

### Post by TheFu on 2019-10-11
> **w1t3c said:**
> It proof that I do something wrong.
In my case 
smartctl -t long /dev/nvme0
takes less than 1s.

```
$ sudo smartctl -t long /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-65-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
**Please wait 85 minutes for test to complete.**
Test will complete after Fri Oct 11 16:14:28 2019

Use smartctl -X to abort test.

```
This was for a laptop.
```
           ID-1: /dev/sda model: Samsung_SSD_860 size: 500.1GB
```
I don't have any NVMe. On a desktop:
On a```

           ID-2: /dev/sdb model: Micron_1100_MTFD size: 512.1GB

$ sudo smartctl -t long /dev/sdb
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-65-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
**Please wait 6 minutes for test to complete.**
Test will complete after Fri Oct 11 14:57:48 2019

Use smartctl -X to abort test.
```

Anyways, figured it would be helpful to see the test output.

---

