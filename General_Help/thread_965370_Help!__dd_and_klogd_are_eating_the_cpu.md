---
title: "Help!  dd and klogd are eating the cpu"
date: 2008-10-31
forum: General Help
---

### Post by ycason on 2008-10-31
For some reason my processor runs all the time and when I check top, the dd and klogd are listed as the top 2 processes.  What could they be doing and how do I make them stop?

I get this error in the system log over and over again.

Oct 31 14:43:37 yale-laptop kernel: [  997.497147] Call Trace:
Oct 31 14:43:37 yale-laptop kernel: [  997.497153]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Oct 31 14:43:37 yale-laptop kernel: [  997.497155]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Oct 31 14:43:37 yale-laptop kernel: [  997.497157]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Oct 31 14:43:37 yale-laptop kernel: [  997.497160]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Oct 31 14:43:37 yale-laptop kernel: [  997.497163]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Oct 31 14:43:37 yale-laptop kernel: [  997.497165]  [<ffffffff804fd735>] start_secondary+0x97/0xc2
Oct 31 14:43:37 yale-laptop kernel: [  997.497167]

---

### Post by alohre on 2008-10-31
I am experiencing the same problems. with this spamming the syslog:

[74366.727181]  =======================
[74366.731329] bad: scheduling from the idle thread!
[74366.731347] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
[74366.731358]  [<c037c3f6>] ? printk+0x1d/0x1f
[74366.731379]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
[74366.731395]  [<c012107f>] dequeue_task+0xcf/0x130
[74366.731412]  [<c012112a>] deactivate_task+0x1a/0x30
[74366.731427]  [<c037ca13>] schedule+0x4b3/0x790
[74366.731442]  [<c014a72d>] ? enqueue_hrtimer+0x7d/0x130
[74366.731460]  [<c014b474>] ? hrtimer_start+0xc4/0x1c0
[74366.731477]  [<c0153f02>] ? tick_nohz_restart_sched_tick+0x122/0x180
[74366.731497]  [<c01028cd>] cpu_idle+0xbd/0x140
[74366.731511]  [<c036edc3>] rest_init+0x53/0x60
[74366.731528]  =======================

---

### Post by ycason on 2008-10-31
I think it may have fixed itself.  I ran all the latest upgrades and got the newest kernel.  It hasn't happened again since I updated.  Hopefully, that's all it will take.

:guitar:

---

### Post by Lampshade on 2008-10-31
I'm seeing the same thing.  DD and klogd are killing me.  Running 8.10 and 64 bit.  Never had this problem with 8.04.  Any idea what the cause is?  Can I just kill those processes?

---

### Post by alohre on 2008-10-31
to stop the klogd you can run 
sudo /etc/init.d/klogd stop

This will stop it from filling up your disk with logs and eating your cpu, but will not remove the problem that is causing this behaviour. This is just a workaround until the bug is fixed.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)

---

