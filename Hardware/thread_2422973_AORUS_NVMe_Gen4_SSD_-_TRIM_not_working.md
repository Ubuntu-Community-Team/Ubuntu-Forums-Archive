---
title: "AORUS NVMe Gen4 SSD - TRIM not working"
date: 2019-07-15
forum: Hardware
---

### Post by backspin on 2019-07-15
I just assembled a X570 board with a **AORUS NVMe Gen4 SSD NVME 1TB**, and I went to set up a weekly TRIM cron, and fstrim fails. I do a lot of compiling which requires a lot of writing and deleting, so it is going to be important to trim the drive on a regular basis.
According to Gigabyte - "TRIM & S.M.A.R.T supported".   

*EDIT* I realize Ubuntu 18.04 runs a weekly job to TRIM, but it just uses fstrim which does not work. 

What I've done so far.

$ sudo fstrim -a -v
[B]fstrim: /boot/efi: FITRIM ioctl failed: Input/output error

[/B]Checking it out with hdparm
$ sudo hdparm -I /dev/nvme0n1p2 | grep TRIM
** HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device**

dmsg print
[B][11786.271949] print_req_error: I/O error, dev nvme0n1, sector 1144536 flags 803

[/B]It just appears nvme is treated differently than SSD, but I'm not sure what commands need to be run. [B]Any thoughts on where to go next?
[/B]
Thanks,

David

*Edit*  I am running a newer kernel.
[B]Ryzen-3900x:~/Desktop$ uname -a
Linux Ryzen-3900x 5.1.16-050116-generic #201907031232 SMP Wed Jul 3 12:35:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux[/B]

---

### Post by backspin on 2019-07-15
More information

**sudo nvme list**
Node.............                       SN                   Model                                    ................Namespace ..............Usage                      .............Format           ........FW ..........Rev  
----------------     -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     SNXXXXXX       GIGABYTE GP-ASM2NE6100TTTD               1           1.00  TB /   1.00  TB    512   B +  0 B   EGFM11.0


**sudo nvme smart-log /dev/nvme0n1**

Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 41 C
available_spare                     : 100%
available_spare_threshold           : 5%
percentage_used                     : 0%
data_units_read                     : 37,319
data_units_written                  : 241,653
host_read_commands                  : 1,072,833
host_write_commands                 : 1,150,325
controller_busy_time                : 2
power_cycles                        : 3
power_on_hours                      : 5
unsafe_shutdowns                    : 2
media_errors                        : 0
num_err_log_entries                 : 72
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0

---

### Post by oldfred on 2019-07-15
Does this apply?
       AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2) 
    
And those fixes are from AMD, so may be a bit before Motherboard vendor has it available.

Have you updated firmware on SSD?

---

### Post by Dennis N on 2019-07-16
systemd will take care of trim. Trim works on my Western Digital NVMe SSD, so at least for this drive, NVMe is not treated differently. System is Ubuntu 18.04

You have to enable* trim before it will work:
```
systemctl enable fstrim.timer
```
then reboot, and it should begin monitoring.

The timer triggers fsck at 00:00 Monday or it occurs first login after that time, then resets to next Monday.

Check status:
```
dmn@Tyana:~$ systemctl status fstrim.timer
&#9679; fstrim.timer - Discard unused blocks once a week
   Loaded: loaded (/lib/systemd/system/fstrim.timer; enabled; vendor preset: enabled)
   Active: active (waiting) since Fri 2019-07-12 12:42:36 MST; 39min ago
  Trigger: Mon 2019-07-15 00:00:00 MST; 2 days left
     Docs: man:fstrim

```
You can check if its working from examining journalctl:
```
dmn@Tyana:~$ journalctl | grep fstrim | grep Jul
Jul 01 12:33:47 Tyana fstrim[1217]: /: 5.9 GiB (6330462208 bytes) trimmed
Jul 08 00:20:42 Tyana fstrim[1237]: /: 6 GiB (6420729856 bytes) trimmed

```

* it may already be enabled by default in Ubuntu. In other distros, it isn't.

---

### Post by backspin on 2019-07-16
@[[IMG]https://ubuntuforums.org/customavatars/avatar321222_2.gif[/IMG]]("https://ubuntuforums.org/member.php?u=321222")[COLOR=#000000][[COLOR=#000000]Dennis N[/COLOR]]("https://ubuntuforums.org/member.php?u=321222")

[/COLOR]


Thanks --  Yes, I looked into the systmctl weekly job and it is enabled, but I don't believe it is going to work.  The reason is when I looked into the command it runs; it runs fstrim, and I've run that manually many times and it fails.  So, I don't believe it is going to successfully TRIM.  

I really appreciate the insight, but am thinking it might be related to the fstrim utility not knowing how to interact with the nvme.

---

### Post by backspin on 2019-07-19
Adding additional dmesg information from the Ubuntu's automated fstrim attempt.

[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] print_req_error: I/O error, dev nvme0n1, sector 4160 flags 803
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] amd_iommu_report_page_fault: 28 callbacks suppressed
[Fri Jul 19 17:05:08 2019] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:08 2019] print_req_error: I/O error, dev nvme0n1, sector 1141976 flags 803
[Fri Jul 19 17:05:59 2019] amd_iommu_report_page_fault: 2 callbacks suppressed
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] print_req_error: I/O error, dev nvme0n1, sector 4160 flags 803
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] nvme 0000:01:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] AMD-Vi: Event logged [IO_PAGE_FAULT device=01:00.0 domain=0x0000 address=0x0 flags=0x0000]
[Fri Jul 19 17:05:59 2019] print_req_error: I/O error, dev nvme0n1, sector 1141976 flags 803

---

### Post by oldfred on 2019-07-19
Have you checked to see if there is a firmware update for your SSD?
Many have needed firmware updates, even if new.

---

### Post by backspin on 2019-07-20
> **oldfred said:**
> Have you checked to see if there is a firmware update for your SSD?
Many have needed firmware updates, even if new.

I'll be checking for firmware updates today.

---

### Post by rbmorse on 2019-07-20
I just ran fstrim manually on my Samsung 970 Pro NVMe device on my ASUS Crosshair VIII (one of the few things that actually works at the moment on the x570 motherboard), so I don't think there is an intrinsic problem with fstrim and NVMe devices.

---

### Post by backspin on 2019-07-20
> **rbmorse said:**
> I just ran fstrim manually on my Samsung 970 Pro NVMe device on my ASUS Crosshair VIII (one of the few things that actually works at the moment on the x570 motherboard), so I don't think there is an intrinsic problem with fstrim and NVMe devices.


Thanks for checking... Others seem to be working fine with NVMe, so I figure it probably has something to do with interfacing with Gigabytes new PCI Gen4 NVMe.  Looks like it is on the latest firmware, though it is likely the first version. I've tried running fstrim with several kernel versions and all fail with the same result.

davidc502@Ryzen-3900x:~$ **sudo nvme fw-log /dev/nvme0n1**
Firmware Log for device:nvme0n1
afi  : 0x1
frs1 : 0x302e31314d464745 (**EGFM11.0**)

Here is another way to get the firmware version. In **BOLD**

davidc502@Ryzen-3900x:~$ sudo nvme list /dev/nvme0n1
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     SN1xxxxxxxx       GIGABYTE GP-ASM2NE6100TTTD               1           1.00  TB /   1.00  TB    512   B +  0 B   **EGFM11.0**

---

### Post by QIII on 2019-07-20
Are you running this command from within a virtual machine?

---

### Post by Dennis N on 2019-07-20
FYI,
Phoronix benchmarked a PCIe 4.0 SSD on Ubuntu, so the NVMe driver does work - at least with the tested drive.
[https://www.phoronix.com/scan.php?page=article&item=corsair-force-mp600&num=1](https://www.phoronix.com/scan.php?page=article&item=corsair-force-mp600&num=1)

Note: The testing used the 5.2 kernel, so that might be what's needed.

---

### Post by backspin on 2019-07-23
Ongoing saga for fstrim.   I Turned on kernel tracing  for the nvme as per instructions from someone willing to help out.  Unfortunately, the person helping doesn't know enough about error to  help further, but are trying to enlist others to  help.

Could  you collect logs via the following steps?

```


Suppose your nvme disk name is /dev/nvme0n1:

1) queue limits log:

    #(cd /sys/block/nvme0n1/queue && find . -type f -exec grep -aH . {} \;)


2) NVMe IO trace

- enable nvme IO trace before running fstrim:

    #echo 1  > /sys/kernel/debug/tracing/events/nvme_setup_cmd/enable
    #echo 1  > /sys/kernel/debug/tracing/events/nvme_complete_rq/enable

- run fstrim

- after the fstrim failure is triggered, disable the nvme io trace & post the log:

    #echo 0  > /sys/kernel/debug/tracing/events/nvme_setup_cmd/enable
    #echo 0  > /sys/kernel/debug/tracing/events/nvme_complete_rq/enable

    #cp    /sys/kernel/debug/tracing/trace /root/nvme_io_trace.log

```



thanks,
Ming


Hello Ming

Thank you for the quick reply   See attached
From the IO trace, discard command(nvme_cmd_dsm) is failed:

  From the IO trace, discard command(nvme_cmd_dsm) is failed:

  kworker/15:1H-462   [015] .... 91814.342452: nvme_setup_cmd: nvme0: disk=nvme0n1, qid=7, cmdid=552, nsid=1, flags=0x0, meta=0x0, cmd=(nvme_cmd_dsm nr=0, attributes=4)
          <idle>-0     [013] d.h. 91814.342708: nvme_complete_rq: nvme0: disk=nvme0n1, qid=7, cmdid=552, res=0, retries=0, flags=0x0, status=8198

And the returned error code is 0x8198, I am not sure how to parse the
'Command Specific Status Values' of 0x98, maybe Christoph, Keith or our other
NVMe guys can help to understand the failure.


Thanks,
Ming

---

### Post by backspin on 2019-07-23
> **QIII said:**
> Are you running this command from within a virtual machine?


Negative.. Only Ubuntu is on the drive.

---

### Post by backspin on 2019-07-23
> **Dennis N said:**
> FYI,
Phoronix benchmarked a PCIe 4.0 SSD on Ubuntu, so the NVMe driver does work - at least with the tested drive.
[https://www.phoronix.com/scan.php?page=article&item=corsair-force-mp600&num=1](https://www.phoronix.com/scan.php?page=article&item=corsair-force-mp600&num=1)

Note: The testing used the 5.2 kernel, so that might be what's needed.

I would like to add your information to the people trying to help, but before I do I have some questions.

Are you saying you have tried fstrim on this PCIe 4.0 SSD, and is not working?

Thanks,

David

---

### Post by Dennis N on 2019-07-23
Phoronix didn't test trim - it's just performance benchmarking. My suggestion in the note is that a newer kernel is often needed to support all features of newest hardware. For that Corsair drive and yours, the vendor information I saw is that the drive supports trim. But maybe you need the latest kernel to make trim work.

---

### Post by backspin on 2019-07-23
> **Dennis N said:**
> Phoronix didn't test trim - it's just performance benchmarking. My suggestion in the note is that a newer kernel is often needed to support all features of newest hardware. For that Corsair drive and yours, the vendor information I saw is that the drive supports trim. But maybe you need the latest kernel to make trim work.

I've tried 3 different kernels including 5.2 rc7.

---

### Post by Dennis N on 2019-07-23
> **backspin said:**
> I've tried 3 different kernels including 5.2 rc7.
Well, I guess you've eliminated that cause. Two obvious possibilities come to mind - the fstrim utility needs updating to handle PCIe 4.0 drives, or it's the drive itself.

---

### Post by backspin on 2019-07-23
> **Dennis N said:**
>  Two obvious possibilities come to mind - the fstrim utility needs updating to handle PCIe 4.0 drives, or it's the drive itself.

That's the 10k question at this point.  I've opened a case with Gigabyte asking if there are any firmware updates, but will take 3-5 days to get back with me.  I was hoping to see more people with PCIe 4.0 drives with issues so we could press this issue more, but appears this is bleeding edge for Ubuntu and the trim utility. I think another issue is I went off the beaten path by going with a Gigabyte SSD which is actually made by Phision, so this may be a while before it gets enough recognition to be fixed.

---

### Post by Dennis N on 2019-07-23
Are you using an m.2 drive with adapter? If you have an unused PCIe 3 slot, you could move the adapter and drive to that and see if trim works with drive operating at PCIe 3 speed. These devices are supposed to be backward compatible.

---

### Post by backspin on 2019-07-24
> **Dennis N said:**
> Are you using an m.2 drive with adapter? If you have an unused PCIe 3 slot, you could move the adapter and drive to that and see if trim works with drive operating at PCIe 3 speed. These devices are supposed to be backward compatible.

There is a code being returned from the NVMe that is out of specification.  This is what I'm being told from the experts who work with fstrim and NVMe's.

---

### Post by backspin on 2019-08-01
At this point I've contacted Phison, and am waiting to hear back.  Phison controllers are in the new NVMe's running PCIe 4.0 like the ones from Gigabyte and Corsair.

---

### Post by Sigster on 2019-10-04
I just saw that I have the same error messages when trying to fstrim
B350 chipset/Ryzen R5 1600/Sabrent Rocket PCIe3 NVMe with Phison E12 controller

Stumbled upon this:
[https://bugzilla.kernel.org/show_bug.cgi?id=202665](https://bugzilla.kernel.org/show_bug.cgi?id=202665)
NVMe AMD-Vi IO_PAGE_FAULT only with hardware IOMMU and fstrim/discard

Not fixed as of today, but there are some workarounds.

---

### Post by backspin on 2020-01-17
I would like to report it is happily working now on Latest kernel 5.4.13  -   Linux Ryzen-3900x 5.4.13-050413-generic #202001171431 SMP Fri Jan 17 19:34:58 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

I have no idea who worked on it, but would like to say thanks --  

davidc502@Ryzen-3900x:~$ sudo fstrim -a -v
/media/davidc502/8d08f08b-7d9a-4170-8ca6-172a5c37d19f: 832.9 GiB (894319067136 bytes) **trimmed**
/boot/efi: 504.9 MiB (529424384 bytes) **trimmed**
/: 876.2 MiB (918781952 bytes) **trimmed**

*edit*
Not sure how to mark this thread as solved.

*Edit*  Now marked as solved.

---

