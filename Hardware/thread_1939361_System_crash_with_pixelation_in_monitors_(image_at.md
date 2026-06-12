---
title: "System crash with pixelation in monitors (image attached)"
date: 2012-03-11
forum: Hardware
---

### Post by mechgt on 2012-03-11
I periodically experience crashes in Ubuntu that look like the attached image with odd sometimes slightly flashing/flickering pixelation in red/blue.  Both of my monitors look like this when crash occurs.  Anyone have any clue what kind of crash this is and how I fix it?  CPU... Xorg... video card... memory... something I'm doing wrong...

No specific program/event triggers it.  Typically I'm at the comptuer working, but sometimes I simply return home for the day and find it in this state.  It happens two or 3 times a month, and has been happening for over a year.

System will freeze.  Music will sometimes continue to play (if already playing), or begin a short loop.  Mouse will >sometimes< still work (can see it move around the screen), sometimes not.  I can never continue interacting with the system (cannot close programs/save, etc).  All keyboard commands are ignored.  Only solution I've found is to hold power button on computer to shut it off.

System Details:
 - Dell Dimension E521, nVidia G86 GeForce 8500 GT video card, dual monitors
 - Currently running ubuntu oneiric 11.10 (although I've experienced this on previous releases as well, so it's not new)

---

### Post by Helen McCall on 2012-03-17
Check your syslog for any I/O errors.

Run through all the logfiles to see if what is causing the errors which cause the crash.

I had similar when the disk contoller on a mother board started going faulty.

---

### Post by 2F4U on 2012-03-17
You should run memtest, for example, from a liveCD. Let it run for several iterations and see if it reveals any problems. There are also special programs that test the CPU, mostly by doing numerical calculations. Overclockers use them to see if there settings are stable but they are also helpful if you just want to test the CPU.

---

### Post by mechgt on 2012-05-10
Just happened again.  Relevant syslog output below.  Anything exciting in here?
FYI, I recently upgraded to Precise, but this crash is the exact same as it's always been.

What happened:
I was on another computer (via KVM) and switched the KVM back to the Ubuntu machine (which was playing music).  I moved the mouse over to FireFox and clicked, then.... computer death.  Music went to 1 sec. loop, screen looked like above.  Held power button to recover/reset.

```

**_Syslog_**
*[COLOR="Blue"](I just switched KVM to this computer... recognizing keyboard/mouse)[/COLOR]*
May 10 22:24:49 jambi kernel: [176818.568107] usb 2-3: new low-speed USB device number 12 using ohci_hcd
May 10 22:24:49 jambi mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-3"
May 10 22:24:49 jambi mtp-probe: bus: 2, device: 12 was not an MTP device
May 10 22:24:49 jambi kernel: [176818.795024] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/input/input20
May 10 22:24:49 jambi kernel: [176818.795239] generic-usb 0003:413C:2003.000B: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-3/input0
May 10 22:24:50 jambi kernel: [176819.096062] usb 2-4: new low-speed USB device number 13 using ohci_hcd
May 10 22:24:50 jambi mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4"
May 10 22:24:50 jambi mtp-probe: bus: 2, device: 13 was not an MTP device
May 10 22:24:50 jambi kernel: [176819.333690] input: Microsoft Microsoft IntelliMouse® Optical as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input21
May 10 22:24:50 jambi kernel: [176819.333945] generic-usb 0003:045E:0039.000C: input,hidraw1: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Optical] on usb-0000:00:0b.0-4/input0

***[COLOR="Blue"](Crash Here???)[/COLOR]***
May 10 22:25:01 jambi kernel: [176830.774761] NVRM: Xid (0000:03:00): 13, 0003 00000000 00008297 00001098 00000000 00000044
May 10 22:25:03 jambi kernel: [176832.847248] sched: RT throttling activated
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 759916 bytes (4307 ms).
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: snd_pcm_dump():
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: Soft volume PCM
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: Control: PCM Playback Volume
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: min_dB: -51
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: max_dB: 0
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: resolution: 256
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c: Its setup is:
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   stream       : PLAYBACK
May 10 22:25:05 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   access       : MMAP_INTERLEAVED
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   format       : S16_LE
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   subformat    : STD
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   channels     : 2
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   rate         : 44100
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   exact rate   : 44100 (44100/1)
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   msbits       : 16
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   buffer_size  : 16384
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   period_size  : 8192
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   period_time  : 185759
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   tstamp_mode  : ENABLE
May 10 22:25:09 jambi pulseaudio[2648]: [alsa-sink] alsa-util.c:   period_step  : 1

*[COLOR="Blue"](I think this must be me rebooting...)[/COLOR]*
May 11 02:26:51 jambi kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 11 02:26:51 jambi rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="771" x-info="http://www.rsyslog.com"] start
May 11 02:26:51 jambi rsyslogd: rsyslogd's groupid changed to 102
May 11 02:26:51 jambi rsyslogd: rsyslogd's userid changed to 101
May 11 02:26:51 jambi rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 11 02:26:51 jambi kernel: [    0.000000] Initializing cgroup subsys cpuset
May 11 02:26:51 jambi kernel: [    0.000000] Initializing cgroup subsys cpu
May 11 02:26:51 jambi kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@yellow) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
May 11 02:26:51 jambi kernel: [    0.000000] Command line: root=UUID=25ac3e7f-21a2-43f7-9947-d3de3380e8c4 ro quiet splash 
May 11 02:26:51 jambi kernel: [    0.000000] KERNEL supported cpus:
May 11 02:26:51 jambi kernel: [    0.000000]   Intel GenuineIntel
May 11 02:26:51 jambi kernel: [    0.000000]   AMD AuthenticAMD
May 11 02:26:51 jambi kernel: [    0.000000]   Centaur CentaurHauls
May 11 02:26:51 jambi kernel: [    0.000000] BIOS-provided physical RAM map:
```

---

