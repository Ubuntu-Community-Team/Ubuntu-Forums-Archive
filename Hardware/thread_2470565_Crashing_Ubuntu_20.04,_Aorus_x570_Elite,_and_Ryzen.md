---
title: "Crashing: Ubuntu 20.04, Aorus x570 Elite, and Ryzen 5 5600G"
date: 2022-01-04
forum: Hardware
---

### Post by Daniël Slenders on 2022-01-04
Hi all

I just assembled my first own desktop running Ubuntu 20.04 - however, at random moments the system completely freezes:
[LIST]
[*]desktop environment goes blank: so more video input, mouse and keyboard unresponsive
[*]SSH connections are terminated
[/LIST]
However, the system does not shut down automatically - CPU fan, disks and motherboard remain active.

I have following hardware:
[LIST]
[*]motherboard: Gigabyte X570 Aorus Elite running BIOS F35
[*]CPU: AMD Ryzen 5 5600G
[*]memory: 32GB Corsair Vengeance LPX (CMK32GX4M2Z3600C18)
[/LIST]

Software:
[LIST]
[*]Operating System: Ubuntu 20.04.3 LTS
[*]Kernel: Linux 5.11.0-43-generic
[*]Architecture: x86-64
[/LIST]



Things I've tried so far:
[LIST]
[*]CPU stresstest (with s-tui) - nothing unexpected came up
[*]memory stresstest (with memtest) - nothing unexpected came up
[*]activated and de-activated XMP in BIOS - system has crashed in both conditions
[/LIST]

Any ideas on why this might be happening?

Any thoughts would be much appreciated!!

---

### Post by TheFu on 2022-01-04
I've found Ryzen CPUs/MBs to be very picky about RAM.  In the system logs, if there are memory faults, try slowing the RAM down.  Start with the D.O.C.P. profile for the RAM, but slow it down.  For unmatched pairs, I've had to drop 3200Mhz RAM to 2666Mhz to get stability.

I have a Ryzen 2600 and a 5600G.  Both use Asus B450 Motherboards (I didn't want the 2.5Gbps new Intel NIC that a B550 would include, but did want Intel GigE NICs).  The 5600G has only 16G in a matched pair of RAM sticks.  It is running at 
```
$ sudo inxi -m
Memory:    Used/Total: 5709.6/15112.3MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: No Module Installed type: N/A
           Device-2: DIMM_A2 size: 8 GB speed: 3200 MT/s type: DDR4
           Device-3: DIMM_B1 size: No Module Installed type: N/A
           Device-4: DIMM_B2 size: 8 GB speed: 3200 MT/s type: DDR4
```

The 2600, runs RAM at:
```
$ sudo inxi -m
Memory:    Used/Total: 19262.5/32101.8MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-2: DIMM_A2 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-3: DIMM_B1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-4: DIMM_B2 size: 8 GB speed: 2666 MT/s type: DDR4
```

**journalctl -b -1** and look for 'dump_stack'

---

### Post by Daniël Slenders on 2022-01-04
Thanks a lot for the quick response!!

Where best in the system logs can I whether there are memory faults? Reading through the different files in /var/log nothing out of the ordinary comes up as far as I can find...

> **TheFu said:**
> Start with the D.O.C.P. profile for the RAM, but slow it down. For unmatched pairs, I've had to drop 3200Mhz RAM to 2666Mhz to get stability.
Default RAM speed using JEDEC config in BIOS is 2666 MHz, but RAM can go up to 3600 as per specs - in both cases I have had the same error. Would it make a difference if I set it to be XMP and at 2666 MHz? Should I also change the voltage settings here? (currently at 1.2V but can go up to 1.35V which I've heard other people do to get more stability)

> **TheFu said:**
> **journalctl -b -1** and look for 'dump_stack'
This comes back blank.

---

### Post by TheFu on 2022-01-04
It was just a shot in the dark.  Check the logs for any warnings or errors, then look each up and decide if they are relevant on the system. Some errors and warnings are seen because a system doesn't have the hardware that someone in the kernel team expected, no necessarily any failure.  But failures will also show up.  Read up on using **journalctl** to look through different log files.  The command I posted only shows the boot/hardware messages from the prior boot, no all prior boots. May want to look back a few - perhaps the last 10 boots - while troubleshooting this.

If you can reproduce the problem on demand, then you can try different things so determine if it is hardware or software or configuration causing the crash.  BTW, defining what you think a "crash" is would be helpful too, since we all have different definitions and the actual result can be different for the different possible types.  

For example, can you boot 21.10?  Does that release also crash?  What about 18.04?  What about non-Ubuntu distros?

---

### Post by Daniël Slenders on 2022-01-07
Thanks for the help!

I've been trying a couple of additional things, nothing conclusive yet
[LIST]
[*]Swapped my RAM for Corsair 32 GB DDR4-3200 Quad-Kit (CMH32GX4M4E3200C16) which is actually on the QVL of the motherboard --> same results with both XMP enabled (running at 3200MHz) and disabled (running at 2667 MHz).
[*]Upgraded to Ubuntu 21.04 --> same results.
[*]Switched to Ubuntu Server 20.04 --> seemed to be stable for as long as I kept running the CPU at load (running 12 hour stresstest). Once I stopped the stresstest, within 20 minutes the system crashed.
[*]Upgraded to Ubuntu Server 21.04 and 21.10 --> same results.
[/LIST]

After further research I found this thread on AskUbuntu: [https://askubuntu.com/questions/1234299/amd-ryzen-5-3600-ubuntu-20-04-problems/1241636#1241636](https://askubuntu.com/questions/1234299/amd-ryzen-5-3600-ubuntu-20-04-problems/1241636#1241636) which seems to describe similar problems. I've changed my BIOS settings in line with the suggestions:

[LIST]
[*]Global C State Control: Disabled
[*]Power Idle Control: Typical Current Idle
[*]SMT: Disabled
[/LIST]
However, haven't changed any ACPI config in grub yet. Currently testing and the system has been stable for the last 60 minutes or so (without any particular load - average below 5%).

One additional thing I've found in the logs is a potential issue with AppArmor which seems to have happened right before the last 2 crashes (unclear whether it causes the crash or whether the crash causes the AppArmor error though or whether unrelated).
> Jan 06 19:51:03.299579 home kernel: EXT4-fs (nvme0n1p2): mounted filesystem with ordered data mode. Opts: (null)Jan 06 19:51:03.408624 home kernel: audit: type=1400 audit(1641498663.404:2): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.423576 home kernel: audit: type=1400 audit(1641498663.416:3): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.423699 home kernel: audit: type=1400 audit(1641498663.416:4): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.443593 home kernel: audit: type=1400 audit(1641498663.436:5): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.443756 home kernel: audit: type=1400 audit(1641498663.436:6): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.443778 home kernel: audit: type=1400 audit(1641498663.436:7): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.455584 home kernel: audit: type=1400 audit(1641498663.448:8): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.515680 home kernel: audit: type=1400 audit(1641498663.508:9): apparmor="STATUS" operation="profile_l>
Jan 06 19:51:03.515788 home kernel: audit: type=1400 audit(1641498663.508:10): apparmor="STATUS" operation="profile_>
Jan 06 19:51:03.515845 home kernel: audit: type=1400 audit(1641498663.508:11): apparmor="STATUS" operation="profile_>
Jan 06 19:51:05.747609 home kernel: igb 0000:03:00.0 enp3s0: igb: enp3s0 NIC Link is Up 100 Mbps Full Duplex, Flow C>
Jan 06 19:51:05.747900 home kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
Jan 06 19:51:21.551779 home kernel: kauditd_printk_skb: 18 callbacks suppressed
Jan 06 19:51:21.551896 home kernel: audit: type=1400 audit(1641498681.544:30): apparmor="STATUS" operation="profile_>
Jan 06 19:51:21.587668 home kernel: audit: type=1400 audit(1641498681.580:31): apparmor="STATUS" operation="profile_>
Jan 06 19:51:21.643584 home kernel: audit: type=1400 audit(1641498681.636:32): apparmor="STATUS" operation="profile_>
Jan 06 19:51:21.691593 home kernel: audit: type=1400 audit(1641498681.684:33): apparmor="STATUS" operation="profile_>
Jan 06 19:51:21.739693 home kernel: audit: type=1400 audit(1641498681.732:34): apparmor="STATUS" operation="profile_>
Jan 06 19:51:21.739799 home kernel: audit: type=1400 audit(1641498681.732:35): apparmor="STATUS" operation="profile_>
Jan 06 19:52:02.711443 home systemd-shutdown[1]: Syncing filesystems and block devices.
Jan 06 19:52:02.716278 home systemd-shutdown[1]: Sending SIGTERM to remaining processes...

> Jan 07 11:47:15.291202 home kernel: audit: type=1400 audit(1641556035.283:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter">Jan 07 11:47:15.291212 home kernel: audit: type=1400 audit(1641556035.283:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" >
Jan 07 11:47:15.291220 home kernel: audit: type=1400 audit(1641556035.283:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/sn>
Jan 07 11:47:15.291234 home kernel: audit: type=1400 audit(1641556035.283:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/sn>
Jan 07 11:47:15.291244 home kernel: audit: type=1400 audit(1641556035.287:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="tcpdump" p>
Jan 07 11:47:15.295153 home kernel: audit: type=1400 audit(1641556035.287:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/N>
Jan 07 11:47:17.371055 home kernel: igb 0000:03:00.0 enp3s0: igb: enp3s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jan 07 11:47:17.371382 home kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
Jan 07 11:47:17.807053 home kernel: rfkill: input handler disabled
Jan 07 11:47:20.647103 home kernel: loop8: detected capacity change from 0 to 8
Jan 07 11:47:20.759066 home kernel: kauditd_printk_skb: 22 callbacks suppressed
Jan 07 11:47:20.759192 home kernel: audit: type=1400 audit(1641556040.751:34): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.759262 home kernel: audit: type=1400 audit(1641556040.751:35): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.763050 home kernel: audit: type=1400 audit(1641556040.755:36): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.763177 home kernel: audit: type=1400 audit(1641556040.755:37): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.763236 home kernel: audit: type=1400 audit(1641556040.755:38): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.763264 home kernel: audit: type=1400 audit(1641556040.755:39): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.763338 home kernel: audit: type=1400 audit(1641556040.755:40): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.767102 home kernel: audit: type=1400 audit(1641556040.759:41): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.767185 home kernel: audit: type=1400 audit(1641556040.759:42): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:47:20.767207 home kernel: audit: type=1400 audit(1641556040.759:43): apparmor="STATUS" operation="profile_replace" info="same as current profile, ski>
Jan 07 11:49:19.571181 home kernel: kauditd_printk_skb: 7 callbacks suppressed
Jan 07 11:49:19.571263 home kernel: audit: type=1400 audit(1641556159.565:51): apparmor="DENIED" operation="capable" profile="/snap/snapd/14295/usr/lib/snapd/s>
Jan 07 11:49:19.691148 home kernel: audit: type=1400 audit(1641556159.685:52): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.691251 home kernel: audit: type=1400 audit(1641556159.685:53): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695064 home kernel: audit: type=1400 audit(1641556159.689:54): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695150 home kernel: audit: type=1400 audit(1641556159.689:55): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695174 home kernel: audit: type=1400 audit(1641556159.689:56): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695189 home kernel: audit: type=1400 audit(1641556159.689:57): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695203 home kernel: audit: type=1400 audit(1641556159.689:58): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695216 home kernel: audit: type=1400 audit(1641556159.689:59): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:49:19.695230 home kernel: audit: type=1400 audit(1641556159.689:60): apparmor="DENIED" operation="open" profile="snap.stress-ng.stress-ng" name="/pro>
Jan 07 11:50:20.135134 home kernel: rfkill: input handler enabled
Jan 07 11:50:21.663053 home kernel: EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: errors=remount-ro. Quota mode: none.
Jan 07 11:50:21.687083 home kernel: rfkill: input handler disabled
Jan 07 11:50:35.859287 home kernel: usb 7-1: new low-speed USB device number 2 using xhci_hcd
Jan 07 11:50:36.019390 home kernel: usb 7-1: New USB device found, idVendor=0461, idProduct=4d64, bcdDevice= 2.00
Jan 07 11:50:36.019942 home kernel: usb 7-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Jan 07 11:50:36.020051 home kernel: usb 7-1: Product: USB Optical Mouse
Jan 07 11:50:36.043173 home kernel: input: USB Optical Mouse as /devices/pci0000:00/0000:00:08.1/0000:08:00.4/usb7/7-1/7-1:1.0/0003:0461:4D64.0003/input/input15
Jan 07 11:50:36.043275 home kernel: hid-generic 0003:0461:4D64.0003: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:08:00.4-1/input0
Jan 07 11:51:04.123682 home kernel: show_signal: 17 callbacks suppressed
Jan 07 11:51:04.123754 home kernel: traps: gnome-control-c[2654] trap int3 ip:7f9f3398166f sp:7fffbd8410e0 error:0 in libglib-2.0.so.0.6800.4[7f9f33942000+8d00>
Jan 07 11:51:13.171202 home kernel: traps: gnome-control-c[2696] trap int3 ip:7fd03259a66f sp:7ffc231599c0 error:0 in libglib-2.0.so.0.6800.4[7fd03255b000+8d00>
Jan 07 11:52:09.955311 home kernel: traps: gnome-control-c[4744] trap int3 ip:7f73ea65266f sp:7ffe878a9820 error:0 in libglib-2.0.so.0.6800.4[7f73ea613000+8d00>
Jan 07 11:52:56.571046 home kernel: rfkill: input handler enabled
Jan 07 11:52:58.323057 home kernel: rfkill: input handler disabled

---

### Post by TheFu on 2022-01-07
Ouch.  My Ryzen 2600 and 5600G don't have those issues, thankfully.  Some of the answers seem a little far fetched - without links to the kernel dev email list clearly saying these are the issues, I'm not sure I'd believe the answers.  Not seeing CPUs? 

Have you updated the BIOS for the motherboard?  May need to do that monthly for this year.

---

