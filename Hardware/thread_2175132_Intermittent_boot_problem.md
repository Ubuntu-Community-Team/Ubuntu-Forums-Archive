---
title: "Intermittent boot problem"
date: 2013-09-17
forum: Hardware
---

### Post by Duncan J Murray on 2013-09-17
Hi all,

I've been plagued by an intermittent boot problem which happens when booting from cold.  The bios splash comes up first, there's a bit of hard-drive activity, and then it all stops with a black screen, and an odd red dotty pattern which covers a strip about 15 pixels across the top of the screen.  At this point I can't ctrl-alt to another virtual terminal, and the only option is holding down the power button to get it to switch off.

The problem happens around 1/5 times, and sometimes happens twice in a row.  It's been going on since I've used 10.04 on my laptop.

My current harware : Thinkpad T60p with dual-core T2500 2.00Ghz, 10.04, 2.6.32-51, gnome 2.30.2, 2GiB RAM, and I think the 256MB ATI Mobility FireGL V5200.  It's all updated to the latest version.

I've looked in /var/log/messages (dmesg only seems to give me the current boot, which is successful).

The odd thing is that I don't think it's recording the failed boot - see here:

Sep 17 20:28:58 T60 kernel: [ 2819.532973] Registered led device: iwl-phy0::assoc
Sep 17 20:28:58 T60 kernel: [ 2819.533243] Registered led device: iwl-phy0::RX
Sep 17 20:28:58 T60 kernel: [ 2819.533702] Registered led device: iwl-phy0::TX
Sep 17 20:28:58 T60 kernel: [ 2819.545054] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 17 20:28:58 T60 kernel: [ 2820.169197] usb 5-1: new full speed USB device using uhci_hcd and address 4
Sep 17 20:28:58 T60 kernel: [ 2820.339432] usb 5-1: configuration #1 chosen from 1 choice
Sep 17 20:29:04 T60 kernel: [ 2826.286022] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 17 21:55:02 T60 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 17 21:55:02 T60 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="858" x-info="http://www.rsyslog.com"] (re)start
Sep 17 21:55:02 T60 rsyslogd: rsyslogd's groupid changed to 103
Sep 17 21:55:02 T60 rsyslogd: rsyslogd's userid changed to 101
Sep 17 21:55:02 T60 kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 17 21:55:02 T60 kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 17 21:55:02 T60 kernel: [    0.000000] Linux version 2.6.32-51-generic (buildd@aatxe) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #113-Ubuntu SMP Wed Aug 21 19:47:04 UTC 2013 (Ubuntu 2.6.32-51.113-generic 2.6.32.61+drm33.26)

where the beginning of the next boot seems to be the current, successful one, even though I experienced the failed start (twice) immediately before the 21:55 boot.

My interpretation of this is that the boot isn't getting very far in the process, and that this might be a hardware problem.  Is this right?  The way it is intermittent makes me think it's a memory problem.

Any ideas on how to investigate this further?

Thanks in advance.

D

---

