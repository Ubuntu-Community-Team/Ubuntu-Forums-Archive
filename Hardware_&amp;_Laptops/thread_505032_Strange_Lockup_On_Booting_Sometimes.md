---
title: "Strange Lockup On Booting Sometimes"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by SuperAndy on 2007-07-19
Sometimes, when I boot, the booting hangs on some sections. Its usually pretty uniform for each of the two kernels i have in grub. i.e., it will lock up at a certain point in one, and a different point with the other.

If i use the failsafe boot, i get the message SOFT LOCKUP DETECTED ON CPU#0! I have made sure I am not overclocking it, and it still wouldn't work, after a good 4 tries. So i booted into vista, and sat there for 5 mintes crying.

Then, i tried linux again, and it worked. Its a bit scary though, becuase it happened before, but i put it down to a software change, as when i livedisced in and got rid of it, i was ok again. But it seems to be something a bit stranger. I put it in this forum becuase it does seem to be a hardware fault. Although its bloody strange. Any ideas?

---

### Post by SuperAndy on 2007-07-20
Well, it now freezes when i am in gnome as well...

I ran memtest on it, it passed all sections. is there any diagnostic software around for linux that will test CPU, stuff like that?

---

### Post by w4ett on 2007-07-20
Have you checked you PSU Voltages lately?  Might be getting a little flakey.  I had it happen before, replaced PSU and voila, no more  problems.   If you don't already have it installed, lm-sensors ( in Syanaptic) is a good place to start.

---

### Post by SuperAndy on 2007-07-20
believe it or not, my core voltage was dropping to 1.1v and causing a restart, but i fixed that problem. was a dodgy bios setting. but i will install and check

---

### Post by SuperAndy on 2007-07-20
yep, all my voltages seem normal:

VCore:     +1.39 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.14 V  (min =  +9.82 V, max =  +8.08 V) ALARM
AVCC:      +3.33 V  (min =  +2.48 V, max =  +2.64 V) ALARM
3VCC:      +3.33 V  (min =  +1.33 V, max =  +2.75 V) ALARM
in4:       +2.04 V  (min =  +0.78 V, max =  +1.36 V) ALARM
in5:       +1.59 V  (min =  +1.18 V, max =  +1.58 V) ALARM
in6:       +5.09 V  (min =  +4.63 V, max =  +5.25 V) 
VSB:       +3.31 V  (min =  +2.16 V, max =  +1.52 V) ALARM
VBAT:      +0.75 V  (min =  +0.35 V, max =  +2.42 V) 
in9:       +1.54 V  (min =  +0.18 V, max =  +1.22 V) ALARM

specfically the core one

---

### Post by w4ett on 2007-07-20
The only other things I can think of would be to force a fsck and see if there are any error messages, and possibly checking the xorg error log for evidence of a video driver/bus issue  (I'm more of a hardware guy than anything else)

---

### Post by SuperAndy on 2007-07-20
soorry for being n00by, but i presume i need to force this at boot. it complians its mounted

---

### Post by w4ett on 2007-07-20
Quote from : Yabbadabbadont


quote:

To force a filesystem check on next boot, simply "touch" a file called "forcefsck" in the root directory of the filesystem to be checked. Example:
Code:

sudo touch /home/forcefsck

would force the /home filesystem to be checked on the next boot.

---

### Post by SuperAndy on 2007-07-21
ah, genius!

---

### Post by SuperAndy on 2007-07-21
ok, i've done that. now when i start it *always* stops and gives the error when it mounts the file system and tries to scan the disk.

so, im a bit peeved :P but it wasn't really working anyway. can i untouch it? :P

---

### Post by SuperAndy on 2007-07-27
right, i stopped that happening. its weird though. i have done some more messing around, and seen a pattern.

if i let grub boot my default automatically after 10 seconds, then it locks up, say, x seconds after it starts. if i press enter on grub 5 seconds through the 10 second timeout, it will lock up at x+5 seconds though. as if there is some clock ticking from when i turn on my computer, or grub starts, or something.

this value of x is the same untill ubuntu succesfully boots, but then it can change. in order to get ubuntu to boot, i have to boot into vista.

this is very strange. i am thinking about trying something like lilo, is that likely to help?

---

### Post by SuperAndy on 2007-10-03
I suddenly realised it would be a good idea to post some of syslog to see if anyone could shed any light on what was going on. This first one is the last however many lines from when the computer froze just after i had logged in.

```

Oct  2 19:15:06 andy-desktop anacron[6149]: Normal exit (0 jobs run)
Oct  2 19:15:06 andy-desktop /usr/sbin/cron[6180]: (CRON) INFO (pidfile fd = 3)
Oct  2 19:15:06 andy-desktop /usr/sbin/cron[6181]: (CRON) STARTUP (fork ok)
Oct  2 19:15:06 andy-desktop /usr/sbin/cron[6181]: (CRON) INFO (Running @reboot jobs)
Oct  2 19:15:06 andy-desktop /USR/SBIN/CRON[6207]: (root) CMD (/opt/grisoft/avg7/bin/avgupdate -n --no-daemons --priority 2 --online)
Oct  2 19:15:07 andy-desktop /USR/SBIN/CRON[6206]: (root) MAIL (mailed 182 bytes of output but got status 0x0001 )
Oct  2 19:15:11 andy-desktop gdm[5154]: Restarting computer...
Oct  2 19:15:11 andy-desktop kernel: [   64.372038] mtrr: no MTRR for a0000000,8000000 found
Oct  2 19:15:12 andy-desktop init: tty4 main process (4546) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty5 main process (4547) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty2 main process (4553) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty3 main process (4554) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty1 main process (4555) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty6 main process (4556) killed by TERM signal
Oct  2 19:15:17 andy-desktop nmbd[5892]: [2007/10/02 19:15:17, 0] nmbd/nmbd.c:terminate(58) 
Oct  2 19:15:17 andy-desktop nmbd[5892]:   Got SIGTERM: going down... 
Oct  2 19:15:19 andy-desktop NetworkManager: <debug info>^I[1191348919.768015] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Oct  2 19:15:19 andy-desktop NetworkManager: <debug info>^I[1191348919.770686] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct  2 19:15:21 andy-desktop rpc.statd[5976]: Caught signal 15, un-registering and exiting.
Oct  2 19:15:21 andy-desktop mountd[5850]: Caught signal 15, un-registering and exiting.
Oct  2 19:15:21 andy-desktop kernel: [   74.004721] nfsd: last server has exited
Oct  2 19:15:21 andy-desktop kernel: [   74.004724] nfsd: unexporting all filesystems
Oct  2 19:15:21 andy-desktop kernel: [   74.005118] RPC: failed to contact portmap (errno -5).
Oct  2 19:15:21 andy-desktop exiting on signal 15
Oct  2 21:00:14 andy-desktop syslogd 1.4.1#20ubuntu4: restart.

```

Seems to be that gnome has decided its going to reboot, and just stopped responding. But it seems to be something more fundamental, as trying to reboot the x server wont work. The reason for the delay into rebooting was because i rebooted into XP. This solves the problem.

This next excerpt is from when the computer crashed the first time:

```

Oct  2 12:27:18 andy-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct  2 12:27:18 andy-desktop dhclient: DHCPACK from 192.168.1.1
Oct  2 12:27:18 andy-desktop dhclient: bound to 192.168.1.105 -- renewal in 35529 seconds.
Oct  2 12:39:01 andy-desktop /USR/SBIN/CRON[23097]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 12:59:30 andy-desktop -- MARK --
Oct  2 13:09:01 andy-desktop /USR/SBIN/CRON[24538]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 13:17:01 andy-desktop /USR/SBIN/CRON[24901]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 13:39:01 andy-desktop /USR/SBIN/CRON[25884]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 13:59:31 andy-desktop -- MARK --
Oct  2 14:09:01 andy-desktop /USR/SBIN/CRON[27330]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 14:17:01 andy-desktop /USR/SBIN/CRON[27715]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 14:39:01 andy-desktop /USR/SBIN/CRON[28749]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 14:59:32 andy-desktop -- MARK --
Oct  2 15:09:01 andy-desktop /USR/SBIN/CRON[30118]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 15:17:01 andy-desktop /USR/SBIN/CRON[30494]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 15:39:01 andy-desktop /USR/SBIN/CRON[31524]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 15:59:34 andy-desktop -- MARK --
Oct  2 16:09:01 andy-desktop /USR/SBIN/CRON[400]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 16:17:01 andy-desktop /USR/SBIN/CRON[773]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 16:39:01 andy-desktop /USR/SBIN/CRON[1758]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 16:59:35 andy-desktop -- MARK --
Oct  2 17:09:01 andy-desktop /USR/SBIN/CRON[3105]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 17:17:01 andy-desktop /USR/SBIN/CRON[3455]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 19:10:51 andy-desktop syslogd 1.4.1#20ubuntu4: restart.

```

This here is just cron stuff. I dont see anything that could cause a crash. Its as if something is happening seemingly at random, for no reason, but then makes gdm go wrong untill i switch operating system. It then works fine.

Any ideas? BIt of a mystery this is.

---

