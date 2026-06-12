---
title: "OS stopped working: command not found?"
date: 2012-01-04
forum: Hardware
---

### Post by eckscalibur on 2012-01-04
The OS was acting strange, so I rebooted.  When I try to boot, it gives something like this:

command groups not found
command xconf not found
etc...

Any ideas?

EDIT:  Thought I would add a few more details:

GRUB seems to quickly flash an error message that says 'error: file not found' before going to the old interface (not the pretty purple one).

The boot process is giving errors something like 

" ... failed to start terminated with exit status ..."

and

"init: Faild to spawn acpid main process: unable to execute: No such file or directory".

No upgrades or modifications were made prior to this.

---

### Post by Buntumatic on 2012-01-04
Dying hard drive? I'd run smartctl from liveCD.

---

### Post by eckscalibur on 2012-01-04
The laptop is fairly new (<1 year), so I should think the hard drive isn't about to fail.

---

### Post by eckscalibur on 2012-01-04
Ran smartctl, got this:
```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
190 Airflow_Temperature_Cel 0x0022   054   040   045    Old_age   Always   In_the_past 46 (0 130 46 45)
```Still passed, but I'm not sure what the rest means.

EDIT:  Ran the self-test with no problems:
[CODE]=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3164         -[\CODE]

---

### Post by Buntumatic on 2012-01-05
What's the output of this?
```
smartctl --all /dev/sda | grep -e "Reallocated_Sector_Ct" -e "Current_Pending_Sector" -e "Offline_Uncorrectable" -e "UDMA_CRC_Error_Count" -e "Hardware_ECC_Recovered"
```

---

