---
title: "[SOLVED] Ubuntu politely insists HD full even though it is clearly not"
date: 2008-11-13
forum: General Help
---

### Post by gruntlips_ on 2008-11-13
When I try and install or uninstall software I run into the following general error:

can't write to [some location on my HD] device is full

When I do df -h, I am showing having over 40 gigs still available on /sd3.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              13G   13G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  224K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  292K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3             157G  113G   38G  76% /home
overflow              1.0M  972K   52K  95% /tmp

When I do baobab / from the command line the program lists my root and home directory as 100% full, despite the fact that none of the subdirectories are anywhere near this mark.  Also I cannot save files to my home directory (such as an email attachment) but I can appear to save changes to a open office doc that I am working on that is saved in my home directory.

This problem just seemed to happen out of nowhere and I can't think of anything I explicitly did to cause it.

I am running 8.10 on a system76 serval.  Any help would be appreciated.  I probably start freaking out in about an hour or so.

Thanks.

- Chris

---

### Post by taurus on 2008-11-13
> **gruntlips_ said:**
> When I try and install or uninstall software I run into the following general error:

can't write to [some location on my HD] device is full

When I do df -h, I am showing having over 40 gigs still available on /sd3.

Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda1              13G   13G     0 100% /[/COLOR]**
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  224K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  292K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3             157G  113G   38G  76% /home
overflow              1.0M  972K   52K  95% /tmp

When I do baobab / from the command line the program lists my root and home directory as 100% full, despite the fact that none of the subdirectories are anywhere near this mark.  Also I cannot save files to my home directory (such as an email attachment) but I can appear to save changes to a open office doc that I am working on that is saved in my home directory.

This problem just seemed to happen out of nowhere and I can't think of anything I explicitly did to cause it.

I am running 8.10 on a system76 serval.  Any help would be appreciated.  I probably start freaking out in about an hour or so.

Thanks.

- Chris

Your / is full, 100%.  Therefore, you will not be able to install anything to your machine (except to your own $HOME) unless you free up some space.

```
sudo apt-get clean
sudo apt-get autoremove
```
Look in /var or /tmp to make sure there are no big files in there, eating up all your space.

---

### Post by ohzopants on 2008-11-13
Programs are installed in the root device, not under /home.

Your / partition (/dev/sda1) is full.

```

sudo apt-get autoremove

```

Always seems to clear up some space for me.  There is also a command to clear apt-get's cache, you might want to try that.

---

### Post by Idefix82 on 2008-11-13
According to df -h your / partition is indeed full. That's why you can't install software. I imagine that when you try to save to /home, it might temporarily need some space on the root partition. You can start by running
```
sudo apt-get clean
sudo apt-get autoremove
```

The first command will delete temporary package files that Synaptic had to download to install things and the second command will remove packages that were installed automatically as dependencies but are no longer needed.

If the first command frees up enough space, you might not want to run the second since it's a bit risky.

---

### Post by ohzopants on 2008-11-13
Damn you taurus!  You even knew the command that I couldn't remember.

---

### Post by taurus on 2008-11-13
> **ohzopants said:**
> Damn you taurus!  You even knew the command that I couldn't remember.

Oh me!  :oops:

---

### Post by JNelson on 2008-11-13
try

> sudo tune2fs -m 0 /dev/sda3


Ext3 reserves 5% of disk space for some reason this should give you all the space.

---

### Post by gruntlips_ on 2008-11-13
Holy cow, yes you are all right - I am an idiot and my root directory is almost hosed. I ran sudo apt-get clean and freed up a tiny bit of space but sudo apt-get autoremove crashes.  I poked around a bit and it appears that my /var/log directory has three massive plain-text files in it:

syslog.0   2.8 GB
kern.log.0  2.8 GB
messages.0  2.6 GB

These were created today, the day the issue started and account for much of the space in my root directory (13 GB).  This led to 3 questions:

1) Can I delete these files?
2) What created these enormous files in the first place?
3) When I open these files in a text editor they are empty (no characters or hard returns).  How can these empty files take up so much space on the HD?


Thanks.

- Chris

---

### Post by taurus on 2008-11-13
Those three are backup files of /var/log/syslog, /var/log/kern.log, /var/log/messages.  Therefore, it's save to remove them.

```
cd /var/log
sudo rm syslog.0 kern.log.0 messages.0
df -h
```

---

### Post by gruntlips_ on 2008-11-13
Thanks taurus.  That worked just great.  

I am curious though - why did my system spawn those huge files in the first place?  Is it a symptom of something wrong with my OS?  

Here is the /var/log directory. I seem to have a lot of these syslog, kern.log, and message files, but none of them are the size of the three most recent.

coldwater@coldwater-laptop:/var/log$ ls -lk sys* ker* mess*
-rw-r----- 1 syslog adm  203 2008-11-13 17:27 kern.log
-rw-r----- 1 syslog adm   95 2008-11-12 10:49 kern.log.1.gz
-rw-r----- 1 syslog adm  167 2008-11-09 11:50 kern.log.2.gz
-rw-r----- 1 syslog adm   15 2008-11-05 09:14 kern.log.3.gz
-rw-r----- 1 syslog adm 6750 2008-11-04 10:09 kern.log.4.gz
-rw-r----- 1 syslog adm   46 2008-10-20 16:30 kern.log.5.gz
-rw-r----- 1 syslog adm  108 2008-10-06 17:58 kern.log.6.gz
-rw-r----- 1 syslog adm  177 2008-11-13 17:18 messages
-rw-r----- 1 syslog adm   15 2008-11-12 10:50 messages.1.gz
-rw-r----- 1 syslog adm  186 2008-11-11 10:34 messages.2.gz
-rw-r----- 1 syslog adm   13 2008-11-05 09:27 messages.3.gz
-rw-r----- 1 syslog adm 6074 2008-11-04 10:09 messages.4.gz
-rw-r----- 1 syslog adm   40 2008-10-20 16:38 messages.5.gz
-rw-r----- 1 syslog adm   72 2008-10-06 18:31 messages.6.gz
-rw-r----- 1 syslog adm  254 2008-11-13 17:27 syslog
-rw-r----- 1 syslog adm   33 2008-11-12 10:50 syslog.1.gz
-rw-r----- 1 syslog adm   32 2008-11-11 10:37 syslog.2.gz
-rw-r----- 1 syslog adm   69 2008-11-10 09:40 syslog.3.gz
-rw-r----- 1 syslog adm   75 2008-11-09 12:00 syslog.4.gz
-rw-r----- 1 syslog adm   60 2008-11-08 13:23 syslog.5.gz
-rw-r----- 1 syslog adm   81 2008-11-06 15:46 syslog.6.gz

---

### Post by taurus on 2008-11-13
Those are logs of your system.  If there is something wrong with your system, it will be recorded in them.  So, you should at least try to look at them (not all the time) to make sure your system is healthy.  And by the way, you can remove those .gz because those are the old logs.

p.s.  Do you have /var/backups also?

```
ls -la /var/backups
```

---

### Post by gruntlips_ on 2008-11-13
Taurus, yes I do have a bunch of backup files.  I also remember that when I closed my computer down this morning it kept repeating:

bad: scheduling from the idle thread!

during the shutdown.  It created those 3 enormous log files at the time.  I am pasting some of the syslog file from that time (too big to upload) and the kern.log as well below it.  To me this is all greek - but it seems like you might well understand what is going on.

Thanks again.

- Chris

syslog file....

Nov 13 07:45:51 coldwater-laptop syslogd 1.5.0#2ubuntu6: restart.
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630436]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630437] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630508] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630510] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630511] 
Nov 13 07:45:51 coldwater-laptop anacron[7694]: Job `cron.daily' terminated (mailing output)
Nov 13 07:45:51 coldwater-laptop anacron[7694]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Nov 13 07:45:51 coldwater-laptop anacron[7694]: Normal exit (1 job run)
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630512] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630514]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630516]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630517]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630519]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630521]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630524]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630526]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630527] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630552] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630554] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630555] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630556] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630558]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630560]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630561]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630563]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630565]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630568]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630570]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630571] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630591] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630593] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630595] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630595] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630597]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630599]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630600]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630602]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630605]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630607]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630609]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630610] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630691] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630693] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630694] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630695] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630697]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630698]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630700]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630702]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630704]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630707]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630709]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630710] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630764] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630766] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630767] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630767] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630769]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630771]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630773]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630775]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630777]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630779]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630781]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630783] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630838] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630840] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630841] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630842] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630844]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630846]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630847]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630849]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630852]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630854]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630856]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630857] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630994] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630996] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630997] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630998] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630999]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631001]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631003]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631005]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631007]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631010]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631011]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631013] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631034] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631035] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631037] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631037] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631039]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631041]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631043]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631045]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631047]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631049]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631051]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631052] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631072] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631074] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631075] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631076] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631078]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631080]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631081]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631083]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631085]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631088]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631090]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631091] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631168] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631170] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631172] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631172] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631174]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631176]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631178]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631180]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631182]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631184]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631186]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631188] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631247] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631249] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631250] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631250] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631252]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631254]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631256]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631258]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631260]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631262]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631264]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631266] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631326] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631327] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631329] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631329] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631331]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631333]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631335]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631337]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631339]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631341]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631343]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631344] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631414] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631416] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631417] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631418] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631420]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631422]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631423]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631425]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631427]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631430]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631432]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631433] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631502] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631503] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1

kern.log file...

Nov 13 07:45:51 coldwater-laptop kernel: [43357.630436]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630437] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630508] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630510] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630511] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630512] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630514]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630516]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630517]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630519]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630521]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630524]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630526]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630527] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630552] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630554] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630555] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630556] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630558]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630560]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630561]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630563]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630565]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630568]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630570]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630571] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630591] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630593] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630595] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630595] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630597]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630599]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630600]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630602]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630605]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630607]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630609]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630610] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630691] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630693] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630694] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630695] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630697]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630698]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630700]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630702]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630704]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630707]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630709]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630710] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630764] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630766] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630767] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630767] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630769]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630771]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630773]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630775]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630777]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630779]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630781]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630783] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630838] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630840] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630841] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630842] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630844]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630846]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630847]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630849]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630852]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630854]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630856]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630857] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630994] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630996] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630997] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630998] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.630999]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631001]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631003]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631005]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631007]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631010]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631011]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631013] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631034] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631035] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631037] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631037] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631039]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631041]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631043]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631045]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631047]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631049]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631051]  [<ffffffff804f0446>] rest_init+0x66/0x70
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631052] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631072] bad: scheduling from the idle thread!
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631074] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631075] 
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631076] Call Trace:
Nov 13 07:45:51 coldwater-laptop kernel: [43357.631078]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40

---

### Post by CatKiller on 2008-11-14
> **gruntlips_ said:**
> When I do baobab / from the command line the program lists my root and home directory as 100% full, despite the fact that none of the subdirectories are anywhere near this mark.

Baobab lists subdirectories as a percentage of *usage*, not as a percentage of *total hard drive space*, so it will always add up to 100%. A lot of people seem to get confused on this point.

Also, if you put [CODE] tags around a huge stream of text it makes it much easier to read.

---

### Post by gruntlips_ on 2008-11-14
Thanks CatKiller, I was confused about how baobab expresses disk usage.  I didn't know about the existence of code tags until I read your post but I will use them in the future.

- Chris

---

