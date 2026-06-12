---
title: "how to track down a hardware/memory failure?"
date: 2010-12-02
forum: Hardware
---

### Post by nagyv on 2010-12-02
Hi,

I've a Lenovo ThinkPad T61, installed with Lucid Lynx on it. For a long time I've had no problems with my laptop, and I guess that now I have some kind of hardware failure, that I would like to find, and handle.

Sometimes, all the apps stop working, no peripherals are responding, and one of the leds on the laptop starts to blink.

My only solution to this problem so far was a reboot.

What are the tools to find out the problem?
I've tried to find any information in my log files, but my knowledge is rather limited in these areas.

Here are some parts of my logfiles:
**messages:**
Dec  2 09:09:50 akasha kernel: [11584.439073] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec  2 09:12:12 akasha kernel: [11725.919193] padlock: VIA PadLock not detected.
Dec  2 09:14:59 akasha kernel: [11893.802376] lo: Disabled Privacy Extensions
Dec  2 09:29:01 akasha kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec  2 09:29:01 akasha rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="834" x-info="http://www.rsyslog.com"] (re)start
Dec  2 09:29:01 akasha rsyslogd: rsyslogd's groupid changed to 103
Dec  2 09:29:01 akasha rsyslogd: rsyslogd's userid changed to 101
Dec  2 09:29:01 akasha kernel: [    0.000000] Initializing cgroup subsys cpuset

**syslog:**
Dec  2 09:12:20 akasha NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec  2 09:12:21 akasha ntpdate[4058]: step time server 91.189.94.4 offset -0.521633 sec
Dec  2 09:14:59 akasha kernel: [11893.802376] lo: Disabled Privacy Extensions
Dec  2 09:17:01 akasha CRON[4166]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  2 09:29:01 akasha kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec  2 09:29:01 akasha rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="834" x-info="http://www.rsyslog.com"] (re)start
Dec  2 09:29:01 akasha rsyslogd: rsyslogd's groupid changed to 103
Dec  2 09:29:01 akasha rsyslogd: rsyslogd's userid changed to 101

Thanks for your help.

---

