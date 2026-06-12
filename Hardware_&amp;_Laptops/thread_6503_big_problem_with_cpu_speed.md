---
title: "big problem with cpu speed"
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by silent82 on 2004-11-29
Hello,
I have an AMD Athlon XP Mobile 2800+, I'ts real speed is ~2100 Mhz.
The problem iis that if I make a cat /proc/cpuinfo I get:
[FONT=System]
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : Mobile AMD Athlon(tm) XP 2800+
stepping        : 0
cpu MHz         : 796.312
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips        : 1572.86[/FONT]

You can see the line  "cpu MHz : 796.312". It should have shown the value 2100...

my kernel is.
uname -a
Linux ubuntu 2.6.9 #7 Mon Nov 29 01:29:41 CET 2004 i686 GNU/Linux

I tried loading the standard ubuntu kernel but I have the same problem.

ps -A
[FONT=System]  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kacpid
   24 ?        00:00:00 kblockd/0
   25 ?        00:00:00 khubd
   37 ?        00:00:00 pdflush
   38 ?        00:00:00 pdflush
   40 ?        00:00:00 aio/0
   39 ?        00:00:00 kswapd0
  627 ?        00:00:00 kseriod
  660 ?        00:00:00 reiserfs/0
  694 ?        00:00:00 udevd
 1268 ?        00:00:00 portmap
 1681 ?        00:00:00 syslogd
 1696 ?        00:00:00 named
 1780 ?        00:00:00 gdomap
 1788 ?        00:00:00 vsftpd
 1793 ?        00:00:00 xfs-xtt
 1891 ?        00:00:00 inetd
 1944 ?        00:00:00 atd
 1954 ?        00:00:00 miniserv.pl
 2049 ?        00:00:00 gdm
 2062 ?        00:00:00 gdm
 2255 ?        00:01:38 Xorg
 2543 ?        00:00:00 pccardd
 3402 ?        00:00:00 klogd
 5587 tty1     00:00:00 getty
 5588 tty2     00:00:00 getty
 5589 tty3     00:00:00 getty
 5590 tty4     00:00:00 getty
 5591 tty5     00:00:00 getty
 5592 tty6     00:00:00 getty
 5729 ?        00:00:00 x-session-manag
 5808 ?        00:00:00 ssh-agent
 5809 ?        00:00:00 ssh-agent
 5813 ?        00:00:00 dbus-daemon-1
 5816 ?        00:00:02 gconfd-2
 5825 ?        00:00:00 gnome-keyring-d
 5829 ?        00:00:00 esd
 5831 ?        00:00:00 bonobo-activati
 5834 ?        00:00:00 gnome-settings-
 5850 ?        00:00:00 xscreensaver
 5878 ?        00:00:01 gnome-smproxy
 5880 ?        00:00:10 metacity
 5883 ?        00:00:00 gnome-volume-ma
 5885 ?        00:00:01 nautilus
 5887 ?        00:00:03 gnome-panel
 5890 ?        00:00:26 gaim
 5892 ?        00:00:10 gnome-terminal
 5897 ?        00:00:00 gnome-vfs-daemo
 5905 ?        00:00:00 mapping-daemon
 5911 ?        00:00:00 gnome-pty-helpe
 5912 pts/0    00:00:00 bash
 5920 pts/1    00:00:00 bash
 5923 pts/2    00:00:00 bash
 5939 ?        00:00:07 wnck-applet
 5958 ?        00:00:00 trashapplet
 6002 ?        00:00:00 multiload-apple
 6004 ?        00:00:00 gnome-cpufreq-a
 6007 ?        00:00:00 gnome-netstatus
 6009 ?        00:00:00 wireless-applet
 6011 ?        00:00:00 notification-ar
 6014 ?        00:00:02 gnome-keyboard-
 6016 ?        00:00:04 clock-applet
 6019 ?        00:00:00 mixer_applet2
 6184 ?        00:00:00 battstat-applet
 6238 pts/3    00:00:00 bash
 6274 pts/2    00:00:00 bash
 6290 pts/2    00:00:00 ppp-on
 6291 pts/2    00:00:00 wvdial
 6292 pts/2    00:00:00 pppd
 6327 ?        00:01:31 mozilla-bin
 6403 pts/3    00:00:00 bash
 6419 ?        00:00:00 netstat <defunct>
 6541 pts/4    00:00:00 bash
 6598 pts/4    00:00:00 bash
 6804 ?        00:00:00 dbus-daemon-1
 6808 ?        00:00:00 hald
 6904 ?        00:00:00 famd
 7198 pts/3    00:00:00 ps
[/FONT]

Sorry for the long post... but i am going nuts 0_o

Thanks to all readers :-)

silent82

---

### Post by amoser on 2004-11-29
Try running the K7 Kernel, as it is compiled for AMD Duron/Athlon.  That will give your ubuntu desktop the kick you are looking for.

---

### Post by bukdor on 2004-11-29
I would've thought that, since it is a mobile processor, it would have the speedstep technology that is in Windows. Meaning that the processor's got it's own gas pedel.

Could that be a reason? The CPU itself is just running at that speed and only jumps up when it is needed?

---

### Post by silent82 on 2004-11-29
[QUOTE=amoser]Try running the K7 Kernel, as it is compiled for AMD Duron/Athlon. That will give your ubuntu desktop the kick you are looking for.[/QUOTE]

I compiled the kernel my self... and I choose Athlon/Duron processor

[QUOTE=bukdor]I would've thought that, since it is a mobile processor, it would have the speedstep technology that is in Windows. Meaning that the processor's got it's own gas pedel.

Could that be a reason? The CPU itself is just running at that speed and only jumps up when it is needed?[/QUOTE]

I am now re-compiling again the kernel with no acpi-apm-power managment stuff...
I hope it works!

I remember that when I first installed ubuntu all was fine, including cpu speed.
then I upgraded some packages from HOARY repository...

I have only GNU/Linux installed but I tried booting ubuntu live cd and it gave me the same problem.

I will now reboot with my newly compiler kernel and, it it doesn't work, i will burn a knoppix... and I will let you know!

Tanks!

silent82

Sorry for the bad English

---

### Post by silent82 on 2004-11-29
[QUOTE=bukdor]I would've thought that, since it is a mobile processor, it would have the speedstep technology that is in Windows. Meaning that the processor's got it's own gas pedel.

Could that be a reason? The CPU itself is just running at that speed and only jumps up when it is needed?[/QUOTE]
 forgot to say that i have disablen cpuspeed, apm, acpi and powernow

silent82

---

### Post by silent82 on 2004-11-29
ok... here is the point

I re-compiled the kernel how I sed, but noting good happened. Then booted knoppix with a 2.4 kernel... same thing :-( 

My immagination is turned off so I will try, during the weekend, installing a win-xp :-(

and... I'll try to find an udpate for my bios...

Hope it's not a hardware issue... 

silent82

---

### Post by silent82 on 2004-12-01
ok!
I found the problem... powernow-k7 kernel module !!!!!!!!

if I don't load the powernow-k7 module, my cpu runs at ~800Mhz ...
but if I load the module I have my cpu running at ~2.12Ghz

this is very strange... but it works...

the problem now is that I have a system that boots in text mode :-(

Hope I can fix it...

Happy Holidays To All Out There In The World!

Peace Be With You All!

silent82

---

