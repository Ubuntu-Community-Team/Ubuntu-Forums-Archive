---
title: "Randomly Unable to Open Applications"
date: 2008-09-01
forum: General Help
---

### Post by jdavis on 2008-09-01
I have a very strange, random bug on my machine, and am not sure what the cause is.

Every day or so, I'll be happily chatting away on pidgin and listening to music on amarok, and I will attempt to open up gnome-terminal. The terminal appears, only I receive a completely black box (with the window decorations around it) rather than the prompt itself, as if it's hung while loading it. The only way to remove this is to click close and force a quit.

Same with firefox, which will refuse to open up at all. The only way to fix this is to do a full reboot of the machine. CTRL+ALT+BACKSPACE will take me back to the login screen although after logging in I get a blank screen with the system's wallpaper and nothing else.

Very few applications will open at all, I can get to the system monitor, but not much else.

Anyone have any advice or anything I can try?

thanks, Jonathan

---

### Post by Kurou-san on 2008-09-01
Try logging in with Failsafe GNOME and see if it works.

---

### Post by jdavis on 2008-09-01
Worth a try, I'll have to wait until it happens again though, which could be anytime! Seems very odd, I think I am able to do a ALT+F2 and run xterm. So it appears that something which gnome-terminal and firefox both use is affected.

I can use the machine for hours on end with no issues, then all of a sudden, bam, can't open anything and have to reboot!

Is there any way I can do a debug or trace when I launch these apps through xterm?

thanks, Jonathan

---

### Post by Kurou-san on 2008-09-01
I'm not sure about debugging, but maybe you could try running
```

killall <NAME>

```
by Alt +F2. (Where <NAME> is the program you are having trouble with.

---

### Post by crazyelf on 2008-09-01
I'm having this same problem mixed with complete system hangs. But random applications freeze not just firefox, and this is a brand new install of ubuntu.

---

### Post by lswb on 2008-09-01
Take a look at your log files, in particular /var/log/syslog, and see if there are any error messages. You can check rebooting if necessary. If you are not familiar with doing this, open a terminal, type the command: less /var/log/syslog

Then you can scroll through the file. Pressing the slash / key  lets you enter a search term, try the words  panic, Oops, segfault, error etc. (try variations on the capitalization also)

I'd take a look at the log file Xorg.0.log.old also, after restarting this should be the log from the previous boot.

---

### Post by OneOfaKindDPC on 2008-09-01
I'm having the problem. The whole system stalls before loading the GUI. Firefox and system apps stall and the update manager is completely unusable. it started about three days ago. Everything was fine before then.

---

### Post by Kurou-san on 2008-09-02
OneOfaKindDPC: I'd advise you to show us your error log (look at the post above you) before we give you wrong advice.

---

### Post by jdavis on 2008-09-02
I have attached my messages from the time of the crash below:


```
Aug 31 22:55:53 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 22:59:03 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 22:59:15 jonathan last message repeated 3 times
Aug 31 23:01:47 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:02:05 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:04:33 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:07:46 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:08:14 jonathan last message repeated 2 times
Aug 31 23:11:01 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:22:41 jonathan kernel: [45344.552080] compiz.real[6231]: segfault at 02dc0187 eip 08055a6d esp bf9c73a0 error 4
Aug 31 23:24:31 jonathan syslogd 1.5.0#1ubuntu1: restart.

```

and my user.log

```
Aug 31 22:55:53 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 22:59:03 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 22:59:03 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 22:59:06 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 22:59:06 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 22:59:11 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 22:59:11 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 22:59:15 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 22:59:15 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:01:47 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 23:01:47 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:02:05 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 23:02:05 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:04:33 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 23:04:33 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:07:46 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 23:07:46 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:07:53 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 23:07:53 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:08:14 jonathan pulseaudio[6140]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Aug 31 23:08:14 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
Aug 31 23:11:01 jonathan pulseaudio[6140]: sink-input.c: Failed to create sink input: too many inputs per sink.
```

Seems to be all pulseaudio messages, and I can't help but think that Amarok might be the cause. I do have some intermittent problems where Amarok will not play any tracks and the error "XINE was unable to initialize any audio drivers" appears. Also, the problem I am reporting has yet to happen when Amarok was closed.

Jonathan

---

### Post by mssever on 2008-09-02
> **jdavis said:**
> ```
 Aug 31 23:22:41 jonathan kernel: [45344.552080] compiz.real[6231]: segfault at 02dc0187 eip 08055a6d esp bf9c73a0 error 4
```Did you notice that compiz segfaulted? Try disabling compiz and see if that changes things. The symptoms you described could certainly be caused by a compiz crash.

---

### Post by jdavis on 2008-09-02
> **mssever said:**
> Did you notice that compiz segfaulted? 

I was wondering whether that was down to the CTRL+ALT+BACKSPACE, but you never know, worth a try!

---

### Post by crazyelf on 2008-09-05
I looked in my logs and had exactly the same errors. I've had compiz turned off for the last 2 days and I'm still having the same problem.  Any other ideas?

---

