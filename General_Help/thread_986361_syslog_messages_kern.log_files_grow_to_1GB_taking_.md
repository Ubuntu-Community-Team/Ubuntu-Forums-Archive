---
title: "syslog messages kern.log files grow to 1GB taking up entire disk"
date: 2008-11-18
forum: General Help
---

### Post by sancho panza on 2008-11-18
I clean-upgraded to Intrepid last month. Over the past week or so,
I have had couple of times when the syslog, messages and kern.log
files in the /var/log folder grow to 1GB each, thereby occupying 
all available space on the root partition and destabilizing the system. I'm not able to figure
out why this is happening. Below is an excerpt from the syslog file
which is typical of the error messages that are causing the files
to grow to 1GB.

Next time this happens I am thinking of using "ps ax" to see if
I can find the process causing this.

Any ideas?

```
Nov 18 13:31:10 Computer_name kernel: [ 5432.180687]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: [ 5432.180691]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: [ 5432.180695]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: [ 5432.180698]  [<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 5432.180703]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.180707]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.180711]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.180714]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.180719]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.181311] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.181315] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: [ 5432.181317]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: [ 5432.181321]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [ 5432.181325]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: [ 5432.181329]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: [ 5432.181332]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: [ 5432.181336]  [<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 5432.181340]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.181344]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.181348]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.181352]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.181356]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.181546] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.181549] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: [ 5432.181551]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: [ 5432.181556]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [ 5432.181559]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: [ 5432.181562]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: [ 5432.181566]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: [ 5432.181570]  [<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 5432.181574]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.181578]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.181582]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.181585]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.181589]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.181778] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.181782] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: [ 5432.181784]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: [ 5432.181788]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [ 5432.181791]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: [ 5432.181795]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: [ 5432.181799]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: [ 5432.181802]  [<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 5432.181807]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.181810]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.181815]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.181818]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.181821]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.182017] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.182021] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: [ 5432.182023]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: [ 5432.182027]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [ 5432.182031]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: [ 5432.182040]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: [ 5432.182043]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: [ 5432.182055]  [<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 5432.182059]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.182063]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.182067]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.182071]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.182074]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.182264] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.182267] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: [ 5432.182269]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: [ 5432.182273]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [ 5432.182277]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: [ 5432.182280]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: [ 5432.182284]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: [ 5432.182288]  [<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 5432.182292]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.182296]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.182300]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.182303]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.182307]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.182503] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.18250gtask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <402e<task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4025etask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4035etask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4045etask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4045etask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4055<task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <40ie<task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4075etask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4075eetask+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <40.]0-7-generic #1
Nov 18 13:31:10 Computer_name kernel: <4x8]0-7-generic #1
Nov 18 13:31:10 Computer_name kernel: <4x86>/0x140
Nov 18 13:31:10 Computer_name kernel: <4601d/0x140
Nov 18 13:31:10 Computer_name kernel: <4601>/0x140
Nov 18 13:31:10 Computer_name kernel: <463b>/0x140
Nov 18 13:31:10 Computer_name kernel: <4603>/0x140
Nov 18 13:31:10 Computer_name kernel: <4603d/0x140
Nov 18 13:31:10 Computer_name kernel: <4604d/0x140
Nov 18 13:31:10 Computer_name kernel: <460b>/0x140
Nov 18 13:31:10 Computer_name kernel: <4606>/0x140
Nov 18 13:31:10 Computer_name kernel: <460b>/0x140
Nov 18 13:31:10 Computer_name kernel: <4607d/0x140
Nov 18 13:31:10 Computer_name kernel: <4608d/0x140
Nov 18 13:31:10 Computer_name kernel: <4608>/0x140
Nov 18 13:31:10 Computer_name kernel: <468b>/0x140
Nov 18 13:31:10 Computer_name kernel: <46090te_timer_broadcast+0x36/0x39 [processor]
Nov 18 13:31:10 Computer_name kernel: <0 032+]x6=.r002-]1
Nov 18 13:31:10 Computer_name kernel: a>] d<>[ 5k+[c010b/3x5 >80x
Nov 18 13:31:10 Computer_name kernel: te_timer_broadcast+0x36/0x39 [processor]
Nov 18 13:31:10 Computer_name kernel: [ 5432.200112]  [<c0153d82>] ? tick_nohz_stop_idle+0x12/0x70
Nov 18 13:31:10 Computer_name kernel: [ 5432.200116]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 5432.200121]  [<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: [ 5432.200124]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: [ 5432.200128]  =======================
Nov 18 13:31:10 Computer_name kernel: [ 5432.201442] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.201446] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: [ 5432.201448]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: [ t<c0380ff5>] ? notifier_call_chain+0x35/0x70
Nov 18 13:31:10 Computer_name kernel: i?< 122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[8<0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[4< 122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[7<0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[0<0122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[4<0122b8a>] dequ ?=20<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: +r/]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <43x62<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <45x92<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <47x32<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <48x62<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <]-]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <47x32<c03r0<7=/]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <43x/]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <44x/]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <46x72<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [0x]>b>/0x140
Nov 18 13:31:10 Computer_name kernel: <4601d/0x140
Nov 18 13:31:10 Computer_name kernel: <46010te_timer_broadcast+0x36/0x39 [processor]
Nov 18 13:31:10 Computer_name kernel: <42/]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <46=/]<c0380ff5>] ? notifier_call_chain+0x35/0x70
Nov 18 13:31:10 Computer_name kernel: <421<1122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[3<1122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[5<1122b8a>] dequeue_taskt4>122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[3<1122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[5<1122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[9< 122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[3<1122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [x=it<c0380ff5>] ? notifier_call_chain+0x35/0x70
Nov 18 13:31:10 Computer_name kernel: <461<1122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4[3< 122b8a>][6[hx]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <44x72<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <40x22<c0380ff5>] ? notifier_call_chain+0x35/0x70
Nov 18 13:31:10 Computer_name kernel: 4>122b8a>] dequeue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [ [x=it<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <43x52<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <46x/]<c014d3bb>] ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <43x12<c01028cd>] cpu_idle+0xbd/0x140
Nov 18 13:31:10 Computer_name kernel: <46]s.] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: 0ol] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: 0ol] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #102ui4/0x130
Nov 18 13:31:10 Computer_name kernel: 26 /0x130
Nov 18 13:31:10 Computer_name kernel: <4xci4/0x130+c= 4/x =1/0x130
Nov 18 13:31:10 Computer_name kernel: <4xc2d/0x130
Nov 18 13:31:10 Computer_name kernel: <4x31 >] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel:  2?>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=/cc>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=bx >] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=bx >] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel:  [b#1
Nov 18 13:31:10 Computer_name kernel: 0ca#1
Nov 18 13:31:10 Computer_name kernel: 0z #1
Nov 18 13:31:10 Computer_name kernel: 0x7#1
Nov 18 13:31:10 Computer_name kernel: <0b>#1
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: <0b3#1
Nov 18 13:31:10 Computer_name kernel: <>0ca#1
Nov 18 13:31:10 Computer_name kernel: <0b>#1
Nov 18 13:31:10 Computer_name last message repeated 4 times
Nov 18 13:31:10 Computer_name kernel: <0<4x]75 5432.236123]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <42 5432.237237]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4243road>d72 d3n.c ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4d37c ? sched_clock_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4d37c ? notifier_call_chain+0x35/0x70
Nov 18 13:31:10 Computer_name kernel: <413 0queue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4]3 0queue_task_idle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4]0r6==
Nov 18 13:31:10 Computer_name kernel: <3d>b>]>==
Nov 18 13:31:10 Computer_name kernel: [ 5432.299034] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.299037]>k[<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: :0<[<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: :0   [<f8875a43>] ? ticks_elapsed_in_us+0xb/0x4d [processor]
Nov 18 13:31:10 Computer_name kernel: <h2 deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name last message repeated 5 times
Nov 18 13:31:10 Computer_name kernel: < + deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: < + deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: 0 + deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <h2 deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: 0 2 deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: 24    W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: <4]3 0    W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: <4]3c
Nov 18 13:31:10 Computer_name kernel: 432.309685]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4 rc
Nov 18 13:31:10 Computer_name kernel: 432.310422]  [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: <4 _c m: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: <45[c m: swapper Tainted: G        W 2.6.27-7-generic #1
Nov 18 13:31:10 Computer_name kernel: <21ot+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43ud4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <434d4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: < us>t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: 34rn+>t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: <43u44t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: <43ud4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <434d4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u44t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43ud4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4i432.328183]  [<c0153d82>] ? tick_nohz_stop_idle+0x12/0lW42[t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: <43ud4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <43u4>t+0x53/0x60
Nov 18 13:31:10 Computer_name last message repeated 5 times
Nov 18 13:31:10 Computer_name kernel: <43ud4t+0x53/0x60
Nov 18 13:31:10 Computer_name kernel:  c3h  printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4es   printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4es3e printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: t13[ schhe3 [<c012112a>] deactivate_task+0x1a/0x30
Nov 18 13:31:10 Computer_name kernel: cbd03432.335421]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 263432.335708]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 293432.336028]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 223432.336316]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 253432.336591]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 283432.336865]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 203432.337055]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: s0c432.337259]  [<c0153e15>] ? tick_nohz_0x1[..337601] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.337604] Pid: 0, comm: swapper Ta0e...a.+.337974] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a...338159] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.338349] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ah..338537] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <.a.s_d8pdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: de=6dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4sk]6dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <sk=pdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <sk=[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4s0h..341656] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.342243] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ah..342719] bad: scheduling from the i.eo2ddle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: de=6dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: [+k68tiack_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: [ 54_=<1]]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel:  d5/0x39 [processor]
Nov 18 13:31:10 Computer_name kernel: <4_= <ck_2a1chg+ck_tick+0x7hgx3 ]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=252]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=8e5]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=462]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=5e5]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=5e5]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=2e5]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=u32]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=4e5]  [<c036edd3>] rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=078/0x39 [processor]
Nov 18 13:31:10 Computer_name kernel: <4_=icck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: <4_< <ck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4_=icck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: <4_=icck6a1ck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4_< cck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4_=icck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4_=icck_tick+0x7b/0xb0
Nov 18 13:31:10 Computer_name kernel: <4_=iccall_chain+0x35/0x70
Nov 18 13:31:10 Computer_name kernel: <4lkxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4sc.+.360722] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.361343] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.361995] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.362493] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ak8432.362550]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 213432.363159]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 273432.363778]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 233432.364387]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 283432.364885]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 273432.365808]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x30x1[..367530] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ac3432.367587]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 273432.367782]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 293432.367966]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 203432.368095]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 213432.368149]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 223432.368315]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 243432.368503]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 293432.368921]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 223432.369296]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 263432.369637]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 203432.370052]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 243432.370451]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 253432.370581]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 263432.370724]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 283432.370856]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 293432.370969]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: [ 2f
Nov 18 13:31:10 Computer_name kernel: +.371146] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.371251] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.371353] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a_.371467] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.371573] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.371677] bad: scheduling from the idle 10706dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle2>=from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <43t3from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4a3t9from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4a3t8from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4a3t4from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4a3t4from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4a3t1from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4aa>=from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4a3>=from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4ap6 q4q37a2.86s3t> t50u7s80=from p9 q4q3a2.99s3t> t50u4s47=from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.377038] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic p6 q4q37a2h06u6]x==7de:6>pr[dle+0x2s2+x4d5k_7>]86u]x==8de:6>pr[dle+0x2as2+x4d5k_7>65u5]x==9de:6>pr[dle+0x2as2+x4d5k_>]48u]x==9de:6>pr[dle+0x2a/0s2+x4d5k_7>e92u2]x==0de:6>pr[dle+0x2as2+x4d5k_7>e37u]x==0e:6>pr[dle+0x2a/0xs2+x4d5k_7>e81u1]x==1de:6>pr[dle+0x2a/s2+x4d5k_7>e26u6]x==1de:6>pr[dle+0x2as2+x4d5k_7>69u]x==2de:6>pr[dle+0x2s2+x4d5k_7>13u4]x==2de:6>pr[dle+0x2a/0s2+x4d5k_7>57u]x==2de:6>pr[dle+0x2a/0s2+x4d5k_7>01u]x==3de:6>pr[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name last message repeated 3 times
Nov 18 13:31:10 Computer_name kernel: <4skx[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4sk=pdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: d0e74ck_tick_=.7ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4]b]f[180
Nov 18 13:31:10 Computer_name kernel: <4<T0c180
Nov 18 13:31:10 Computer_name kernel: <4<ec3180
Nov 18 13:31:10 Computer_name last message repeated 2 times
Nov 18 13:31:10 Computer_name kernel: T0n180
Nov 18 13:31:10 Computer_name kernel: <4<ec3180
Nov 18 13:31:10 Computer_name kernel: <4=13180
Nov 18 13:31:10 Computer_name kernel: T0n180
Nov 18 13:31:10 Computer_name kernel: <4<T0n180
Nov 18 13:31:10 Computer_name kernel: <4<ec3180
Nov 18 13:31:10 Computer_name kernel: <4<T05essor]
Nov 18 13:31:10 Computer_name kernel: <4r
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <bb97ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4fe1ic406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4]3[6c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4]31ic406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4]3[6c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4]316c406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4]31ic406>] ? printk+0x1d/0x1]34=67ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedul]b]f[180
Nov 18 13:31:10 Computer_name kernel: <4<ec3180
Nov 18 13:31:10 Computer_name kernel: <4<T0oessor]
Nov 18 13:31:10 Computer_name kernel: <4r
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4b
Nov 18 13:31:10 Computer_name kernel: 17ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4fe1ic406>] ? printk+0x1d/0x1f
Nov 18 13:31:10 Computer_name kernel: <4]fx[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4sc.+.401792] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.402747] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <40.0d:dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skx[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4sk=[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skx[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4skxpdle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4s7=[dle+0x2a/0x40
Nov 18 13:31:10 Computer_name kernel: <4sc...409312] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.409371] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a.+.410047] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.a...410733] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ah..411413] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ah..412043] bad: scheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4.ak8432.412101]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 20c432.412316]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 253432.412631]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 283432.412881]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 21c432.413149]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 243432.413423]  [<c0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: 263432.413702]  [<c0153e15gd
Nov 18 13:31:10 Computer_name kernel: +.415045] bad: sched1._rest_init+0x53/0x60
Nov 18 13:31:10 Computer_name kernel: <4=>]_]
Nov 18 13:31:10 Computer_name kernel: <40=c 0
Nov 18 13:31:10 Computer_name kernel: <0=470x70
Nov 18 13:31:10 Computer_name kernel: <yu>[ 5432.416404]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: f35heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4c=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 435heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 435heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 435heduling from the2 5t5heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4c=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4cheduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 1c=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4c=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4c=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 43=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4c=heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [4c141>[ 5432.422572]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.422897]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.423219]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.423544]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.423866]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +32
Nov 18 13:31:10 Computer_name kernel: >[ 5432.424205]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.424527]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.424850]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.425185]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.425256]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.425566]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: 5=[>[ 5432.425889]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.426218]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.426538]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.426900]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.427174]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.427443]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.427717]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3[>[ 5432.428416]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.429098]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3[>[ 5432.429811] 5>i[30
Nov 18 13:31:10 Computer_name kernel: [ 5432.430512]  [<c0153dcc>] ? tick_nohz_stop_idle+0x5c/0x70
Nov 18 13:31:10 Computer_name kernel: =470
Nov 18 13:31:10 Computer_name kernel: <40=tu0
Nov 18 13:31:10 Computer_name kernel: <d3 0
Nov 18 13:31:10 Computer_name kernel: <4=470
Nov 18 13:31:10 Computer_name kernel: <1tu0
Nov 18 13:31:10 Computer_name kernel: <1tu0x70
Nov 18 13:31:10 Computer_name kernel: 4>[ 5432.436773]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: b8= >[ 5432.437741]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.438691]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: <>[ 5432.439650]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.440600]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3[>[ 5432.441548]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.442494]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.443437]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.444390]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.445347]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.446305]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.447248]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: 2=[>[ 5432.448203]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.449165]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.450127]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +=[>[ 5432.451078]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: +3
Nov 18 13:31:10 Computer_name kernel: >[ 5432.452064]  [<c012107f>] dequeue_task+0xcf/0x130
Nov 18 13:31:10 Computer_name kernel: f35heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 435heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: <4 4c5heduling from the idle thread!
Nov 18 13:31:10 Computer_name kernel: [ 5432.454151] Pid: 0, comm: swapper T4
Nov 18 13:31:10 Computer_name kernel: t8dltart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: G0_tart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: G0_ed_in_us+0xb/0x4d [processor]
Nov 18 13:31:10 Computer_name kernel: <42d:14>[ 5432.456391]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4 d:14>[ 5432.456664]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4 d:14>[ 5432.456749]  [<c037ca23>] schedule+0x4b3/0x790
Nov 18 13:31:10 Computer_name kernel: <4 ,5_0153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180
Nov 18 13:31:10 Computer_name kernel: <4 ,>10153e15>] ? tick_nohz_restart_sched_tick+0x35/0x180^C
my_name@Computer_name:/var/log$ 


```

---

### Post by sdennie on 2008-11-18
This sounds like this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285).  Until it is fixed, a possible short term solution might be: [http://ubuntuforums.org/showpost.php?p=6200061&postcount=8](http://ubuntuforums.org/showpost.php?p=6200061&postcount=8)

---

### Post by sancho panza on 2008-11-18
Yes it that bug on launchpad. Thanks.

I'll see if the workaround helps.

---

