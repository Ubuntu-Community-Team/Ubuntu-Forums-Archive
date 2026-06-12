---
title: "NVME keeps crashing and causing file system errors"
date: 2020-10-21
forum: Hardware
---

### Post by kuraiskrap on 2020-10-21
hey so i recently built a minecraft server, its running in the desktop enviroment due to issues getting ethernet working in terminal.

its been having a issue where when the NVME SSD is under load it can freeze up, and sometimes get file system issues, and everything gets set to read only, and we need to run FSCK manually at the server
we disabled some power saving settings, in the etc/default/grub file i added the lines pcie_aspm=off nvme_core.default_ps_max_latency_us=0

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off nvme_core.default_ps_max_latency_us=0"

this did stop the freezing, however it still seems to have the file system issue, it happened last night while i was asleep, and it happened during a backup while it was compressing the files today

our hardware is as follows

ryzen 3800x
[https://www.newegg.ca/amd-ryzen-7-3800x/p/N82E16819113104?Description=3800x&cm_re=3800x-_-19-113-104-_-Product](https://www.newegg.ca/amd-ryzen-7-3800x/p/N82E16819113104?Description=3800x&cm_re=3800x-_-19-113-104-_-Product)
XPG GAMMIX gaming SSD S11 Pro 2TB
[https://www.newegg.ca/xpg-gammix-2tb/p/0D9-00DF-00047](https://www.newegg.ca/xpg-gammix-2tb/p/0D9-00DF-00047)
B550-f strix wifi
[https://www.asus.com/ca-en/Motherboards/ROG-STRIX-B550-F-GAMING-WI-FI/](https://www.asus.com/ca-en/Motherboards/ROG-STRIX-B550-F-GAMING-WI-FI/)
F4-3600C16D32GVKC at 3200 due to not being supported
[https://www.newegg.ca/g-skill-32gb-288-pin-ddr4-sdram/p/N82E16820232907](https://www.newegg.ca/g-skill-32gb-288-pin-ddr4-sdram/p/N82E16820232907)


does anyone have any idea how we might be able to resolve this issue?

---

### Post by TheFu on 2020-10-21
Intel® I225-V 2.5Gb Ethernet is the issue.  [https://ubuntuforums.org/showthread.php?t=2445791](https://ubuntuforums.org/showthread.php?t=2445791)  Seems the intel drivers for it need more time to simmer. ;(

No clue about the SSD.  Besides saying to check the system logs.

---

### Post by oldfred on 2020-10-21
Have you updated UEFI?
And updated SSD to latest firmware?

---

### Post by kuraiskrap on 2020-10-21
so the BIOS/UEFI is up to date

the SSD firmware probably isnt up to date however, ordered it recently so idk how long it was sitting in a warehouse

---

### Post by oldfred on 2020-10-21
You can check firmware version - FW Rev:
[FONT=monospace][COLOR=#000000]sudo nvme list
or
[FONT=monospace][COLOR=#000000]udisksctl status[/COLOR]
[/FONT]

If not installed,
sudo apt install nvme-cli
[/COLOR]
[/FONT]

---

### Post by pqwoerituytrueiwoq on 2020-10-22
make sure the BCLK is set to 100 in the overclocking section, sometimes they try i make a small bump to that to make the system preform faster with a mild overclock to make a unskilled reviewer let there product look better in charts

---

### Post by kuraiskrap on 2020-10-22
Node             SN                   Model                                    N                                                                                                                                                             amespace Usage                      Format           FW Rev
---------------- -------------------- ---------------------------------------- -                                                                                                                                                             -------- -------------------------- ---------------- --------
/dev/nvme0n1     2K282LAA56KG         XPG GAMMIX S11 Pro                       1                                                                                                                                                                        1.81  TB /   2.05  TB    512   B +  0 B   42B7T1KA


so i guess the firmware is 42B7T1KA

but i dont see anywheres obvious on the website to see firmware updates/version
other then installing the toolbox in windows....

i can check the BCLK in the bios some morning when its quiet

---

### Post by kuraiskrap on 2020-10-23
BCLK is 100 in the bios, thats not the issue

---

### Post by pqwoerituytrueiwoq on 2020-10-24
Hve you checked the SMART data on the disk?
[FONT=courier new]sudo nvme smart-log /dev/nvme0[/FONT]

Have you tried logging the drive's temps to see if it is abnormally hot when the issue occurs?
The nvme drive i have run's silly hot without active cooling, with a GPU load i have had it hit 80C, in it's stock config it idles at 70C, i replaced the sticker heat sink with finned heat sync just on the controller with thermal adhesive and got the idle temps down 7-10C (my case is not silly hot, the drive just runs as hot as my CPUs load temps under prime95)

---

### Post by kuraiskrap on 2020-10-24
the motherboard has decently large NVME heatsinks/heatspreaders, its reporting 29c
theres not much heat in the system, and its got a decent amount of airflow, but heres my results

Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 29 C
available_spare                     : 100%
available_spare_threshold           : 10%
percentage_used                     : 0%
data_units_read                     : 19,195,797
data_units_written                  : 19,101,517
host_read_commands                  : 273,915,425
host_write_commands                 : 358,339,026
controller_busy_time                : 6,568
power_cycles                        : 38
power_on_hours                      : 1,205
unsafe_shutdowns                    : 14
media_errors                        : 0
num_err_log_entries                 : 0
Warning Temperature Time            : 16
Critical Composite Temperature Time : 0
Thermal Management T1 Trans Count   : 27
Thermal Management T2 Trans Count   : 21
Thermal Management T1 Total Time    : 1230
Thermal Management T2 Total Time    : 272

---

### Post by pqwoerituytrueiwoq on 2020-10-25
over cooling the flash nand on a ssd is bad, they need to be warm, the controllers like being cold

---

