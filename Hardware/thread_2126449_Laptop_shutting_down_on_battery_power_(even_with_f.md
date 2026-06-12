---
title: "Laptop shutting down on battery power (even with full battery)"
date: 2013-03-17
forum: Hardware
---

### Post by Daniël Slenders on 2013-03-17
Hey guys

I have an Asus K52f laptop with Ubuntu 12.04 64bit installed. Since I did the upgrade to 12.04 I have a problem with my battery. Whenever I unplug my laptop, it will shut down within seconds even when the battery is still full. (It's not a problem with the battery itself, because in Windows it works perfectly.)

I already edited the settings in dconf-editor > org > gnome > settings-daemon > plugins > power > critical-battery-action to nothing and I unchecked use-time-for-policy but that didn't help.

Any ideas?

thanks,
Daniël

---

### Post by Daniël Slenders on 2013-03-30
Any ideas?

---

### Post by matt_symes on 2013-03-30
Hi

That's an odd one. 

Take a look at the log file

```
/var/log/syslog
```

Is there anything in there to suggest what may cause it ?

Kind regards

---

### Post by Daniël Slenders on 2013-03-30
Hi

Thanks for the reply!

After I unplugged the power supply, the following 3 lines were added to syslog:
> Mar 30 13:33:04 daniel-laptop kernel: [488875.694609] keyboard: can't emulate rawmode for keycode 240
Mar 30 13:33:04 daniel-laptop kernel: [488875.694624] keyboard: can't emulate rawmode for keycode 240
Mar 30 13:33:05 daniel-laptop kernel: [488876.303491] init: anacron main process (22035) killed by TERM signal

Then after about 3 minutes, my laptop powered off. In syslog, the following was added (as far as I understand, it's just the log of the reboot):
> Mar 30 13:36:36 daniel-laptop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Mar 30 13:36:36 daniel-laptop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="915" x-info="http://www.rsyslog.com"] start
Mar 30 13:36:36 daniel-laptop rsyslogd: rsyslogd's groupid changed to 103
Mar 30 13:36:36 daniel-laptop rsyslogd: rsyslogd's userid changed to 101
Mar 30 13:36:36 daniel-laptop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Mar 30 13:36:36 daniel-laptop dbus[875]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Mar 30 13:36:36 daniel-laptop polkitd[955]: started daemon version 0.104 using authority implementation `local' version `0.104'
Mar 30 13:36:36 daniel-laptop dbus[875]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: init!
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: update_system_hostname
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPluginIfupdown: management mode: unmanaged
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.5/net/eth0, iface: eth0)
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.5/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 30 13:36:36 daniel-laptop NetworkManager[905]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 30 13:36:36 daniel-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 30 13:36:36 daniel-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 30 13:36:36 daniel-laptop kernel: [    0.000000] Linux version 3.2.0-39-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 (Ubuntu 3.2.0-39.62-generic 3.2.39)
Mar 30 13:36:36 daniel-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-39-generic root=UUID=78e6ef7a-9308-4841-b08e-96dc189dcc37 ro quiet splash vt.handoff=7
...

I don't really know what I should be looking for exactly...


thanks
Daniël

---

### Post by matt_symes on 2013-03-30
Hi

Not really much in the logs then :(

Let's start by looking at what the kernel thinks of your battery and see where we can go from there.

From the terminal, please post the output of (copy and past this into the terminal)...

```

cat /sys/class/power_supply/*/{model_name,present,energy_now,energy_full,energy_full_design,capacity}
```

Just to ket you know, i have not come across this issue before that was not fixed by the method you have already tried. You are 100% sure you have done this correctly ?

Kind regards

---

### Post by Daniël Slenders on 2013-03-30
Hi

Here's the output of my battery:
> cat /sys/class/power_supply/*/{model_name,present,energy_now,energy_full,energy_full_design,capacity}
K52F-44
1
27830000
29920000
46640000
cat: /sys/class/power_supply/*/capacity: No such file or directory


I'm quite sure I changed dconf correctly. But by mentioning it, you gave me the idea to just deactivate the power plugin in dconf, so I unchecked org > gnome > settings-daemon > plugins > power > active, and after that I managed to work for about 10 minutes on battery power. Also the output of the syslog after unplugging changed to
> 
Mar 30 14:24:43 daniel-laptop kernel: [  204.516719] keyboard: can't emulate rawmode for keycode 240
Mar 30 14:24:43 daniel-laptop kernel: [  204.516735] keyboard: can't emulate rawmode for keycode 240
No more output about anacron, so maybe there's a problem?

---

### Post by matt_symes on 2013-03-30
Hi

> **Daniël Slenders said:**
> Hi

Here's the output of my battery:

Your battery looks alright. It's lost some capacity from design but is still useable.

> 
I'm quite sure I changed dconf correctly. But by mentioning it, you gave me the idea to just deactivate the power plugin in dconf, so I unchecked org > gnome > settings-daemon > plugins > power > active, and after that I managed to work for about 10 minutes on battery power.

Now this is interesting. Good call BTW.

Can you create a new user, reboot and log into that user and see if you get the same problem when unpluging the power supply. (Ensure the power plugin is enabled)

> Also the output of the syslog after unplugging changed to

No more output about anacron, so maybe there's a problem?

I don't think anacron is the problem here. init is just killing it as part of the shutdown process from what i can see.

I think we need to investigate the power plugin.

Kind regards

---

### Post by Daniël Slenders on 2013-03-30
> Can you create a new user, reboot and log into that user and see if you  get the same problem when unpluging the power supply. (Ensure the power  plugin is enabled)
I tried this, but I still got the same problems.

I did found something else in syslog though. After unplugging, the following was added after a few minutes:
> Mar 30 21:22:55 daniel-laptop dhclient: DHCPREQUEST of 192.168.0.130 on wlan0 to 192.168.0.40 port 67
Mar 30 21:22:55 daniel-laptop dhclient: DHCPACK of 192.168.0.130 from 192.168.0.40
Mar 30 21:22:55 daniel-laptop dhclient: bound to 192.168.0.130 -- renewal in 299 seconds.
My laptop powered off after about the same time dhclient should renew (can't be sure it's the exact moment). Then again, it didn't show up in the log file I first posted here, so it might just be a coincidince...


kind regards,
Daniël

---

