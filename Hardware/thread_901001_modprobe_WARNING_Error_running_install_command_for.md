---
title: "modprobe: WARNING: Error running install command for nvidia.... but I don't HAVE one"
date: 2008-08-26
forum: Hardware
---

### Post by malocite on 2008-08-26
Ok,

This is driving me CRAZY.  For whatever reason this machine that I have installed Mythbuntu 8.04.1 on to is shutting itself down, kind of.  The screen goes blank, and it looses its IP (can no longer ping it) or ssh to it.  I can only reboot it by holding in the power and starting it back up.

When I look at syslog I see this

modprobe: WARNING: Error running install command for nvidia

This is displayed in two consecutive lines.  The next line is my machine booting up again.

The problem is, that I am not trying to install nvidia drivers, I don't have an nvidia card, (its the integrated intel) and I am not trying to do anything like that when it crashes.  In fact, I am generally sitting back trying to watch a video when this happens (off a network drive, not a tv card, or DVD)

This appears to be a fatal error, but I cannot figure out what is causing it.

Someone PLEASE help, its driving me batty and is basically rendering this machine useless.  I have two other ubuntu machines that give me no issues... well... not this one anyway :)


I can't tell for certain but it almost looks like (when I look at a verbose boot up like everything is getting run twice...

Maybe its always like that, but I never noticed.  Also, the boot ups are inconsistent.  Sometimes it starts by loading restricted drivers, other times it skips it altogether... as if it were loading a different drive (there is only one drive in the pc)


1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19

	

Aug 25 22:46:16 mythbox02 kernel: [   49.405587] PCI: Setting latency timer of device 000$
Aug 25 22:46:16 mythbox02 kernel: [   49.405734] [drm] Initialized i915 1.6.0 20060119 on$
Aug 25 22:46:18 mythbox02 kernel: [   51.810153] wlan0: no IPv6 routers present
Aug 25 22:46:19 mythbox02 /usr/sbin/cron[5174]: (CRON) INFO (pidfile fd = 3)
Aug 25 22:46:19 mythbox02 /usr/sbin/cron[5175]: (CRON) STARTUP (fork ok)
Aug 25 22:46:19 mythbox02 /usr/sbin/cron[5175]: (CRON) INFO (Running @reboot jobs)
Aug 25 22:50:02 mythbox02 /USR/SBIN/CRON[5545]: (root) CMD ([ -x /etc/init.d/mythtv-statu$
Aug 25 22:50:23 mythbox02 ntpd[4656]: synchronized to 91.189.94.4, stratum 2
Aug 25 22:50:23 mythbox02 ntpd[4656]: kernel time sync status change 0001
Aug 25 22:50:53 mythbox02 modprobe: WARNING: Error running install command for nvidia
Aug 25 22:50:53 mythbox02 modprobe: WARNING: Error running install command for nvidia
Aug 25 23:05:22 mythbox02 syslogd 1.5.0#1ubuntu1: restart.
Aug 25 23:05:22 mythbox02 kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 25 23:05:22 mythbox02 kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-ge$
Aug 25 23:05:22 mythbox02 kernel: Symbols match kernel version 2.6.24.
Aug 25 23:05:23 mythbox02 kernel: Loaded 18898 symbols from 78 modules.
Aug 25 23:05:23 mythbox02 kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 25 23:05:23 mythbox02 kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 25 23:05:23 mythbox02 kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@$

---

### Post by IntuitiveNipple on 2008-08-26
It sounds as if the PC is trying to suspend, and getting stuck (as many do!).

I **do** know why you're seeing the "modprobe: WARNING: Error running install command for nvidia" message though. I need to explain some background first.

The modprobe command has a facility for extending its functionality with custom actions that are driver-dependent. Configuration files are installed in **/etc/modprobe.d/** and each time modprobe is executed it scans these files an acts upon them.

Some configuration entries **can cause other programs to be run**. A case in point is the Ubuntu LRM (Linux Restricted Modules). The file **/etc/modprobe.d/lrm-video**
```

install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

```
causes executable shell scripts to be executed when a module is being installed. The scripts mentioned above are in /sbin/.

Something on the system is causing modprobe to be called and it appears the "nvidia" parameter is being passed. That is causing modprobe to try to run the shell-script **/sbin/lrm-video**. I'd guess that file is either missing or doesn't have its executable bits set, or is returning an error code.

See the man-page for modprobe.conf for details:
```

$ man modprobe.conf

```

The root cause would appear to be a script or cron job running that calls modprobe and tries to initiate the nvidia install action.

---

### Post by xeth_delta on 2008-08-26
Two things, I wonder if this actually happens when it's trying to resume and for some reason is mistakenly trying to modprobe the nvidia module...

By the other hand, that is just a warning, not an error per se. In any case, check in /etc/X11/xorg.conf what driver you are using.

Given that you do not have an nVidia card, you can blacklist the module.
```
sudo gedit /etc/modprobe.d/blacklist
```
Add at the end of the file
```
blacklist nvidia
```
Hope it helps.

---

### Post by malocite on 2008-08-26
You guys are wonderful for chiming in there.

I am going to take a looky-loo for that tonight when I get home.

The question I would have though, is how did this happen in the first place.  This is a fresh mythbuntu install on a freshly formatted harddrive, where nothing's been done but the wireless config...

Any thoughts as to where this cron job came from?

Also, how can I find the list of cron jobs and see whats goin' on there.

---

### Post by hgu on 2008-08-26
The strange thing is that I also noticed this log message now on my mythtv box. I have Ubuntu 7.10, and have not done any updates for many months now. This is the new error I see in logs nothing else seems to be new, that's why I searched and hit this post. The problems I see is that myth frontend seg faults, after trying to start playing recordings. Some recordings do play other creates the seg fault, and the error on installing nvidia drivers. I have mythtv 0.20 and also internal intel graphics.

I'll try to blacklist nvidia driver and check the script. Blacklisting changes the message to not loading nvidia due to blacklisting but mythfrontend still crashes.

---

### Post by malocite on 2008-08-28
I have gone and blacklisted those items, but you also mentioned you thought my system was trying to put itself to sleep.  How do I find out if this is the case, and if it is prevent it from doing this.  This is a small form factor desktop machine, not a laptop.  It has no reason to sleep.

It is my slave

It performs at my will :)

Sleep is for chumps...

--malocite

---

