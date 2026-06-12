---
title: "random freezes"
date: 2023-11-17
forum: Hardware
---

### Post by gerard-lerest-o on 2023-11-17
Good eveening,

I'm French, so be cool with my english!
My computer freeze sometimes. I saw stranges things. There was reds lines beside this lines  kern.log
```
nov 12 15:39:18 gerard-ThinkCentre-M700 kernel: [    0.090580] rcu:     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=4.Nov 12 15:39:18 gerard-ThinkCentre-M700 kernel: [    0.090581]  Trampoline variant of Tasks RCU enabled.
Nov 12 15:39:18 gerard-ThinkCentre-M700 kernel: [    0.090582]  Rude variant of Tasks RCU enabled.
Nov 12 15:39:18 gerard-ThinkCentre-M700 kernel: [    0.090582]  Tracing variant of Tasks RCU enabled.
```
and these line:
```
Nov 12 15:39:18 gerard-ThinkCentre-M700 kernel: [    0.149020] rcu:     Max phase no-delay instances is 1000.
```

I made " sudo journalctl " and there were red lines:
```
 pulseaudio[1884]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send>
```
```
.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the n>
```

and an another day kern.log gave:
```
Nov 16 16:59:09 gerard-ThinkCentre-M700 kernel: [ 4557.292284] audit: type=1400 audit(1700150349.864:197): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature_next.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:00:07 gerard-ThinkCentre-M700 kernel: [ 4615.067025] audit: type=1400 audit(1700150407.640:198): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature_next.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:00:07 gerard-ThinkCentre-M700 kernel: [ 4615.067751] audit: type=1400 audit(1700150407.640:199): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:00:19 gerard-ThinkCentre-M700 kernel: [ 4627.060565] audit: type=1400 audit(1700150419.632:200): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:00:19 gerard-ThinkCentre-M700 kernel: [ 4627.060970] audit: type=1400 audit(1700150419.632:201): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature_next.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:00:19 gerard-ThinkCentre-M700 kernel: [ 4627.064750] audit: type=1400 audit(1700150419.636:202): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature_next.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:00:19 gerard-ThinkCentre-M700 kernel: [ 4627.065513] audit: type=1400 audit(1700150419.636:203): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature.txt" pid=20922 comm="FSBroker21574" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 16 17:03:16 gerard-ThinkCentre-M700 kernel: [ 4803.888499] perf: interrupt took too long (3357 > 3325), lowering kernel.perf_event_max_sample_rate to 59500
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] microcode: microcode updated early to revision 0xf0, date = 2021-11-12
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] Linux version 6.2.0-36-generic (buildd@lcy02-amd64-050) (x86_64-linux-gnu-gcc-11 (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct  9 15:34:04 UTC 2 (Ubuntu 6.2.0-36.37~22.04.1-generic 6.2.16)
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-36-generic root=UUID=b06329e6-0496-4800-a33e-5a016ffbdd13 ro quiet splash vt.handoff=7
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] KERNEL supported cpus:
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000]   Intel GenuineIntel
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000]   AMD AuthenticAMD
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000]   Hygon HygonGenuine
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000]   Centaur CentaurHauls
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000]   zhaoxin   Shanghai  
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b8491fff] usable
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000b8492000-0x00000000b8492fff] ACPI NVS
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000b8493000-0x00000000b84bcfff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000b84bd000-0x00000000bb903fff] usable
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bb904000-0x00000000bc862fff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bc863000-0x00000000bc925fff] ACPI data
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bc926000-0x00000000bce58fff] ACPI NVS
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bce59000-0x00000000bd2fefff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bd2ff000-0x00000000bd2fffff] usable
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bd300000-0x00000000bd3fffff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Nov 16 17:04:19 gerard-ThinkCentre-M700 kernel: [    0.00000...

```

et and later:
```

Nov 17 16:55:39 gerard-ThinkCentre-M700 kernel: [11813.048229] audit: type=1400 audit(1700236539.276:398): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature.txt" pid=30888 comm="FSBroker31424" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 17 16:55:39 gerard-ThinkCentre-M700 kernel: [11813.070096] audit: type=1400 audit(1700236539.300:399): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature.txt" pid=30888 comm="FSBroker31424" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 17 16:55:39 gerard-ThinkCentre-M700 kernel: [11813.070385] audit: type=1400 audit(1700236539.300:400): apparmor="DENIED" operation="open" class="file" profile="snap.firefox.firefox" name="/etc/igfx_user_feature_next.txt" pid=30888 comm="FSBroker31424" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 17 16:57:38 gerard-ThinkCentre-M700 kernel: [11931.925306] audit: type=1400 audit(1700236658.150:401): apparmor="DENIED" operation="open" class="file" profile="snap.chromium.chromium" name="/proc/pressure/cpu" pid=32204 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 17 16:57:38 gerard-ThinkCentre-M700 kernel: [11931.925321] audit: type=1400 audit(1700236658.150:402): apparmor="DENIED" operation="open" class="file" profile="snap.chromium.chromium" name="/proc/pressure/io" pid=32204 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 17 16:57:38 gerard-ThinkCentre-M700 kernel: [11931.925330] audit: type=1400 audit(1700236658.150:403): apparmor="DENIED" operation="open" class="file" profile="snap.chromium.chromium" name="/proc/pressure/memory" pid=32204 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov 17 17:02:25 gerard-ThinkCentre-M700 kernel: [12219.194610] audit: type=1107 audit(1700236945.420:404): pid=880 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" name=":1.3" mask="receive" pid=30888
```

Thank you a lot for your help.

---

### Post by TheFu on 2023-11-19
To me, only the memory dump looks bad.  

apparmor complains all the time. That's normal.
dbus errors are common.
and anything with freedesktop.org in it is extremely common. 

What I would do is look ensure my watch/phone clock and computer clock match ... to the second.  Then I'd use the computer until it has a problem, note the exact time.  Then I'd pull the logs for 30 seconds before/after that exact time and read ever single line in the logs.  Not just errors. All of them. See what it says.

Some errors like a bad PSU generally don't show up in logs, unless we are really lucky and get an undervoltage warning.

Also, pay specific attention to any stack traces.  These will have the program all the way down into the subsystem where a failure happened. It will be the RAM, Storage, GPU or GPU from my experience.  

I had RAM that wouldn't run at full speed after I'd added 2 more sticks.  All 4 sticks weren't from matched sets. I had 2 separate sets of 2-matched sets. All the RAM was the same vendor, same model, same speed, same everything. Separately, each set worked at the stated clock speed, 3200Mhz.  But with all four sticks installed, it wouldn't boot until I slowed it to 2900Mhz, but it still crashed a few times every day.  So I slowed the RAM down bit by bit until it ran for 3+ days without any crash ... that was at 2666Mhz.    I needed the extra RAM, so I waited for RAM prices to drop over 50% and replaced those 4 sticks with 2 larger sticks and have been happy since. That's just an example.

Of course, I don't know what the issue is with your system.  When the logs don't jump out with the clear error, start looking for lose connections, dust, and other physical issues.  Swap in 1 new component at a time.  Many computer shops have testing equipment for things like PSUs and will test a GPU too.  I've had a failing GPU cause a system to crash.  Over the years, the heating on that GPU caused some of the solder connections to become lose, that's my guess.  Eventually, it fried and the computer wouldn't boot without a GPU.  It was 10+ yrs old, so time for an upgrade.

---

### Post by gerard-lerest-o on 2024-01-26
Good evening, I just read your message. Thank you for it. The problem came from the Firefox snap. I uninstalled it and installed the deb version for Ubuntu. Everything is okay now.

---

