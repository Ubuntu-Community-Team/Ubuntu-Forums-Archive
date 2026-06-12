---
title: "Computer is freezing - home partition FSCK"
date: 2017-03-29
forum: Hardware
---

### Post by MarcoPau on 2017-03-29
Hi, I am experiencing often freezes on my computer. I have an SSD on my old Intel E2140 + ASUS P5K with AHCI upgrade.

At times, it goes in maintenance mode and I need to fsck /dev/sda4 (home). It's always that partition that needs fsck.

SSD is almost new, rest is old HW.

Is there any way I could troubleshoot the problem? Or is it maybe just a matter of throwing away Mobo + CPU?

Thanks a lot!

---

### Post by TheFu on 2017-03-29
The need for an fsck really is a symptom that the disk wasn't closed cleanly and that the journal log is corrupted in some way. That means the failure happened in the middle of a disk write transaction. Not good.  I've seen that maybe 5 times in 25 yrs.

You'll need to look at the log files immediately after a failure.  That means **booting from alternate media** (not the normal hdd) so the old logs aren't overwritten at the next boot.  Then mount the  partition with /var/logs and look in there for issues. Google "ubuntu log files" for more details.

It could be a bad SSD. Back it up, wipe it and return it.  Also, check the cable and power feed to the SSD. Just know that problem disks don't get better over time. They get worse.

But a computer freeze can be caused by all sorts of things. Could be RAM, PSU, or just running out of RAM+virtual memory.  In theory, the log files should show the issue and you'll be able to trace it back to a root cause.

---

### Post by MarcoPau on 2017-03-29
Wow, thanks for the explanation.

I was thinking: is that going to be OK if I check those logs after a freeze that won't end up in maintenance mode for FSCK?

Because only once every around 5-10 freezes it prompts me there.

If I don't reboot, I will never know if that is the case of FSCK or not.

If it's ok after any freeze, no problem, otherwise, I'm going to have to check those logs for quite a few times if I'm supposed to pick the time when it'd prompt to maintenance mode.

Is it also ok if I boot from another Ubuntu I have in the same computer but on another HD? I still keep the old Ubuntu I used before buying the SSD...

Thanks a lot!

---

### Post by TheFu on 2017-03-29
A GUI freeze isn't necessarily a system freeze. Are you able to log into the machine from another box and see that is it just the GUI?

BTW, there are thousands of possible reasons why a system could be locking up. I just provided a few examples.

You really need to look at the log files. Issues responsible are probably happening all the time, just not at the right instance to cause a lockup.  Any "alternate media" can work - really the goal is NOT to overwrite the log files in the problem OS install. How you do that is up to you. There are hundreds of alternatives.

---

### Post by MarcoPau on 2017-03-29
Great. I wouldn't say it's a GUI freeze since keyboard is not responding, can't alt F+num to switch TTY etc...

I will then use the other distro to boot and investigate thru the system logs.

Do you think I could post the logs in case I am not able to interpret them?

Thanks again.

---

### Post by MarcoPau on 2017-03-30
Computer froze, mounted the partition from the other ubuntu.

Can I paste some logs? These are the most recent lines.


syslog
Mar 30 10:16:55 pau kernel: [  230.420286] perf interrupt took too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Mar 30 10:17:01 pau CRON[2360]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

kern.log
kernel: [ 1810.338002] perf interrupt took too long (5002 > 5000), lowering kernel.perf_event_max_sample_rate to 25000

auth.log
Mar 30 10:17:01 pau CRON[2359]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 30 10:17:01 pau CRON[2359]: pam_unix(cron:session): session closed for user root

---

### Post by TheFu on 2017-03-30
I wouldn't paste much here. Only "relevant parts". - look for errors, warnings, crashes and the lines just above those (think groupings).

**dmesg** is where hardware stuff usually shows up. There is a log file for that - don't remember the name.

Nothing looks funny there. If you want to, sanitize your logs and post them using any of the txt file posting tools. I use sprung.us, but lots of others exist.

---

