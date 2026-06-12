---
title: "server freezes, trace output: mem_cgroup_move_lists etc"
date: 2009-07-27
forum: Hardware
---

### Post by Creap on 2009-07-27
I have a newly built server with the following hardware:

[LIST]
[*]Asus P5Q-E
[*]Intel Core 2 Duo E8400
[*]Thermalright Ultra-120 Extreme 775
[*]Corsair XMS2 Dominator TwinX DDR2 PC8500/1066MHz CL5 2x2GB
[*]Samsung EcoGreen F2 HD103SI 32MB 1TB	
[/LIST]

A couple of days ago it went down, didn't answer pings, so I rebooted it. Still nothing, so I connected a monitor and got **"CRC error - system halted"** when I rebooted. 

I ran memtest, and got some errors, so I figured it was the RAM. I then removed one of my RAM modules and ran memtest, with no errors. I switched RAMs, and got no errors on the other one either. Then I put them both in, ran memtest, and this time got no errors! I ran memtest until it told me "check complete, no errors found". 

When I booted normally, it worked again. After 24 hours though, it didn't answer on ping again, so I checked what was up. The screen had the following:

```

a00
[44418.714906] Call Trace:
[44418.714913]  [<ffffffffff802bac04>] activate_page-0x154/0x170
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] mark_page_accessed-0x5b/0x70
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] __find_get_block-xxxxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] __getblk-xxxxxxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] journal_get_descriptor_buffer-xxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] journal_write_commit_record-xxxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] ? __journal_remove_journal_head-xxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] journal_commit_transaction-xxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] ? try_to_del_timer_synx-xxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] kjournald-xxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] ? autoremove_wake_function-xxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] ? kjournald-xxxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] kthread-xxxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] child_rip-xxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] ? kthread-xxxx
[xxxxx.xxxxxx]  [<xxxxxxxxxxxxxxxxxx>] ? child_rip-xxx
[xxxxx.xxxxxx] Code: 19 c0 85 c0 75 d5 .... etc
[xxxxx.xxxxxx] RIP  [<xxxxxxxxxxxxxxxxxx>] mem_cgroup_move_lists-xxxxxx
[xxxxx.xxxxxx]  RSP <xxxxxxxxxxxxxxxxxx>
[xxxxx.xxxxxx] ---[ end trace 2a7d715a5fd041a0 ]---

```

I didn't feel like writing down all the numbers, so I replaced them with x's. 

Does anyone have any idea what this is? How can I troubleshoot? What is most likely to have broken?

Thanks.

---

