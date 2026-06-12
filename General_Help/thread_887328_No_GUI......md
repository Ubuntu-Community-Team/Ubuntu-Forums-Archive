---
title: "No GUI....."
date: 2008-08-12
forum: General Help
---

### Post by Chris_Foster on 2008-08-12
Hi,

I'm running kubuntu 8.10, with kde3.5 for my desktop.
I recently got a new computer with reasonably good speed, and I believe it's an Ext3 journaling file system. I was just doing my stuff (can't recall exactly), and I wondered what the button below the power button did. It looked like an eject sign on it, so I thought maybe it was for the CD drive. I pressed it, and the computer shuts down without warning. I learnt later in the BIOS, that the computer is supposed to shutdown with out the 4 second wait if a power button is pressed. But again I'm not sure if that button was a power button.

Now, when I start the computer, it searches for a hibernation image, doesn't find one, then goes to a tty login prompt.

I can login and type "sudo kdm" to start the GUI back-up, but its very annoying to do this every time I start the computer. The rest of my family would not be too happy with it, as they are not into the tech part of computers.

There was no obvious data loss, but I didn't do a very in depth search. Everything else appears to run fine.

I want to ask that could ubuntu not known what to do with that button and caused a fatal error? Or was that a power button after all? Also, what can I do to fix this issue?

Any help would be much appreciated.

-Chris Foster

---

### Post by Chris_Foster on 2008-08-12
Also, I apologize ahead of time if this is in the wrong category. It was difficult for me to decide which one because I don't know much about the problem.

-Chris Foster

---

### Post by Crafty Kisses on 2008-08-12
> **Chris_Foster said:**
> Also, I apologize ahead of time if this is in the wrong category. It was difficult for me to decide which one because I don't know much about the problem.

-Chris Foster

Have you tried reconfiguring X?

---

### Post by Chris_Foster on 2008-08-12
Thanks for answering,

I tried a command that I thought re-configured X, I'm not sure if it was the correct command.
What command would you reccomend, and can I run this wile X is running?

I have some more information that might be helpful. The computer gets past the kubuntu loading screen were the bar gets bigger, but then goes to a terminal just before it should load kdm. I was trying a new kdm theme, but I just switched back to a defult one and It made no difference.

---

### Post by Crafty Kisses on 2008-08-12
Try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Chris_Foster on 2008-08-12
I ran this wile the X server was running and I was logged in, then I restarted and there was no difference.

---

### Post by Crafty Kisses on 2008-08-12
> **Chris_Foster said:**
> I ran this wile the X server was running and I was logged in, then I restarted and there was no difference.

What are your system specs?

---

### Post by Chris_Foster on 2008-08-12
```

Chris@Uplink:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping        : 9
cpu MHz         : 2612.613
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5230.21
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping        : 9
cpu MHz         : 2612.613
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5225.51
clflush size    : 64

Chris@Uplink:~$ cat /proc/meminfo
MemTotal:      2043176 kB
MemFree:       1282144 kB
Buffers:         15416 kB
Cached:         443032 kB
SwapCached:          0 kB
Active:         343512 kB
Inactive:       289848 kB
HighTotal:     1146816 kB
HighFree:       530468 kB
LowTotal:       896360 kB
LowFree:        751676 kB
SwapTotal:      979956 kB
SwapFree:       979956 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:      174912 kB
Mapped:          68360 kB
Slab:            30160 kB
SReclaimable:    21148 kB
SUnreclaim:       9012 kB
PageTables:       2772 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2001544 kB
Committed_AS:   497644 kB
VmallocTotal:   114680 kB
VmallocUsed:      6516 kB
VmallocChunk:   107636 kB
Chris@Uplink:~$   

```

Is that what you meant?
I don't know how to find other system specs...

---

### Post by Chris_Foster on 2008-08-12
The Xserver re-set command only asked me questions about my keyboard, is that normal?

---

### Post by Crafty Kisses on 2008-08-13
> **Chris_Foster said:**
> The Xserver re-set command only asked me questions about my keyboard, is that normal?

It should ask you a lot more questions, like monitor, graphics card and what not.

---

### Post by Chris_Foster on 2008-08-14
No, I tried it without the kdm started and the same thing...
Heres the questions it asks me (in order):

Frame buffering
Autodetect keyboard
XKB ruleset
Keyboard model
Keyboard Varient
Keyboard options

and then it exits....

Any ideas?

And thanks for you help so far.

---

### Post by angry_johnnie on 2008-08-14
> **Chris_Foster said:**
> 
Heres the questions it asks me (in order):

Frame buffering
Autodetect keyboard
XKB ruleset
Keyboard model
Keyboard Varient
Keyboard options


:-) That's all it does now... reconfiguring xserver used to be the way to go, but for some reason somebody thought it wasn't all that hot any more... go figure!

Anyway, you could try:

```
sudo dpkg-reconfigure kdm
```

and see if it works.

I think it should start automatically, but if it doesn't, just do

```
sudo /etc/init.d/kdm start
```

Somewhere in kcontrol there should be an option to enable/disable system services (I'm not in kde right now, but i'm pretty sure it's there).  Try to find it, and make sure kdm is enabled.

---

### Post by Chris_Foster on 2008-08-14
The reconfigure command for kdm worked!

It even got my kdm theme I had been trying to get working show up.

Thanks jonhhie!

---

