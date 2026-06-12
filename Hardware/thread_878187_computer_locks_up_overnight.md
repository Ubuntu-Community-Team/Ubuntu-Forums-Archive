---
title: "computer locks up overnight"
date: 2008-08-02
forum: Hardware
---

### Post by roob85 on 2008-08-02
im running kubuntu 8.04 on my desktop with a atheros based wireless card and if i download alot(which i do...normally download using torrents with ktorrent as the app) it will lock up my computer(nothing responds..not even trying alt+sysRQ) randomly overnight....i wake up to a frozen computer a few times a week. ive looked through /var/log/messages and i dont really see anything usefull..but i will post outputs from /var/log/messages /var/log/syslog and /var/log/kern from around when the crash occurs. Ive tried using the version of madwifi that ubuntu provides. ive tried using a stable release directly from madwifi. and im currently trying there subversion version. 

EDIT: i thought Hardware & Laptops part was for general hardware issues....didnt realize it was for them not being detected or supported....the wireless card is detected and works fine.

here are the logs:

/var/log/messages:
Aug  1 21:53:36 b0ng -- MARK --
Aug  1 22:13:36 b0ng -- MARK --
Aug  1 22:33:36 b0ng -- MARK --
Aug  1 22:53:36 b0ng -- MARK --
Aug  1 23:13:36 b0ng -- MARK --
Aug  1 23:33:36 b0ng -- MARK --
Aug  1 23:53:36 b0ng -- MARK --
Aug  2 00:13:36 b0ng -- MARK --
Aug  2 00:33:36 b0ng -- MARK --
Aug  2 00:53:36 b0ng -- MARK --
Aug  2 01:13:36 b0ng -- MARK --
Aug  2 01:33:36 b0ng -- MARK --
Aug  2 01:53:36 b0ng -- MARK --
Aug  2 01:59:54 b0ng kernel: [273522.870569] rtc: lost 38 interrupts
Aug  2 02:12:42 b0ng kernel: [274288.740369] mythfilldatabas[15486]: segfault at 1f615ee8 eip 0815a8df esp b48ff01c error 6
Aug  2 02:33:36 b0ng -- MARK --
Aug  2 02:53:36 b0ng -- MARK --
Aug  2 03:13:36 b0ng -- MARK --
Aug  2 03:33:36 b0ng -- MARK --
Aug  2 03:53:36 b0ng -- MARK --
Aug  2 04:13:36 b0ng -- MARK --
Aug  2 04:33:36 b0ng -- MARK --
Aug  2 04:53:36 b0ng -- MARK --
Aug  2 05:13:36 b0ng -- MARK --
Aug  2 05:33:36 b0ng -- MARK --
Aug  2 05:53:36 b0ng -- MARK --
Aug  2 06:13:36 b0ng -- MARK --
Aug  2 06:33:36 b0ng -- MARK --
Aug  2 06:53:36 b0ng -- MARK --
Aug  2 07:13:36 b0ng -- MARK --
Aug  2 07:33:36 b0ng -- MARK --
Aug  2 07:53:36 b0ng -- MARK --
Aug  2 07:55:30 b0ng syslogd 1.5.0#1ubuntu1: restart.
Aug  2 08:13:36 b0ng -- MARK --
Aug  2 08:33:36 b0ng -- MARK --
Aug  2 08:53:36 b0ng -- MARK --
Aug  2 09:13:36 b0ng -- MARK --
Aug  2 09:33:36 b0ng -- MARK --
Aug  2 09:53:36 b0ng -- MARK --
Aug  2 10:13:36 b0ng -- MARK --
Aug  2 16:19:20 b0ng syslogd 1.5.0#1ubuntu1: restart.

on this syslog...there is ALOT of garbage about vmware...but from my googling its not related..
/var/log/syslog:

Aug  2 10:15:24 b0ng kernel: [303186.240872] /dev/vmmon[14496]: host clock rate change request 83 -> 87
Aug  2 10:15:29 b0ng kernel: [303191.280938] /dev/vmmon[14496]: host clock rate change request 87 -> 89
Aug  2 10:15:38 b0ng kernel: [303200.333138] /dev/vmmon[14496]: host clock rate change request 89 -> 98
Aug  2 10:15:49 b0ng kernel: [303211.311986] /dev/vmmon[14496]: host clock rate change request 98 -> 0
Aug  2 10:15:49 b0ng kernel: [303211.312032] /dev/vmmon[14496]: host clock rate change request 0 -> 86
Aug  2 10:15:49 b0ng kernel: [303211.515551] /dev/vmmon[14496]: host clock rate change request 86 -> 89
Aug  2 10:16:00 b0ng kernel: [303222.479136] /dev/vmmon[14496]: host clock rate change request 89 -> 0
Aug  2 10:16:00 b0ng kernel: [303222.479182] /dev/vmmon[14496]: host clock rate change request 0 -> 86
Aug  2 10:16:08 b0ng kernel: [303230.634716] /dev/vmmon[14496]: host clock rate change request 86 -> 105
Aug  2 10:16:19 b0ng kernel: [303241.609479] /dev/vmmon[14496]: host clock rate change request 105 -> 0
Aug  2 10:16:19 b0ng kernel: [303241.609521] /dev/vmmon[14496]: host clock rate change request 0 -> 81
Aug  2 10:16:19 b0ng kernel: [303241.713281] /dev/vmmon[14496]: host clock rate change request 81 -> 83
Aug  2 10:16:24 b0ng kernel: [303246.742090] /dev/vmmon[14496]: host clock rate change request 83 -> 87
Aug  2 10:16:28 b0ng kernel: [303250.761120] /dev/vmmon[14496]: host clock rate change request 87 -> 89
Aug  2 10:16:48 b0ng kernel: [303270.847442] /dev/vmmon[14496]: host clock rate change request 89 -> 90
Aug  2 10:16:59 b0ng kernel: [303281.820853] /dev/vmmon[14496]: host clock rate change request 90 -> 0
Aug  2 10:16:59 b0ng kernel: [303281.820887] /dev/vmmon[14496]: host clock rate change request 0 -> 81
Aug  2 10:17:00 b0ng kernel: [303281.980927] /dev/vmmon[14496]: host clock rate change request 81 -> 90
Aug  2 10:17:01 b0ng /USR/SBIN/CRON[364]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  2 10:17:08 b0ng kernel: [303290.049628] /dev/vmmon[14496]: host clock rate change request 90 -> 104
Aug  2 10:17:19 b0ng kernel: [303301.000183] /dev/vmmon[14496]: host clock rate change request 104 -> 0
Aug  2 10:17:19 b0ng kernel: [303301.000225] /dev/vmmon[14496]: host clock rate change request 0 -> 78
Aug  2 10:17:20 b0ng kernel: [303302.169582] /dev/vmmon[14496]: host clock rate change request 78 -> 81
Aug  2 10:17:23 b0ng kernel: [303305.163902] /dev/vmmon[14496]: host clock rate change request 81 -> 83
Aug  2 10:17:24 b0ng kernel: [303306.176668] /dev/vmmon[14496]: host clock rate change request 83 -> 84
Aug  2 10:17:28 b0ng kernel: [303310.223650] /dev/vmmon[14496]: host clock rate change request 84 -> 86
Aug  2 10:17:29 b0ng kernel: [303311.262336] /dev/vmmon[14496]: host clock rate change request 86 -> 89
Aug  2 10:17:38 b0ng kernel: [303320.378068] /dev/vmmon[14496]: host clock rate change request 89 -> 99
Aug  2 10:17:49 b0ng kernel: [303331.368547] /dev/vmmon[14496]: host clock rate change request 99 -> 0
Aug  2 10:17:49 b0ng kernel: [303331.368592] /dev/vmmon[14496]: host clock rate change request 0 -> 86
Aug  2 10:17:58 b0ng kernel: [303340.598386] /dev/vmmon[14496]: host clock rate change request 86 -> 95
Aug  2 10:18:08 b0ng kernel: [303350.702463] /dev/vmmon[14496]: host clock rate change request 95 -> 98
Aug  2 16:19:20 b0ng syslogd 1.5.0#1ubuntu1: restart.


/var/log/kern.log:
Aug  2 10:14:28 b0ng kernel: [303130.609475] /dev/vmmon[14496]: host clock rate change request 86 -> 93
Aug  2 10:14:38 b0ng kernel: [303140.702323] /dev/vmmon[14496]: host clock rate change request 93 -> 107
Aug  2 10:14:49 b0ng kernel: [303151.665870] /dev/vmmon[14496]: host clock rate change request 107 -> 0
Aug  2 10:14:49 b0ng kernel: [303151.665916] /dev/vmmon[14496]: host clock rate change request 0 -> 93
Aug  2 10:14:57 b0ng kernel: [303159.947423] /dev/vmmon[14496]: host clock rate change request 93 -> 95
Aug  2 10:15:18 b0ng kernel: [303181.060376] /dev/vmmon[14496]: host clock rate change request 95 -> 0
Aug  2 10:15:18 b0ng kernel: [303181.060399] /dev/vmmon[14496]: host clock rate change request 0 -> 83
Aug  2 10:15:24 b0ng kernel: [303186.240872] /dev/vmmon[14496]: host clock rate change request 83 -> 87
Aug  2 10:15:29 b0ng kernel: [303191.280938] /dev/vmmon[14496]: host clock rate change request 87 -> 89
Aug  2 10:15:38 b0ng kernel: [303200.333138] /dev/vmmon[14496]: host clock rate change request 89 -> 98
Aug  2 10:15:49 b0ng kernel: [303211.311986] /dev/vmmon[14496]: host clock rate change request 98 -> 0
Aug  2 10:15:49 b0ng kernel: [303211.312032] /dev/vmmon[14496]: host clock rate change request 0 -> 86
Aug  2 10:15:49 b0ng kernel: [303211.515551] /dev/vmmon[14496]: host clock rate change request 86 -> 89
Aug  2 10:16:00 b0ng kernel: [303222.479136] /dev/vmmon[14496]: host clock rate change request 89 -> 0
Aug  2 10:16:00 b0ng kernel: [303222.479182] /dev/vmmon[14496]: host clock rate change request 0 -> 86
Aug  2 10:16:08 b0ng kernel: [303230.634716] /dev/vmmon[14496]: host clock rate change request 86 -> 105
Aug  2 10:16:19 b0ng kernel: [303241.609479] /dev/vmmon[14496]: host clock rate change request 105 -> 0
Aug  2 10:16:19 b0ng kernel: [303241.609521] /dev/vmmon[14496]: host clock rate change request 0 -> 81
Aug  2 10:16:19 b0ng kernel: [303241.713281] /dev/vmmon[14496]: host clock rate change request 81 -> 83
Aug  2 10:16:24 b0ng kernel: [303246.742090] /dev/vmmon[14496]: host clock rate change request 83 -> 87
Aug  2 10:16:28 b0ng kernel: [303250.761120] /dev/vmmon[14496]: host clock rate change request 87 -> 89
Aug  2 10:16:48 b0ng kernel: [303270.847442] /dev/vmmon[14496]: host clock rate change request 89 -> 90
Aug  2 10:16:59 b0ng kernel: [303281.820853] /dev/vmmon[14496]: host clock rate change request 90 -> 0
Aug  2 10:16:59 b0ng kernel: [303281.820887] /dev/vmmon[14496]: host clock rate change request 0 -> 81
Aug  2 10:17:00 b0ng kernel: [303281.980927] /dev/vmmon[14496]: host clock rate change request 81 -> 90
Aug  2 10:17:08 b0ng kernel: [303290.049628] /dev/vmmon[14496]: host clock rate change request 90 -> 104
Aug  2 10:17:19 b0ng kernel: [303301.000183] /dev/vmmon[14496]: host clock rate change request 104 -> 0
Aug  2 10:17:19 b0ng kernel: [303301.000225] /dev/vmmon[14496]: host clock rate change request 0 -> 78
Aug  2 10:17:20 b0ng kernel: [303302.169582] /dev/vmmon[14496]: host clock rate change request 78 -> 81
Aug  2 10:17:23 b0ng kernel: [303305.163902] /dev/vmmon[14496]: host clock rate change request 81 -> 83
Aug  2 10:17:24 b0ng kernel: [303306.176668] /dev/vmmon[14496]: host clock rate change request 83 -> 84
Aug  2 10:17:28 b0ng kernel: [303310.223650] /dev/vmmon[14496]: host clock rate change request 84 -> 86
Aug  2 10:17:29 b0ng kernel: [303311.262336] /dev/vmmon[14496]: host clock rate change request 86 -> 89
Aug  2 10:17:38 b0ng kernel: [303320.378068] /dev/vmmon[14496]: host clock rate change request 89 -> 99
Aug  2 10:17:49 b0ng kernel: [303331.368547] /dev/vmmon[14496]: host clock rate change request 99 -> 0
Aug  2 10:17:49 b0ng kernel: [303331.368592] /dev/vmmon[14496]: host clock rate change request 0 -> 86
Aug  2 10:17:58 b0ng kernel: [303340.598386] /dev/vmmon[14496]: host clock rate change request 86 -> 95
Aug  2 10:18:08 b0ng kernel: [303350.702463] /dev/vmmon[14496]: host clock rate change request 95 -> 98
Aug  2 16:19:20 b0ng kernel: Inspecting /boot/System.map-2.6.24-19-generic

---

### Post by BasiliusCarver on 2008-08-02
I read this when I was setting up my wireless and I don't know if it will help at all but I'd give it a shot if it was me. Assuming you're using the madwifi drivers.

"*Finally, the MadWifi driver will prevent you from resuming after suspend-to-ram. To fix this, edit /etc/default/acpi-support and add the ath_pci driver to the MODULES variable, like so:*"

```
# ...
MODULES="ath_pci"

# ...
```

---

### Post by roob85 on 2008-08-03
this is on my desktop system...would this still be applicable to me?

---

### Post by BasiliusCarver on 2008-08-03
probably, i think its a problem with the madwifi drivers and atheros wireless cards. yours internal?

---

### Post by roob85 on 2008-08-03
yea its a dlink pci card. ill go ahead and try this tonight see how it goes.

---

