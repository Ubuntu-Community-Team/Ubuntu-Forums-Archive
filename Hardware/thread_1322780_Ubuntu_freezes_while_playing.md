---
title: "Ubuntu freezes while playing"
date: 2009-11-11
forum: Hardware
---

### Post by slovy88 on 2009-11-11
Need help guys, my ubuntu freezes and turns to black screen randomly while playing games such as Urban terror or CS source.
firstly i thought it could be caused by overheating but I doubt it beacuse it sometimes happens in the beginning of the game and sometimes it never happens. 
Using: 9.10 on a HP 6725s
Below i pasted my syslog, thought it could be useful. Thx

```
Nov 11 14:07:51 slovy88-laptop anacron[2222]: Anacron 2.3 started on 2009-11-11
Nov 11 14:07:51 slovy88-laptop anacron[2222]: Normal exit (0 jobs run)
Nov 11 14:07:51 slovy88-laptop kernel: [   62.783110] CPU0 attaching NULL sched-domain.
Nov 11 14:07:51 slovy88-laptop kernel: [   62.783117] CPU1 attaching NULL sched-domain.
Nov 11 14:07:51 slovy88-laptop kernel: [   62.796387] CPU0 attaching sched-domain:
Nov 11 14:07:51 slovy88-laptop kernel: [   62.796392]  domain 0: span 0-1 level MC
Nov 11 14:07:51 slovy88-laptop kernel: [   62.796396]   groups: 0 1
Nov 11 14:07:51 slovy88-laptop kernel: [   62.796403] CPU1 attaching sched-domain:
Nov 11 14:07:51 slovy88-laptop kernel: [   62.796405]  domain 0: span 0-1 level MC
Nov 11 14:07:51 slovy88-laptop kernel: [   62.796408]   groups: 1 0
Nov 11 14:07:56 slovy88-laptop anacron[2354]: Anacron 2.3 started on 2009-11-11
Nov 11 14:07:56 slovy88-laptop anacron[2354]: Normal exit (0 jobs run)
Nov 11 14:07:56 slovy88-laptop kernel: [   67.954733] CPU0 attaching NULL sched-domain.
Nov 11 14:07:56 slovy88-laptop kernel: [   67.954741] CPU1 attaching NULL sched-domain.
Nov 11 14:07:56 slovy88-laptop kernel: [   67.968109] CPU0 attaching sched-domain:
Nov 11 14:07:56 slovy88-laptop kernel: [   67.968115]  domain 0: span 0-1 level MC
Nov 11 14:07:56 slovy88-laptop kernel: [   67.968119]   groups: 0 1
Nov 11 14:07:56 slovy88-laptop kernel: [   67.968127] CPU1 attaching sched-domain:
Nov 11 14:07:56 slovy88-laptop kernel: [   67.968129]  domain 0: span 0-1 level MC
Nov 11 14:07:56 slovy88-laptop kernel: [   67.968132]   groups: 1 0
Nov 11 14:08:04 slovy88-laptop pulseaudio[2295]: module-x11-xsmp.c: X11 session manager not running.
Nov 11 14:08:04 slovy88-laptop pulseaudio[2295]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 11 14:08:12 slovy88-laptop NetworkManager: <debug> [1257944892.000405] periodic_update(): Roamed from BSSID 00:1F:CF:10:12:2E (jackie) to (none) ((none))
Nov 11 14:08:12 slovy88-laptop NetworkManager: Tried to set deprecated property gsm/band
Nov 11 14:08:15 slovy88-laptop NetworkManager: last message repeated 3 times
Nov 11 14:08:15 slovy88-laptop wpa_supplicant[1207]: CTRL-EVENT-SCAN-RESULTS 
Nov 11 14:08:18 slovy88-laptop NetworkManager: <debug> [1257944898.000737] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1F:CF:10:12:2E (jackie)
Nov 11 14:08:55 slovy88-laptop wpa_supplicant[1207]: CTRL-EVENT-SCAN-RESULTS 
Nov 11 14:09:01 slovy88-laptop CRON[2724]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 11 14:09:55 slovy88-laptop wpa_supplicant[1207]: CTRL-EVENT-SCAN-RESULTS 
Nov 11 14:11:12 slovy88-laptop NetworkManager: <debug> [1257945072.002581] periodic_update(): Roamed from BSSID 00:1F:CF:10:12:2E (jackie) to (none) ((none))
Nov 11 14:11:15 slovy88-laptop wpa_supplicant[1207]: CTRL-EVENT-SCAN-RESULTS 
Nov 11 14:11:18 slovy88-laptop NetworkManager: <debug> [1257945078.004926] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1F:CF:10:12:2E (jackie)

```

---

### Post by slovy88 on 2009-12-04
bump

---

