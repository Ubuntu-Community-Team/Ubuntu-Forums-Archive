---
title: "Lcdproc-0.5.2 and imon VFD issue"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by pablo79 on 2009-09-26
Dear all my system is a mythbuntu 9.04 and my case is a Silverstone LC16M. I've installed lirc 0.8.7-CVS and lcdproc-0.5.2. The remote and the VFD work correctly (mythtv information are displayed correctly) but when I shutdown the computer instead to switch off (in the goodbye message in LCDd.conf I've inserted two " " lines) I've the LCDproc Server impressed. It seems the LCDd daemon is stoppped but without pass the goodbye message. I've try to tun manually LCDd with
```
LCDd -f -r 4
```
and to stop it whit CTRL + C but the VFD stop to ru with the LCDproc SEr impressed and the dmesg show the following errors:
```

[  154.665049] display port opened
[  156.368818] lirc_imon: send_packet: task interrupted
[  156.368832] lirc_imon: send_packet: error submitting urb(-22)
[  156.368840] lirc_imon: vfd_write: send packet failed for packet #4
[  156.368897] lirc_imon: send_packet: error submitting urb(-22)
[  156.568034] lirc_imon: vfd_write: send packet failed for packet #0
[  156.568057] display port closed

```

I think the problem is linked to these errors but how to solve thrm.

Ah, before to compile the lirc module I've modified lirc_imon.c adding this two line in the send_packet function:
```

set_current_state(TASK_INTERRUPTIBLE);
schedule_timeout(50);

```

Without these 2 lines the VFD works but with blinking pixel.

The VFD is always powered on in this case and so is not so fine to have the LCDproc on the VFD when the pc is off.

Thank you all in advance,
Paolo

---

### Post by pablo79 on 2009-09-29
I've had also tried to repeat to start and stop the LCDd daemon and sometimes it closed correctly. When it happend the dmesg showed only
```

[ 3234.536831] display port opened
[ 3241.716043] display port closed

```

It seems something linked to the lirc_imon driver that doesn't work in the right way.

Someone as a suggestion on how proceed?

Thank you,
  Pablo

---

### Post by ezacon on 2009-12-21
I also have same issue.
Have you resolved it?
thanks

---

### Post by Termo on 2010-11-03
I have the imon 15c2:ffdc VFD, and have a similar issue on Ubuntu 10.04

syslog:

```
display port opened
lirc_imon: send_packet: task interrupted
lirc_imon: send_packet: error submitting urb(-22)
lirc_imon: vfd_write: send packet failed for packet #0
display port closed
```

Any ideas to what is going on, and what *urb(-22)* means??

---

