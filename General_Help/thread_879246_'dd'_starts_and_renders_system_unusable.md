---
title: "'dd' starts and renders system unusable"
date: 2008-08-03
forum: General Help
---

### Post by HyperHacker on 2008-08-03
Every so often when copying a lot of files from an SD card, I'll leave the computer for a while, and come back to find it in an unusable state:
[list][*]An instance of 'dd' has started and is using 100% CPU.
[*]I cannot start any processes such as gnome-system-monitor. Nothing will happen. (Or maybe they're just taking several minutes to start because of the high CPU usage?)
[*]I cannot press Ctrl+Alt+Fx to use a terminal, because they're all being flooded with messages:> Aug  3 17:33:43 Mercury kernel: [ 3214.798823] FAT: Filesystem panic (dev sdd1)
Aug  3 17:33:43 Mercury kernel: [ 3214.798824]     fat_get_cluster: invalid cluster chain (i_pos 19452994)(Same i_pos every time; /dev/sdd1 is the SD card.) If I press Ctrl+Alt+Delete, it beeps, but nothing happens.
[*]/var/log/syslog and /var/log/kern.log grow with these messages until /var is full.
[*]Pulling out the SD card and/or restarting X has no effect.[/list]The only way out is a hard reboot.

So there seems to be 4 problems:
1) Bad filesystem/clusters on SD card; how can I fix this or at least get the files off it before throwing it out?
2) Why is 'dd' running at all, and using 100% CPU?
3) Why, when this happens, does nothing work (i.e. starting a process, Ctrl+Alt+Delete)?
4) Isn't there a way, when the terminal is being flooded with kernel messages, to "mute" them so I can use it?

---

### Post by fsmithred on 2008-08-04
When your console is being flooded with messages, you can still type and execute commands. You just have to pay attention to what you're typing, because it won't display properly.

Another way to shut down is to hold down ctrl-alt-SysRq(Print Screen) and then type: r e i s u b
allowing a few seconds between each letter you type.

Try installing testdisk, which includes a utility to recover pictures (photorec).

---

### Post by HyperHacker on 2008-08-04
Yeah, it's kind of difficult to use the console when I can't see the commands' output. Does the SysRq trick work in Xubuntu?

Photorec doesn't seem to be working (can't find /dev/sdd or /dev/sdd1, thinks /media/KODAK is 4KB), but I'll try it with an image of the card.

[edit] Seems to have recovered everything using the image. (Fortunately just photos on the card to begin with.) Now is it possible to test the card to see if the problem is actually bad sectors that can't be fixed, or just a bad filesystem?

---

### Post by fsmithred on 2008-08-04
You could try formatting it with mkfs using the -c option to check for bad blocks, or you could run 'badblocks /dev/sdd1'. If it's ok, you should probably let the camera format it.

---

### Post by HyperHacker on 2008-08-05
OK, so if badblocks runs for a while but doesn't produce any output, does that mean it's good? Or is there a log file?

---

### Post by mcduck on 2008-08-05
> **HyperHacker said:**
> Does the SysRq trick work in Xubuntu?
It sends commands directly to the Linux kernel, so it works pretty much in every Linux system and doesn't depend on any shells or desktop environments..

---

### Post by fsmithred on 2008-08-05
Unless you specify an output file, badblocks will display on the screen. If there's no output and no error message, then there are no bad blocks.

---

### Post by HyperHacker on 2008-08-05
OK, that card checked out fine, but when I tested another one, it eventually just started spewing numbers to the console and then sure enough, dd and klogd started up again, chewing up CPU and flooding syslog. Even though I got to it before /var filled up (which seems to be when everything stops working) and killed dd, and there is no disk access going on, klogd is still running at 100% CPU and spamming messages:
> Aug  5 13:54:41 Mercury kernel: [136468.202228] attempt to access beyond end of device
Aug  5 13:54:41 Mercury kernel: [136468.202235] sdd: rw=0, want=3636897, limit=1985024So again I'm going to have to reboot, even though it's not totally unresponsive yet, as just killing klogd seems like a bad idea.

So is the system just going to effectively crash like this every time I put in a faulty memory card, then? >_>

Also, does badblocks account for the possibility that the partition table is corrupt? Thunar says about 700MB used, 300MB free on the card when it's supposed to be 2GB, so I'm guessing the partitions are fudged. Could this cause badblocks to fail, reporting blocks as bad because it can't access past the end of the partition? It's suspicious that every single block past a certain point fails, and yet almost every file on the card is intact. :-/

---

### Post by fsmithred on 2008-08-06
To check the filesystem on the sd card, make sure it's unmounted and run:
```
sudo dosfsck -v -a /dev/sdd1
```

I don't know why dd would run. Are you sure it's not a leftover from when you made the image?

---

### Post by HyperHacker on 2008-08-06
No, that one terminated normally. It actually seems to be a normal background process that goes crazy trying to keep up with the logfile flood, as I noticed it's running right now, just idling, with the command line "/bin/dd bs 1 if /proc/kmsg/ of /var/run/klogd/kmsg". I guess what's actually happening is the filesystem driver freaks out, and dd and klogd just can't keep up with the messages.

---

