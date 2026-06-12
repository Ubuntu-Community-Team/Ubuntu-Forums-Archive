---
title: "Harddisk failure"
date: 2011-12-18
forum: Hardware
---

### Post by jsra on 2011-12-18
Hi,

just encountered harddisk failure. Almost every command ends up with Input/output error. In syslog I found:

```
kernel: [9254886.566594] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
kernel: [9254886.566628] ata1.00: cmd ca/00:10:57:48:03/00:00:00:00:00/e0 tag 0 dma 8192 out
kernel: [9254886.566629]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
kernel: [9254886.566645] ata1.00: status: { DRDY }
kernel: [9254891.596281] ata1: port is slow to respond, please be patient (Status 0xd0)
kernel: [9254896.566134] ata1: device not ready (errno=-16), forcing hardreset
kernel: [9254896.566145] ata1: soft resetting link
kernel: [9254926.734549] ata1.00: qc timeout (cmd 0xec)
kernel: [9254926.734562] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
kernel: [9254926.734565] ata1.00: revalidation failed (errno=-5)
kernel: [9254926.734583] ata1: failed to recover some devices, retrying in 5 secs
kernel: [9254936.764050] ata1: port is slow to respond, please be patient (Status 0x80)
kernel: [9254941.733905] ata1: device not ready (errno=-16), forcing hardreset
kernel: [9254941.733915] ata1: soft resetting link
kernel: [9254971.902319] ata1.00: qc timeout (cmd 0xec)
kernel: [9254971.902331] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
kernel: [9254971.902335] ata1.00: revalidation failed (errno=-5)
kernel: [9254971.902353] ata1: failed to recover some devices, retrying in 5 secs
kernel: [9254981.931828] ata1: port is slow to respond, please be patient (Status 0x80)
kernel: [9254986.901667] ata1: device not ready (errno=-16), forcing hardreset
kernel: [9254986.901677] ata1: soft resetting link
kernel: [9255017.070086] ata1.00: qc timeout (cmd 0xec)
kernel: [9255017.070099] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
kernel: [9255017.070103] ata1.00: revalidation failed (errno=-5)
kernel: [9255017.070121] ata1.00: disabled
kernel: [9255022.608756] ata1: port is slow to respond, please be patient (Status 0x80)
kernel: [9255027.588585] ata1: device not ready (errno=-16), forcing hardreset
kernel: [9255027.588596] ata1: soft resetting link
kernel: [9255027.759615] ata1: EH complete
kernel: [9255027.759654] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
kernel: [9255027.759660] end_request: I/O error, dev sda, sector 215127
kernel: [9255027.759694] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
kernel: [9255027.759700] end_request: I/O error, dev sda, sector 17753111
kernel: [9255027.759705] Buffer I/O error on device sda1, logical block 2219131
kernel: [9255027.759724] lost page write due to I/O error on sda1
kernel: [9255027.759749] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
kernel: [9255027.759755] end_request: I/O error, dev sda, sector 17786055
kernel: [9255027.759759] Buffer I/O error on device sda1, logical block 2223249
kernel: [9255027.759773] lost page write due to I/O error on sda1

```

After this last line, the syslog ends. System is still running.

My question is what steps should I do now? I do have backups. Should I try to boot livecd and rescue the system? Or just reinstall system on new hdd and use backup files? Although hdd failed, system still manages to supply some services. I want to shorten the outage time as much as possible, thats why I'm asking for advices here.

Thanks for advices!

---

### Post by sudodus on 2011-12-18
Well, you have backups, and finally you have a reason to use them ;-)

I think it is almost certain, that you save time by reinstalling your system to a new drive compared to saving your failing system and repairing it.

But it depends on what and where the damage is. If there are many read/write errors, you will probably loose something important while saving the information using for example ddrescue. It takes time to repair it, and it is hard to estimate how long time. I'd say this method is for people without a recent backup. Or you could look for a particular file or group of files created after the last backup.

---

### Post by jsra on 2011-12-18
Ok, I will just reinstall the system and use my backups. There are some files that were not backuped yet, but I will try to get them from failed HDD later.
Thanks for advice.

---

### Post by 2F4U on 2011-12-18
Don't shutdown the machine. As long as it is running use the time to backup stuff you need. It is not certain that you will be able to start it again.

---

### Post by jsra on 2011-12-18
> **2F4U said:**
> Don't shutdown the machine. As long as it is running use the time to backup stuff you need. It is not certain that you will be able to start it again.

Thanks for your tip. I suggested it would not be able to bootup again. Unforutnately I'm unable to read anything out of that failed disk. Today I dont have enough time to install fresh system and get my backup going so I just let the system with failed disk running as it is.

---

