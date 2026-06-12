---
title: "Ubuntu (Heron) Totally Locked Up"
date: 2008-10-04
forum: General Help
---

### Post by cheesey_toastie on 2008-10-04
My Ubuntu desktop totally locked up a few minutes ago.  Even the caps lock on the keyboard was unresponsive and I had to do a hard reboot. 

Am I right in thinking this is most likely to be a hardware issue (my money is on the video card which is a piece o' junk).  The cpu useage was maxed out just before it happened (which possibly could be overheating?).  

I'm running on a fairly old PC so h/w is probably creaking a little.  

Basically are there any system logs that might shed some light on my problem?  

Steve

---

### Post by iaculallad on 2008-10-04
On your terminal, you could issue the dmesg command:

```
dmesg | tail
```

And take a look at the currently logged events.

---

### Post by cheesey_toastie on 2008-10-04
> **iaculallad said:**
> On your terminal, you could issue the dmesg command:

```
dmesg | tail
```

And take a look at the currently logged events.

Hi,

Thanks for that - that's an interesting command.  Though even leaving out the tail option I can only seem to see messages since the last boot as I had to power down and up again.

Any other ideas?

CT

---

### Post by iaculallad on 2008-10-04
On your terminal, try looking at:

> /var/log/syslog

and

> /var/log/messages.

---

### Post by cheesey_toastie on 2008-10-05
> **iaculallad said:**
> On your terminal, try looking at:



and

.


Syslog at that time 

```

Oct  4 09:16:05 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:17:01 steve-desktop /USR/SBIN/CRON[8041]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 09:20:20 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:20:25 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:26:49 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:26:54 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:33:20 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:33:25 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:37:40 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:37:45 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:39:01 steve-desktop /USR/SBIN/CRON[8605]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  4 09:42:00 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:42:05 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:46:20 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:46:25 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:48:30 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:48:35 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:50:40 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:50:45 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 09:52:50 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 09:52:55 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 10:01:30 steve-desktop NetworkManager: <info>  Supplicant state changed: 0 
Oct  4 10:01:35 steve-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct  4 10:10:55 steve-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct  4 10:10:55 steve-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct  4 10:10:55 steve-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Oct  4 10:10:55 steve-desktop kernel: Symbols match kernel version 2.6.24.
Oct  4 10:10:55 steve-desktop kernel: Loaded 16541 symbols from 85 modules.
Oct  4 10:10:55 steve-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  4 10:10:55 steve-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  4 10:10:55 steve-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)

```


And messages seems to give no clue?

```

Oct  4 09:03:49 steve-desktop -- MARK --
Oct  4 09:14:01 steve-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct  4 09:43:49 steve-desktop -- MARK --
Oct  4 10:03:49 steve-desktop -- MARK --
Oct  4 10:10:55 steve-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct  4 10:10:55 steve-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct  4 10:10:55 steve-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.

```

---

### Post by cheesey_toastie on 2008-10-06
Plugged an external HD into my computer yesterday and it locked the system again. 

I've put it down to a dodgy USB hub.  Thanks for the help!

---

