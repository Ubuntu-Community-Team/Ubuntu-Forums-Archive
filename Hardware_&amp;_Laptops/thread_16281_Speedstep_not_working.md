---
title: "Speedstep not working?"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by psyko-lefse on 2005-02-20
I have just installed Ubuntu on my laptop. Its my first linux distro, and I love it exept for one major problem, my CPU runs on 1.7GHz constantly.
It seems like the speedstep technology dosent work at all  ](*,) 

Any good tips?

Specs:
-1557 ASL
-Pentium M dothan 1.7GHz

---

### Post by GilGalad on 2005-02-20
Have you installed the powernowd package and is it running?

---

### Post by psyko-lefse on 2005-02-20
[QUOTE=GilGalad]Have you installed the powernowd package and is it running?[/QUOTE]
 No, I havent. Im not using my computer rigth now :D
Will powernowd solve the problem?

---

### Post by GilGalad on 2005-02-20
Well, yes you need some daemon running which manages the cpu scaling. Powernowd is one of them and it is supported by Ubuntu (i.e., it is in the main repository).

---

### Post by ember on 2005-02-20
Additionally look that you modprobe something like speedstep_centrino and put it into your /etc/modules-file - I think that's necessary for a working setup (maybe a little different name for the module - I remeber it only from another thread here, as I do not own a centrino-machine)

---

### Post by psyko-lefse on 2005-02-21
Powernowd was installed, but here is the error i get when trying to run it:

> morten@morten:~ $ sudo powernowd
Password:
powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
couldn't open govn's file for writing: No such file or directory
Couldn't get per-cpu data: Illegal seek
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]


Need help with peforming the "make-sures"....
BTW, i'm a complete noob :mrgreen:

---

### Post by GilGalad on 2005-02-21
Try this:

sudo modprobe cpufreq_userspace
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe speedstep_centrino
sudo invoke-rc.d powernowd restart

Also do

ls /sys/devices/system/cpu/cpu0/cpufreq/

and check that there is something there (im my case):

affected_cpus     scaling_available_frequencies  scaling_governor
cpuinfo_cur_freq  scaling_available_governors    scaling_max_freq
cpuinfo_max_freq  scaling_cur_freq               scaling_min_freq
cpuinfo_min_freq  scaling_driver                 scaling_setspeed

Report back the errors.

---

### Post by psyko-lefse on 2005-02-21
> morten@morten:~ $ sudo modprobe cpufreq_userspace
morten@morten:~ $ sudo modprobe cpufreq_ondemand
FATAL: Module cpufreq_ondemand not found.
morten@morten:~ $ sudo modprobe cpufreq_powersave
morten@morten:~ $ sudo modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.8.1-3-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
morten@morten:~ $ sudo invoke-rc.d powernowd restart
 * Stopping powernowd:                                                   [ ok ]
powernowd.
morten@morten:~ $ ls /sys/devices/system/cpu/cpu0/cpufreq/
ls: /sys/devices/system/cpu/cpu0/cpufreq/: No such file or folder
morten@morten:~ $

Help....

---

### Post by GilGalad on 2005-02-21
What linux version are you using (uname -r). Not sure if 2.6.8 has support for Dothan. Just checked and 2.6.10 do has.

Also can you post the output of 'dmesg'.

---

### Post by psyko-lefse on 2005-02-21
> psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
mtrr: base(0xd8000000) is not aligned on a size(0x3e00000) boundary
[fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[fglrx] free  AGP = 256126976
[fglrx] max   AGP = 256126976
[fglrx] free  LFB = 45072384
[fglrx] max   LFB = 45072384
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 65536
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
speedstep-centrino: found unsupported CPU with Enhanced SpeedStep: send /proc/cpuinfo to Jeremy Fitzhardinge <jeremy@goop.org>

Running 2.6.8.1-3-386
How do i update to 2.6.10, if I have to?

---

### Post by GilGalad on 2005-02-21
Is that all the output from dmesg? Should be much larger.

Anyway, kernel 2.6.8 does not seem to have support for dothan processors, I think they were included around 2.6.10.

You'll need to upgrade to the 2.6.10 kernel in Hoary. To do so add the following lines to your /etc/apt/sources.list

```

deb http://archive.ubuntu.com/ubuntu/ hoary main restricted

```

Run synaptic, click on reload and search for the linux-image-2.6.10-3-686. 
Are you using a nvidia graphics card?

---

### Post by psyko-lefse on 2005-02-21
No, i'm using a R9600M card.
Will try upgrading to 2.6.10 now....

edit: the output from dmesg was much larger, but it was only repeates of the touchpad-error...

---

### Post by psyko-lefse on 2005-02-21
2.6.10 is now installed, and checks back fine using uname-r
> 2.6.10-3-686

But the fan still blows like cracy, now what?

---

### Post by GilGalad on 2005-02-21
powernowd should be running. Try "sudo invoke-rc.d powernowd restart" or the modprobe commands I wrote above. If that does not work I am running out of ideas.

---

### Post by psyko-lefse on 2005-02-21
> morten@morten:~ $ sudo modprobe cpufreq_userspace
morten@morten:~ $ sudo modprobe cpufreq_ondemand
morten@morten:~ $ sudo modprobe cpufreq_powersave
morten@morten:~ $ sudo modprobe speedstep_centrino
morten@morten:~ $ sudo invoke-rc.d powernowd restart
 * Stopping powernowd:                                                   [ ok ]
powernowd.
morten@morten:~ $ sudo ls /sys/devices/system/cpu/cpu0/cpufreq/
affected_cpus     scaling_available_frequencies  scaling_governor
cpuinfo_cur_freq  scaling_available_governors    scaling_max_freq
cpuinfo_max_freq  scaling_cur_freq               scaling_min_freq
cpuinfo_min_freq  scaling_driver                 scaling_setspeed

Looks like everythings working now, and I havent heard the fan in a while either :D
Is there a program for linux wich measures the freq. the CPU is running at, just to be sure?

---

### Post by psyko-lefse on 2005-02-21
Well, we move from one problem to another :D

My display drivers dosent work with the new kernel. I had way over 50FPS on the ant-screensaver before i Installed the new kernel, now I have 5FPS ](*,) 

Any good tips before I make a new thread?

driver:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by GilGalad on 2005-02-21
Oh sure. I am more used to command line utils so...

1. You can type 'cat /proc/cpuinfo'. There is a lot of information there, you can find your actual frequency under "cpu MHz".

2. 'sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq' gives your current freq. in Hz.

3. Go to the panel, right button -> 'Add to panel' -> scroll to 'CPU Frequency Scaling Monitor'. -> Add.

4. If you ever install gDesklets there are some nice utilities to show your cpu info as well.

---

### Post by GilGalad on 2005-02-21
Try installing linux-restricted-modules-2.6.10-3-686 from hoary restricted (you already add this repository when you modified sources.list). Be careful there if synaptics tells you that a lot of other packages also need to be upgraded.

---

### Post by trygvebw on 2005-02-21
[QUOTE=psyko-lefse]Well, we move from one problem to another :D

My display drivers dosent work with the new kernel. I had way over 50FPS on the ant-screensaver before i Installed the new kernel, now I have 5FPS ](*,) 

Any good tips before I make a new thread?

driver:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)[/QUOTE]
 To make the drivers work again, you have to install the linux-restricted-modules for your current kernel in Synaptic.

---

### Post by psyko-lefse on 2005-02-21
[QUOTE=GilGalad]Try installing linux-restricted-modules-2.6.10-3-686 from hoary restricted (you already add this repository when you modified sources.list). Be careful there if synaptics tells you that a lot of other packages also need to be upgraded.[/QUOTE]

Its already installed...

---

### Post by GilGalad on 2005-02-21
Never had an ATI myself.  Have you tried reading [http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567)

---

### Post by psyko-lefse on 2005-02-21
Guess what? The problems are back   ](*,) 
Just installed a fresh copy of ubuntu. The first thing I did was to update the kernel to 2.6.10 (Hoary). Then I installed the fglrx-driver. Speedstep should work now, but it didn't.

> morten@morten:~ $ sudo modprobe cpufreq_userspace
morten@morten:~ $ sudo modprobe cpufreq_ondemand
morten@morten:~ $ sudo modprobe cpufreq_powersave
morten@morten:~ $ sudo modprobe speedstep_centrino
morten@morten:~ $ sudo invoke-rc.d powernowd restart
* Stopping powernowd: [ ok ]
powernowd.
morten@morten:~ $ sudo ls /sys/devices/system/cpu/cpu0/cpufreq/
affected_cpus scaling_available_frequencies scaling_governor
cpuinfo_cur_freq scaling_available_governors scaling_max_freq
cpuinfo_max_freq scaling_cur_freq scaling_min_freq
cpuinfo_min_freq scaling_driver scaling_setspeed



> morten@morten:~ $ sudo powernowd
powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
powernowd:   cpu0: 600Mhz - 1700Mhz


Everything appears to be allright, but the freq. is stuck at 1.7GHz.
Help?

---

### Post by psyko-lefse on 2005-02-21
Problem solved...

---

### Post by psyko-lefse on 2005-02-21
Hmm, speedstep is working properly, but I have to run this command after every reboot to activate it:
$ sudo modprobe speedstep_centrino

How to make it permanent?

---

### Post by GilGalad on 2005-02-22
[QUOTE=psyko-lefse]Hmm, speedstep is working properly, but I have to run this command after every reboot to activate it:
$ sudo modprobe speedstep_centrino

How to make it permanent?[/QUOTE]
 Add it to /etc/modules

---

### Post by psyko-lefse on 2005-02-22
Finally, speedstep is working as it should :D
Here's how I did it:
-first I installed Ubuntu, and updatet the kernel to 2.6.10-686.
-then I added "speedstep_centrino" and "powernowd" to the /etc/modules list.

I want to thank everybody for their help, espesially GilGalad   :wink: 

Thank you!

---

