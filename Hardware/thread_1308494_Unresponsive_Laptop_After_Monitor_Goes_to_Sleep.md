---
title: "Unresponsive Laptop After Monitor Goes to Sleep"
date: 2009-10-31
forum: Hardware
---

### Post by TubaTodd on 2009-10-31
Karmic 9.10

I have a Toshiba laptop that I use an external monitor (laptop lid stays closed) with most of the time. I have the screensaver set to go on after 5 minutes. I also have the monitor (just the monitor) set to sleep after 10 minutes. With Karmic, if I come back to my machine after the monitor has gone to sleep and click the keyboard or mouse to wake the monitor up, I get nothing. The screen is blank. I've tried ctrl+alt+backspace (which I enabled) and ctrlt+alt+f1to get some kind of response, but nothing happens. 

I can take another computer on my network and ssh into my laptop and it appears to be functioning. To recover from this problem, I reboot from the ssh session.

How do I fix this?

---

### Post by TubaTodd on 2009-10-31
Bump...

---

### Post by linuxchiq on 2009-11-01
I am experiencing exactly the same behavior with my HP desktop, Dell monitor. /var/log/messages reveals the following:

Nov  1 07:28:54 scully kernel: [39600.520048]  f6beff04 00000046 f6bcbefc c08145c0 f6bcc168 c08145c0 bcf30f1a 000023b7
Nov  1 07:28:54 scully kernel: [39600.520061]  c08145c0 c08145c0 f6bcc168 c08145c0 bcf30205 000023b7 c08145c0 f664c000
Nov  1 07:28:54 scully kernel: [39600.520072]  f6bcbed0 f691e414 f691e418 ffffffff f6beff30 c056f776 c0748e80 f691e41c
Nov  1 07:28:54 scully kernel: [39600.520084] Call Trace:
Nov  1 07:28:54 scully kernel: [39600.520096]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Nov  1 07:28:54 scully kernel: [39600.520102]  [<c056f690>] mutex_lock+0x20/0x40
Nov  1 07:28:54 scully kernel: [39600.520129]  [<f82abc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Nov  1 07:28:54 scully kernel: [39600.520136]  [<c0157a7e>] run_workqueue+0x6e/0x140
Nov  1 07:28:54 scully kernel: [39600.520150]  [<f82abbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Nov  1 07:28:54 scully kernel: [39600.520156]  [<c0157bd8>] worker_thread+0x88/0xe0
Nov  1 07:28:54 scully kernel: [39600.520161]  [<c015c280>] ? **autoremove_wake_function**+0x0/0x40
Nov  1 07:28:54 scully kernel: [39600.520165]  [<c0157b50>] ? worker_thread+0x0/0xe0
Nov  1 07:28:54 scully kernel: [39600.520170]  [<c015bf8c>] kthread+0x7c/0x90
Nov  1 07:28:54 scully kernel: [39600.520174]  [<c015bf10>] ? kthread+0x0/0x90
Nov  1 07:28:54 scully kernel: [39600.520179]  [<c0104007>] kernel_thread_helper+0x7/0x10

---

### Post by TubaTodd on 2009-11-01
That is an interesting catch. I have stopped my monitor from going to sleep so the problem hasn't happened again and I noticed that the autoremove_wake_function line is no longer found in my log files. Of course the problem isn't fixed yet. I'm just working around it for the time being.

---

### Post by fornix on 2009-11-01
Could you post the output of
```
$ lsmod | grep 8042
```

---

### Post by linuxchiq on 2009-11-01
I get no output:

root@scully:/var/log# lsmod | grep 8042
root@scully:/var/log#

---

### Post by fornix on 2009-11-01
I had a similar problem with my HP laptop. Solved it by following this thread -> [http://ubuntuforums.org/showthread.php?t=1047284]("http://ubuntuforums.org/showthread.php?t=1047284")

---

### Post by TubaTodd on 2009-11-09
Thank you for the responses. Just to clarify, only my monitor is being put to sleep. The machine itself is not in sleep or suspend. Any ideas?

---

### Post by NJC on 2009-11-25
I have identical problem on my desktop PC running Ubuntu 9.10. A bug has been filed but isn't getting any attention. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/470926](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/470926)

There is some mysterious latency too - IE if the monitor has recently blanked off, then it will desktop will resume. But if it's been sitting for hours, then it's unresponsive and I have to reboot. It's a major PITA and one that has turned me back to 9.04. I don't particularly want my monitor on 16hrs/day.

---

