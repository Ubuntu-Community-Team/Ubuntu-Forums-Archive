---
title: "Accepted method of troubleshooting Machine Check exceptions (MCEs)?"
date: 2023-06-12
forum: Hardware
---

### Post by r-karl on 2023-06-12
Hello folks, 

What is the current accepted method of troubleshooting mce's? Every so often I see mce's in dmesg output (maybe 1x per day). Yet finding exactly what the problem is has become difficult since the accepted tool doesn't appear to be doing its job. Based on everything i've read, `mcelog` has been deprecated in Debian, so more current versions of ubuntu no longer include it in its repositories (23.04 is the version i'm running in this case). Some posts have stated that this functionality has been replaced with `rasdaemon`, so I've installed that. However, despite the fact that it's installed, it is not telling me anything about these mce's: 

```
[COLOR=#000000][FONT=Menlo][COLOR=#39C026][Mon Jun 12 04:19:12 2023] [/COLOR][COLOR=#AAAB25]mce: [/COLOR][Hardware Error]: Machine check events logged[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#39C026][Mon Jun 12 04:19:12 2023] [/COLOR][COLOR=#AAAB25]mce: [/COLOR][Hardware Error]: Machine check events logged[/FONT][/COLOR]
[COLOR=#5E221C][FONT=Menlo][COLOR=#39C026][Mon Jun 12 04:20:07 2023] [/COLOR][COLOR=#AAAB25]PMS BTQ[1971934]: [/COLOR]segfault at 7fc2f24b4a65 ip 00007fc6281bb958 sp 00007fc5cce422c8 error 4 in ld-musl-x86_64.so.1[7fc6281aa000+53000] likely on CPU 15 (core 28, socket 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#39C026][Mon Jun 12 04:20:07 2023] [/COLOR][COLOR=#AAAB25]Code: [/COLOR]05 0d 6d fe ff 45 0f b7 04 00 49 c1 e0 04 4d 89 c3 49 29 d3 49 83 c3 fc 4c 8b 4f 10 48 63 c6 49 0f af c0 49 01 c1 49 83 c1 10 <41> 80 79 fd 00 74 07 41 0f b7 49 fe ff c1 4d 89 da 49 c1 ea 04 0f[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#39C026][Mon Jun 12 06:48:21 2023] [/COLOR][COLOR=#AAAB25]systemd-journald[1267]: [/COLOR]Data hash table of /var/log/journal/310ca2c4936440a881b2d4e317211a9f/system.journal has a fill level at 75.0 (174764 of 233016 items, 125829120 file size, 719 bytes per hash table item), suggesting rotation.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#39C026][Mon Jun 12 06:48:21 2023] [/COLOR][COLOR=#AAAB25]systemd-journald[1267]: [/COLOR]/var/log/journal/310ca2c4936440a881b2d4e317211a9f/system.journal: Journal header limits reached or header out-of-date, rotating.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]root@lateralus:/pool1/work# ras-mc-ctl --errors[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]No Memory errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]No PCIe AER errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]No Extlog errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]No MCE errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]

```

I've also found the sqlite db and see that it's not been written to since May 29, which was when I installed it. 

```
[COLOR=#000000][FONT=Menlo]root@lateralus:/var/lib/rasdaemon# ls -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]total 20[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-rw-r--r-- 1 root root 20480 May 29 15:12 ras-mc_event.db[/FONT][/COLOR]

```

So what's the deal? How are people troubleshooting mce's now? Is there an accepted way? Thanks in advance for any help.

---

### Post by Doug S on 2023-06-14
MCE errors are difficult to impossible to debug and isolate. I haven't ever been able to get the "tools" to work to help. Make sure your BIOS is up to date. I have made some progress in the past by increasing timing margins via slightly reducing the maximum CPU frequency permitted to be used. I have also made progress by picking away at things in an attempt to increase (yes, increase) the frequency of occurrence of the MCE error, in an attempt to reduce the testing time to obtain statistics (i.e. is it better or worse or the same?).  However, I have a dedicated test server, whereas often users don't and can not dedicate the computer time. I also will try the most recent [Ubuntu mainline kernel]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") in an attempt to determine if the cause of the error might have already been fixed upstream.

EDIT (not really relevant): I checked if I could still create the MCE I was trying to figure out back in March. I can.
Performance CPU frequency scaling governor; intel_pstate CPU frequency scaling driver; HWP (HardWare Pstates) enabled; Kern 6.4-rc6, 1000Hz tick rate (Low latency); Force 49% idle injection; do prime95 - Torture Test - Test 2, Small FFTs (tests L1/L2/L3 caches, maximum power/heat/CPU stress). Typically MCE occurs within a couple of hours.

The potentially relevant thing about this edit is that this particular MCE freezes the system. As far as I have been able to determine (I would well be wrong), the processor halts, so it would be difficult to acquire more information.

---

### Post by Doug S on 2023-06-20
I started to look again into the cause of the MCE I have been seeing, as sometimes the report of an MCE does not result in system freeze. I remain unable to get rasdaemon to report things properly, and I also tried running it foreground mode. I have not tried to figure out how to manually run the trace events, but that is the only thing I can think if to attempt to get more information.

---

### Post by #&amp;thj^% on 2023-06-20
> **Doug S said:**
> I have not tried to figure out how to manually run the trace events, but that is the only thing I can think if to attempt to get more information.

My effort to help:
EDIT: Some more info on usage, but Doug S knows this already.
 Check Exceptions are hardware failure events and can be logged with rasdaemon.service to journalctl. On Ubuntu, you can install via:

```
sudo apt install rasdaemon
```

verify rasdaemon is active:

```
systemctl status rasdaemon
```

Then after the system has crashed **or been used for a while **take a look at the log:

```
sudo journalctl -f -u rasdaemon
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording aer_event events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: read
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording mce_record events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording mce_record events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording extlog_event events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording aer_event events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording extlog_event events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording mce_record events
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: read
Jun 20 12:52:32 kaisenlinux rasdaemon[9437]: rasdaemon: Recording mce_record events



```

---

### Post by Doug S on 2023-06-20
Thanks for chiming in 1fallen, your posting was useful.

I have been getting this:

```
Jun 20 13:47:00 s19 rasdaemon[788]: Huh! something got wrong. Aborting.
```

I think, but am not sure, it is because of troubles communicating with sqlite, which I don't think is even running. That is the reason I tried to kill the service and just run it in the foreground not logging to the db.

To attempt to correlate with known non-crashing MCE's listed in kernel.log and to provide a bigger context:

```
...
Jun 19 16:53:04 s19 kernel: [32414.739518] EXT4-fs (sdc): mounted filesystem 59c0a6e1-0f3b-4357-a667-18881f067ba1 r/w with ordered data mode. Quota mode: none.
Jun 19 16:57:07 s19 kernel: [32658.103858] intel_powerclamp: Stop forced idle injection
Jun 20 09:14:13 s19 kernel: [91284.411543] mce: [Hardware Error]: Machine check events logged
Jun 20 09:17:33 s19 kernel: [91484.981461] mce: [Hardware Error]: Machine check events logged
Jun 20 09:22:21 s19 kernel: [91772.666420] mce: [Hardware Error]: Machine check events logged
Jun 20 09:24:45 s19 kernel: [91916.944706] show_signal: 7 callbacks suppressed
Jun 20 09:24:45 s19 kernel: [91916.944709] traps: genksyms[304534] general protection fault ip:7ffc42548ad0 sp:fffffe21 error:28
Jun 20 09:54:13 s19 kernel: [93685.204922] mce: [Hardware Error]: Machine check events logged
Jun 20 09:55:41 s19 kernel: [93772.707323] mce: [Hardware Error]: Machine check events logged
Jun 20 09:56:41 s19 kernel: [93833.213045] perf: interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 79000
Jun 20 10:00:03 s19 kernel: [94034.847526] mce: [Hardware Error]: Machine check events logged
Jun 20 10:02:42 s19 kernel: [94193.433666] BUG: unable to handle page fault for address: 0000000003836e98
Jun 20 10:02:42 s19 kernel: [94193.433725] #PF: supervisor write access in user mode
Jun 20 10:02:42 s19 kernel: [94193.433782] #PF: error_code(0x10202) - not-present page
...
```

```
sudo journalctl -u rasdaemon
...
Jun 19 16:06:36 s19 rasdaemon[849]: Enabled event mce:mce_record
Jun 19 16:06:36 s19 rasdaemon[849]: ras:extlog_mem_event event enabled
Jun 19 16:06:36 s19 rasdaemon[849]: Enabled event ras:extlog_mem_event
Jun 19 16:06:36 s19 systemd[1]: Started RAS daemon to log the RAS events.
Jun 19 16:06:36 s19 rasdaemon[849]: rasdaemon: Recording mc_event events
Jun 19 16:06:36 s19 rasdaemon[849]: rasdaemon: Recording aer_event events
Jun 19 16:06:36 s19 rasdaemon[849]: rasdaemon: Recording extlog_event events
Jun 19 16:06:36 s19 rasdaemon[849]: rasdaemon: Recording mce_record events
Jun 19 16:06:36 s19 rasdaemon[849]: rasdaemon: Recording arm_event events
Jun 20 10:27:40 s19 systemd[1]: Stopping RAS daemon to log the RAS events...
Jun 20 10:27:40 s19 rasdaemon[653827]: ras:mc_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: rasdaemon: ras:mc_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: rasdaemon: ras:aer_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: ras:aer_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: rasdaemon: mce:mce_record event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: rasdaemon: ras:extlog_mem_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: mce:mce_record event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: ras:extlog_mem_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: ras:arm_event event disabled
Jun 20 10:27:40 s19 rasdaemon[653827]: rasdaemon: ras:arm_event event disabled
Jun 20 10:27:40 s19 rasdaemon[849]: rasdaemon: Recevied signal=15
Jun 20 10:27:40 s19 rasdaemon[849]: overriding event (1486) ras:mc_event with new print handler
Jun 20 10:27:40 s19 rasdaemon[849]: overriding event (1483) ras:aer_event with new print handler
Jun 20 10:27:40 s19 rasdaemon[849]: overriding event (1485) ras:arm_event with new print handler
Jun 20 10:27:40 s19 rasdaemon[849]: overriding event (113) mce:mce_record with new print handler
Jun 20 10:27:40 s19 rasdaemon[849]: overriding event (1487) ras:extlog_mem_event with new print handler
Jun 20 10:27:40 s19 rasdaemon[849]: Calling ras_mc_event_opendb()
Jun 20 10:27:40 s19 rasdaemon[849]: Calling ras_mc_event_closedb()
Jun 20 10:27:40 s19 rasdaemon[849]: [COLOR="#FF0000"]Huh! something got wrong. Aborting.[/COLOR]
Jun 20 10:27:40 s19 systemd[1]: rasdaemon.service: Succeeded.
Jun 20 10:27:40 s19 systemd[1]: Stopped RAS daemon to log the RAS events.
-- Reboot --
...
```

EDIT: I think what I want is not this:

```
doug@s19:~$ systemctl status rasdaemon
&#9679; rasdaemon.service - RAS daemon to log the RAS events
     Loaded: loaded (/lib/systemd/system/rasdaemon.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-06-20 13:47:22 PDT; 1h 24min ago
    Process: 787 ExecStartPost=/usr/sbin/rasdaemon --enable (code=exited, status=0/SUCCESS)
   Main PID: 785 (rasdaemon)
      Tasks: 1 (limit: 38159)
     Memory: 14.6M
     CGroup: /system.slice/rasdaemon.service
             &#9492;&#9472;785 [COLOR="#FF0000"]/usr/sbin/rasdaemon -f -r[/COLOR]

Jun 20 13:47:22 s19 rasdaemon[785]: mce:mce_record event enabled
Jun 20 13:47:22 s19 rasdaemon[785]: Enabled event mce:mce_record
Jun 20 13:47:22 s19 rasdaemon[785]: ras:extlog_mem_event event enabled
Jun 20 13:47:22 s19 rasdaemon[785]: Enabled event ras:extlog_mem_event
Jun 20 13:47:22 s19 systemd[1]: Started RAS daemon to log the RAS events.
Jun 20 13:47:22 s19 rasdaemon[785]: rasdaemon: Recording mc_event events
Jun 20 13:47:22 s19 rasdaemon[785]: rasdaemon: Recording aer_event events
Jun 20 13:47:22 s19 rasdaemon[785]: rasdaemon: Recording extlog_event events
Jun 20 13:47:22 s19 rasdaemon[785]: rasdaemon: Recording mce_record events
Jun 20 13:47:22 s19 rasdaemon[785]: rasdaemon: Recording arm_event events
doug@s19:~$
```

But rather this:
```
&#9492;&#9472;785 [COLOR="#FF0000"]/usr/sbin/rasdaemon -f[/COLOR]
```

---

### Post by #&amp;thj^% on 2023-06-20
Nicely Done Doug S ;)
I seen those as well, I'm going to check old notes i have.
If I find anything relevant I'll post back.

---

### Post by Doug S on 2023-06-20
Thanks,

I am now running this:

```
doug@s19:~/config/lib/systemd/system$ diff rasdaemon.service.original rasdaemon.service
6c6
< ExecStart=/usr/sbin/rasdaemon -f -r
---
> ExecStart=/usr/sbin/rasdaemon -f
doug@s19:~/config/lib/systemd/system$
```

And will also report back later.

---

### Post by Doug S on 2023-06-20
I got a few MCE errors that did not result in a crash:

```
...
Jun 20 16:47:06 s19 kernel: [  112.916919] intel_powerclamp: Start idle injection to reduce power
Jun 20 16:47:18 s19 kernel: [  124.952739] process 'home/doug/prime95/mprime' started with executable stack
Jun 20 17:09:03 s19 kernel: [ 1430.309723] mce: [Hardware Error]: Machine check events logged
Jun 20 17:10:28 s19 kernel: [ 1515.027384] mce: [Hardware Error]: Machine check events logged
Jun 20 17:14:08 s19 kernel: [ 1734.893259] mce: [Hardware Error]: Machine check events logged
Jun 20 17:46:42 s19 kernel: [    0.000000] microcode: updated early: 0xe2 -> 0xf4, date = 2022-07-31
```

the rasdaemon should have read out and logged to the journal during the  shutdown portion of reboot, but it still aborted:

```
sudo journalctl -u rasdaemon | tail -200
...
Jun 20 16:45:18 s19 rasdaemon[773]: ras:extlog_mem_event event enabled
Jun 20 16:45:18 s19 rasdaemon[773]: Enabled event ras:extlog_mem_event
Jun 20 17:46:19 s19 systemd[1]: Stopping RAS daemon to log the RAS events...
Jun 20 17:46:19 s19 rasdaemon[1515]: rasdaemon: ras:mc_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: rasdaemon: ras:aer_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: rasdaemon: mce:mce_record event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: rasdaemon: ras:extlog_mem_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: rasdaemon: ras:arm_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: ras:mc_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: ras:aer_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: mce:mce_record event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: ras:extlog_mem_event event disabled
Jun 20 17:46:19 s19 rasdaemon[1515]: ras:arm_event event disabled
Jun 20 17:46:19 s19 rasdaemon[773]: rasdaemon: Recevied signal=15
Jun 20 17:46:19 s19 rasdaemon[773]: overriding event (1486) ras:mc_event with new print handler
Jun 20 17:46:19 s19 rasdaemon[773]: overriding event (1483) ras:aer_event with new print handler
Jun 20 17:46:19 s19 rasdaemon[773]: overriding event (1485) ras:arm_event with new print handler
Jun 20 17:46:19 s19 rasdaemon[773]: overriding event (113) mce:mce_record with new print handler
Jun 20 17:46:19 s19 rasdaemon[773]: overriding event (1487) ras:extlog_mem_event with new print handler
Jun 20 17:46:19 s19 rasdaemon[773]: [COLOR="#FF0000"]Huh! something got wrong. Aborting.[/COLOR]
Jun 20 17:46:19 s19 systemd[1]: rasdaemon.service: Succeeded.
Jun 20 17:46:19 s19 systemd[1]: Stopped RAS daemon to log the RAS events.
-- Reboot --
Jun 20 17:46:42 s19 systemd[1]: Starting RAS daemon to log the RAS events...
Jun 20 17:46:42 s19 rasdaemon[790]: ras:mc_event event enabled
...
```

---

### Post by Doug S on 2023-06-21
I ran a trace of MCE events manually. Got 3 MCEs, as noted in the kern.log file. Stopped the trace and dumped the trace buffer. Nothing. I'm stumped and out of ideas.

EDIT: By the way, the reduce the maximum CPU frequency to increase timing margins method of mitigation I mentioned in [post #2]("https://ubuntuforums.org/showthread.php?t=2487675&p=14146974#post14146974") above, works for this particular issue. If I limit the max CPU frequency to 95%, I never get the MCE errors.

EDIT 2: Okay, success with manually running trace. This time I first stopped and disabled the rasdaemon service. So, I either did it wrong last time or the rasdeamon service was getting the way. This time I made scripts:

```
doug@s19:~/idle/perf$ cat mce-trace.txt
# tracer: nop
#
# entries-in-buffer/entries-written: 1/1   #P:12
#
#                                _-----=> irqs-off/BH-disabled
#                               / _----=> need-resched
#                              | / _---=> hardirq/softirq
#                              || / _--=> preempt-depth
#                              ||| / _-=> migrate-disable
#                              |||| /     delay
#           TASK-PID     CPU#  |||||  TIMESTAMP  FUNCTION
#              | |         |   |||||     |         |
     kworker/0:4-1042    [000] ..... [COLOR="#FF0000"]53303.037895[/COLOR]: mce_record: CPU: 0, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa8b465b4/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: c7052fb26155, PROCESSOR: 0:a0655, TIME: 1687361699, SOCKET: 0, APIC: 0
```

From kern.log:
```
Jun 21 08:34:59 s19 kernel: [[COLOR="#FF0000"]53303.059579[/COLOR]] mce: [Hardware Error]: Machine check events logged
```

The scripts:

```
doug@s19:~/idle/perf$ cat trace_mce_enable
#! /bin/bash

# trace_mce_enable. Smythies 2023.06.21
#       Enable MCE trace. Use default trace buffer size.
#       This script is just because I'll forget how.
#       Use trace_mce_disable to terminate and dump.
#
# run as sudo

# clean up any garbage.
echo "" >/sys/kernel/debug/tracing/trace

# allocate as much memory as possible.
#echo 1000000 >/sys/kernel/debug/tracing/buffer_size_kb
#echo 1500000 >/sys/kernel/debug/tracing/buffer_size_kb

echo 1 >/sys/kernel/debug/tracing/events/mce/mce_record/enable

```

and

```
doug@s19:~/idle/perf$ cat trace_mce_disable
#! /bin/bash

# trace_mce_disable. Smythies 2023.06.21
#       Disable MCE trace and dump the trace file.
#       This script is just because I'll forget how.
#
# run as sudo

echo 0 >/sys/kernel/debug/tracing/events/mce/mce_record/enable

cat /sys/kernel/debug/tracing/trace > mce-trace.txt

# clear the buffer for next time.
echo "" >/sys/kernel/debug/tracing/trace
```

Use the format file to help decode what the line means:

```
doug@s19:~/idle/perf$ sudo cat /sys/kernel/debug/tracing/events/mce/mce_record/format
name: mce_record
ID: 113
format:
        field:unsigned short common_type;       offset:0;       size:2; signed:0;
        field:unsigned char common_flags;       offset:2;       size:1; signed:0;
        field:unsigned char common_preempt_count;       offset:3;       size:1; signed:0;
        field:int common_pid;   offset:4;       size:4; signed:1;

        field:u64 mcgcap;       offset:8;       size:8; signed:0;
        field:u64 mcgstatus;    offset:16;      size:8; signed:0;
        field:u64 status;       offset:24;      size:8; signed:0;
        field:u64 addr; offset:32;      size:8; signed:0;
        field:u64 misc; offset:40;      size:8; signed:0;
        field:u64 synd; offset:48;      size:8; signed:0;
        field:u64 ipid; offset:56;      size:8; signed:0;
        field:u64 ip;   offset:64;      size:8; signed:0;
        field:u64 tsc;  offset:72;      size:8; signed:0;
        field:u64 walltime;     offset:80;      size:8; signed:0;
        field:u32 cpu;  offset:88;      size:4; signed:0;
        field:u32 cpuid;        offset:92;      size:4; signed:0;
        field:u32 apicid;       offset:96;      size:4; signed:0;
        field:u32 socketid;     offset:100;     size:4; signed:0;
        field:u8 cs;    offset:104;     size:1; signed:0;
        field:u8 bank;  offset:105;     size:1; signed:0;
        field:u8 cpuvendor;     offset:106;     size:1; signed:0;

print fmt: "CPU: %d, MCGc/s: %llx/%llx, MC%d: %016Lx, IPID: %016Lx, ADDR/MISC/SYND: %016Lx/%016Lx/%016Lx, RIP: %02x:<%016Lx>, TSC: %llx, PROCESSOR: %u:%x, TIME: %llu, SOCKET: %u, APIC: %x", REC->cpu, REC->mcgcap, REC->mcgstatus, REC->bank, REC->status, REC->ipid, REC->addr, REC->misc, REC->synd, REC->cs, REC->ip, REC->tsc, REC->cpuvendor, REC->cpuid, REC->walltime, REC->socketid, REC->apicid
```

EDIT 3: More events:

```
doug@s19:~/idle/perf$ cat mce-trace.txt
# tracer: nop
#
# entries-in-buffer/entries-written: 6/6   #P:12
#
#                                _-----=> irqs-off/BH-disabled
#                               / _----=> need-resched
#                              | / _---=> hardirq/softirq
#                              || / _--=> preempt-depth
#                              ||| / _-=> migrate-disable
#                              |||| /     delay
#           TASK-PID     CPU#  |||||  TIMESTAMP  FUNCTION
#              | |         |   |||||     |         |
     kworker/5:0-48      [005] .....  5005.737263: mce_record: CPU: 5, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa53c2c4d/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: 12c14cd046e8, PROCESSOR: 0:a0655, TIME: 1687375813, SOCKET: 0, APIC: a
     kworker/1:1-123     [001] .....  5413.471313: mce_record: CPU: 1, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa5143a46/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: 1446e7a84d08, PROCESSOR: 0:a0655, TIME: 1687376221, SOCKET: 0, APIC: 2
     kworker/3:3-452     [003] .....  5452.640009: mce_record: CPU: 3, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa5eadcc0/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: 146c55006d97, PROCESSOR: 0:a0655, TIME: 1687376260, SOCKET: 0, APIC: 6
     kworker/1:1-123     [001] .....  5637.231915: mce_record: CPU: 1, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa5004f90/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: 151cb765438c, PROCESSOR: 0:a0655, TIME: 1687376445, SOCKET: 0, APIC: 2
     kworker/5:0-48      [005] .....  5698.868443: mce_record: CPU: 5, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa54b565f/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: 15579cc35a61, PROCESSOR: 0:a0655, TIME: 1687376506, SOCKET: 0, APIC: a
     kworker/5:0-48      [005] .....  6632.120864: mce_record: CPU: 5, MCGc/s: c0c/0, MC0: 9400004000040150, IPID: 0000000000000000, ADDR/MISC/SYND: 0001ffffa5143a46/0000000000000000/0000000000000000, RIP: 00:<0000000000000000>, TSC: 18d35e8c097d, PROCESSOR: 0:a0655, TIME: 1687377439, SOCKET: 0, APIC: a
```

---

### Post by #&amp;thj^% on 2023-06-22
Doug S I found my notes finally, but nothing to report here. Sorry.
Mine just got fixed with updates and this was around 14 months ago.
But those are some serious looking logs.
```
name: mce_record
ID: 113
format:
	field:unsigned short common_type;	offset:0;	size:2;	signed:0;
	field:unsigned char common_flags;	offset:2;	size:1;	signed:0;
	field:unsigned char common_preempt_count;	offset:3;	size:1;signed:0;
	field:int common_pid;	offset:4;	size:4;	signed:1;

	field:u64 mcgcap;	offset:8;	size:8;	signed:0;
	field:u64 mcgstatus;	offset:16;	size:8;	signed:0;
	field:u64 status;	offset:24;	size:8;	signed:0;
	field:u64 addr;	offset:32;	size:8;	signed:0;
	field:u64 misc;	offset:40;	size:8;	signed:0;
	field:u64 synd;	offset:48;	size:8;	signed:0;
	field:u64 ipid;	offset:56;	size:8;	signed:0;
	field:u64 ip;	offset:64;	size:8;	signed:0;
	field:u64 tsc;	offset:72;	size:8;	signed:0;
	field:u64 walltime;	offset:80;	size:8;	signed:0;
	field:u32 cpu;	offset:88;	size:4;	signed:0;
	field:u32 cpuid;	offset:92;	size:4;	signed:0;
	field:u32 apicid;	offset:96;	size:4;	signed:0;
	field:u32 socketid;	offset:100;	size:4;	signed:0;
	field:u8 cs;	offset:104;	size:1;	signed:0;
	field:u8 bank;	offset:105;	size:1;	signed:0;
	field:u8 cpuvendor;	offset:106;	size:1;	signed:0;

print fmt: "CPU: %d, MCGc/s: %llx/%llx, MC%d: %016Lx, IPID: %016Lx, ADDR/MISC/SYND: %016Lx/%016Lx/%016Lx, RIP: %02x:<%016Lx>, TSC: %llx, PROCESSOR: %u:%x, TIME: %llu, SOCKET: %u, APIC: %x", REC->cpu, REC->mcgcap, REC->mcgstatus, REC->bank, REC->status, REC->ipid, REC->addr, REC->misc, REC->synd, REC->cs, REC->ip, REC->tsc, REC->cpuvendor, REC->cpuid, REC->walltime, REC->socketid, REC->apicid
```

---

### Post by Doug S on 2023-06-23
I am trying to decode the captured information. I think I have to reverse engineer the code to determine which MSR's are being read and then use the [Intel SDM]("325462-sdm-vol-1-2abcd-3abcd") to look up and decode those register contents.

Anyway, this thread now details one way to obtain more MCE information, which is what the OP was looking for.

---

