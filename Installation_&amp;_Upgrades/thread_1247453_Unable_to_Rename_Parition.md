---
title: "Unable to Rename Parition"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by xcusmwah on 2009-08-22
I have a hard drive which is currently named "MMA" Wrestling" Boxing" which I want named "MP3s".  I have done everything to try and rename it but have been unsuccessful.  I am able to write to the partitions just fine but cannot rename them.  When running gParted I am seeing an error (see screenshot) which may be causing the problem.  Any advice would be much appreciated.  Thank you

---

### Post by raymondh on 2009-08-23
> **xcusmwah said:**
> I have a hard drive which is currently named "MMA" Wrestling" Boxing" which I want named "MP3s".  I have done everything to try and rename it but have been unsuccessful.  I am able to write to the partitions just fine but cannot rename them.  When running gParted I am seeing an error (see screenshot) which may be causing the problem.  Any advice would be much appreciated.  Thank you

Gparted will not write/touch any partition that is mounted.  Are you using a liveCD?  If so, try to right clk on the partition (extended and then the logicals) and see if you have the option to unmount.  For swap, select swapoff.

---

### Post by drs305 on 2009-08-23
Depending on the gparted version, you may also need to install *ntfsprogs* to be able to label an NTFS partition via gparted. You can check to see if gparted has ntfs labelling capabilities by clicking on View, Filesystem Support and looking at the NTFS row. If there are no checks, install ntfsprogs and reopen gparted.

Or, install ntfsprogs and label it via the command line:
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ntfsprogs
sudo umount <device>
sudo ntfslabel <device> <label>

```
Example:
sudo umount /dev/sda5
sudo ntfslabel /dev/sda5 data

---

