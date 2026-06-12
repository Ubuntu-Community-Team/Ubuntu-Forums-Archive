---
title: "Perf Interrupt taking too long"
date: 2014-11-20
forum: Hardware
---

### Post by ds-mailbag on 2014-11-20
Ok,

Keep having a problem with the mouse cursor freezing; at the end of dmesg I find this after the event.

```
[ 1798.430468] perf interrupt took too long (2511 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2588.253279] psmouse serio1: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.

```

I can bring the mouse back to life with this bash script

```
#!/bin/sh
# restart a dead mouse
sudo rmmod psmouse
sleep 3
sudo modprobe psmouse
#EOF
```

But it continues to happen.

I pressume "perf" is a peripheral interrupt but where can I find the settings for this; can I manually change the value kernel.perf_event_max_sample_rate to stop this happening?

HARDWARE
HP Compaq dc5800 with ATI v5900 graphics

---

### Post by Doug S on 2014-11-20
Hi and welcome to Ubuntu forums:

I think it is this: perf - Performance analysis tools for Linux

If you are not running a "perf record" session, then I do not know why you would be getting the message(s). It is an innocent message anyhow and can be ignored.
The default setting for perf are:```
doug@s15:~/ubuntu-help$ [COLOR=#ff0000]cat /proc/sys/kernel/perf_event_max_sample_rate[/COLOR]
50000
doug@s15:~/ubuntu-help$ [COLOR=#ff0000]cat /proc/sys/kernel/perf_cpu_time_max_percent[/COLOR]
25
```And you can change those numbers.
I don't know what is wrong with your mouse.

Edit: Even if a "perf record" session is not in progress, a lot of the perf infrastructure still runs.

---

### Post by ds-mailbag on 2014-11-22
Hi,

Thanks for the info.

Still not sure whats going on with the mouse; remenisent of bug posted for Hardy since sometimes the cursor goes cazy round the screen and opens everything it passes over.
Just happened again - always get those two messages together when it does.

```
[ 1038.025572] perf interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2149.737996] psmouse serio1: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
```

---

### Post by Doug S on 2014-11-22
The perf interrupts are over time by 0.4% and 0.12%, and so barely. With a slightly higher CPU usage threshold, you wouldn't get the messages. They are also separated from the mouse log entries by over 13 and 18 minutes (thanks for editing in the time stamp for the second perf message posting). Interesting, but I'm not sure what to suggest.

Edit: Actually, you should try a higher CPU usage threshold, say 30%. To observe if there are still messages, but closer in time to the mouse log entry event. The thinking being that things get worse over time since boot.

Edit 2: Are you using the low latency kernel or the generic kernel?

---

### Post by ds-mailbag on 2014-11-23
Ok,

Perhaps that's my mistake for linking the two messages; whenever this occurs those are the last two messages.

This old bug report against an earlier version is close to the mark with the problem I'm experiencing.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/113733](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/113733)

```
 uname -r
3.16.0-24-generic
```

---

