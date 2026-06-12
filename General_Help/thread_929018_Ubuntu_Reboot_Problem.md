---
title: "Ubuntu Reboot Problem"
date: 2008-09-24
forum: General Help
---

### Post by siddhartha_at on 2008-09-24
Hello everyone,

i still have this annoying reboot problem. (in my old system gentoo on the same machine all works well)

Shutdown (shutdown -h now) works well. Just a reboot hangs with a blank screen after the ubuntu shutdown screen (process bar ...)
The keyboard lights shut down and after, the screen goes black.
Its also not possible to change to terminal.

I read several threads. Tried kernel options like reboot=h|f|b ...

Still no change to do a proper reboot and i need this reboot to set my nvram timer settings.

Here are my last syslog messages after reboot:
Sep 24 21:14:32 *** exiting on signal 15
Sep 24 21:16:12 *** syslogd 1.5.0#1ubuntu1: restart.

I hope someone can help me.
Thanks in advance
 Michael

---
Ubuntu 8.04.1 
2.6.24-21-generic

---

### Post by siddhartha_at on 2008-09-26
Perhaps i found a hint for help.

If i start ubuntu in Recovery Mode and just goto start root terminal than the reboot command reboot successfully.

But otherwise still no success :?:

---

### Post by Sycron on 2008-09-26
It may be a hardware that has not been halted corectly. For example Everything on your computer has been halted but your sound care is still running.

---

### Post by siddhartha_at on 2008-09-26
But how can i find such hardware :confused:

Is it possible to shut down each module/hardware element separately?

---

### Post by Sycron on 2008-09-26
You can do that with ```
sudo modprobe -r name_of_the_hardware 
```

---

### Post by Gedemins on 2008-09-26
i have the same problem on intrepid ibex 8.10
when shut down or reboot is initiated, everything looks normal, but then when it seems it should shut down, the monitor goes black and nothing happens. 
can anyone help fixing this issue?

edit: "shutdown -h now" works too

---

### Post by Sycron on 2008-09-26
DO you have the latest Intrepid Ibex ? I had once this problem too. After updating everything is fine.

---

### Post by siddhartha_at on 2008-09-26
I am still working on this issue.

Perhaps following procedure is a hint for someone:
```
init 1
```
 after that i automatically run into the Ubuntu recovery menu and selected root shell typed ```
reboot
``` and the pc rebooted sucessfully.

In the root shell i looked into my installed modules ```
lsmod
``` and search the differences between normal mode and in 'init 1' mode.

The only differences i found are in the 'Used by' column.
There are some modules which are not used anymore (f.e. snd_via82xx, evdev, dvb_bt8xx, em8300)

And now i will try to manually shutdown these modules. But how is this possible?
The command ```
modprobe -r xxx
``` just exits with
```
FATAL: Module xxx is in use.
FATAL: Error running remove command for xxx
```

---

### Post by Sycron on 2008-09-26
:) if you know the module you have to modify the /**etc/init.d/halt** file :)

---

### Post by Gedemins on 2008-09-26
i've just reinstalled ubuntu (intrepid ibex, alpha6, amd64), downloaded all the update. then system needed a reboot, which it didn't complete (had to manually push reset button). 
forgot to mention (don't know if it's important) OS is installed inside windows (through wubi).

---

### Post by Sycron on 2008-09-26
Look here. [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes) 

At the shudown paragraph.

---

### Post by siddhartha_at on 2008-09-26
Still no success.:mad:

I manually removed all modules which are not used in init-1 state.
But reboot still failed.

And now the last try: Update ubuntu to 8.10.

---

### Post by Gedemins on 2008-09-26
as for my problem:
i unchecked the enable networking box, and then shut down and restart normally. and after that "reboot" worked as it should. 
another problem as network configuration somehow messed up, so i reinstalled ubuntu again, but as i figured out, i should've just manually set my network connections again.
everything works (for now..)
i didn't install updates this time so i hope reboot and shut down works after doing that.

---

### Post by Sycron on 2008-09-26
This should work out-of-the-box. Are you using Intrepid ?

---

### Post by Gedemins on 2008-09-27
ok so i finally came up with something after rebooting with system log opened, which left the screen turned on and showed command lines. 
the problem was the unmounted hard drive. now i have to unmout it before rebooting and it reboots. 
but this is a temporary solution. and i know after some time this will become annoying.

btw: should i report this as a bug?

---

### Post by Sycron on 2008-09-30
I think you can automatically unmount it in /etc/init.d/halt , and yes you are free to report is as a BUG.

---

