---
title: "System frequently hangs and lagging response"
date: 2014-07-05
forum: Hardware
---

### Post by subhojit on 2014-07-05
I am using Ubuntu 14.04. Did the upgrade few months ago. My system was working normally until yesterday it started lagging. The system frequently hangs for 30 seconds (approx or more than that), and there is lagging response as I type. Other than that system is working normal.


I googled for this and found this answer: [http://askubuntu.com/a/21643/55026](http://askubuntu.com/a/21643/55026). Third point helped me and I am getting these messages from [B]kern.log

[/B][INDENT]Jul  4 16:11:40 moony kernel: [24200.058787] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen[/INDENT]
[INDENT]Jul  4 16:11:40 moony kernel: [24200.058792] ata1.00: failed command: FLUSH CACHE EXT[/INDENT]
[INDENT]Jul  4 16:11:40 moony kernel: [24200.058796] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0[/INDENT]
[INDENT]Jul  4 16:11:40 moony kernel: [24200.058796]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)[/INDENT]
[INDENT]Jul  4 16:11:40 moony kernel: [24200.058797] ata1.00: status: { DRDY }[/INDENT]
[INDENT]Jul  4 16:11:40 moony kernel: [24200.058801] ata1: hard resetting link[/INDENT]
[INDENT]Jul  4 16:11:45 moony kernel: [24205.432930] ata1: link is slow to respond, please be patient (ready=0)[/INDENT]
[INDENT]Jul  4 16:11:45 moony kernel: [24205.488995] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/INDENT]
[INDENT]Jul  4 16:11:45 moony kernel: [24205.490405] ata1.00: configured for UDMA/100[/INDENT]
[INDENT]Jul  4 16:11:45 moony kernel: [24205.490412] ata1.00: retrying FLUSH 0xea Emask 0x4[/INDENT]
[INDENT]Jul  4 16:11:45 moony kernel: [24205.504962] ata1.00: device reported invalid CHS sector 0[/INDENT]
[INDENT]Jul  4 16:11:45 moony kernel: [24205.504981] ata1: EH complete
[/INDENT]


**System details:**[INDENT]
HDD - 500GB TOSHIBA MK5076GS[/INDENT]
[INDENT]RAM - 4GB DDR3 in two slots[/INDENT]
[INDENT]CPU - Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz[/INDENT]
[INDENT]Display - 3rd Gen Core processor Graphics Controller[/INDENT]
[INDENT]Laptop - HP 2116TU[/INDENT]

I have googled the error messages and they say that it might be some hard disk problem.

[B]UPDATE
[/B]I am also getting these messages in [B]kern.log

[/B][INDENT]Jul  5 14:55:31 moony kernel: [17540.897575] Call Trace:[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897577]  [<ffffffff8171e749>] schedule+0x29/0x70[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897579]  [<ffffffff8128bea5>] jbd2_log_wait_commit+0x95/0x100[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897581]  [<ffffffff810aaea0>] ? prepare_to_wait_event+0x100/0x100[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897583]  [<ffffffff8128e473>] jbd2_complete_transaction+0x53/0xa0[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897585]  [<ffffffff8123a112>] ext4_sync_file+0x292/0x320[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897587]  [<ffffffff811ec4f1>] do_fsync+0x51/0x80[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897589]  [<ffffffff811ec780>] SyS_fsync+0x10/0x20[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897591]  [<ffffffff8172aeff>] tracesys+0xe1/0xe6[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897592] INFO: task bounce:10099 blocked for more than 120 seconds.[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897593]       Tainted: GF        C O 3.13.0-30-generic #54-Ubuntu[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897594] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897595] bounce          D ffff88014f254440     0 10099   2061 0x00000000[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897596]  ffff8800100b9e50 0000000000000002 ffff880107092fe0 ffff8800100b9fd8[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897598]  0000000000014440 0000000000014440 ffff880107092fe0 ffff880148887000[/INDENT]
[INDENT]Jul  5 14:55:31 moony kernel: [17540.897600]  000000000125d4ab ffff880148887088 ffff880148887024 ffff8800100b9e90[/INDENT]


P.S. System used to hang while copying large file (movies, etc.) to system. But I used to ignore them.

Please HELP ](*,)

---

### Post by TheFu on 2014-07-05
Yep. Something is failing.  Backup, backup, backup.  Hopefully it isn't too late.
Check
* HDD controller
* cables
* HDDs

Hopefully, it is just a loose cable.  Are any USB drives connected? I've had the most trouble with those. Disconnect, see if that helps.  Also try different ports, different cables.

BTW, systems shouldn't "hang", even when copying large files.

Did I mention - backups?  Hopefully it isn't too late.

---

### Post by subhojit on 2014-07-05
Thank you for the response. Yes I have taken all backups. WIll check for any loose cables. No there were not any USB drives connected.

---

