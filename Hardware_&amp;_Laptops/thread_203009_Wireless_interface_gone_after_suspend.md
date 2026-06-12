---
title: "Wireless interface gone after suspend"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by jostein on 2006-06-24
After suspending my laptop, the ath0 interface (my wireless card) is gone, but everything else seems fine. I can't find it with either ifconfig -a or iwconfig. Hibernation (suspend to disk) works fine. ath0 reappears if I type "ifconfig ath0" (note: "ifconfig ath0 up" or ifup ath0" does not do this! Why?). If I then try configuring ath0, i get "SIOCSIFFLAGS: Input/output error". Then it goes on trying to get an IP from DHCP, which fails with "send_packet: Network is down" for each DHCPDISCOVER.

I'm running Dapper (i386).

Some of the settings in /etc/default/acpi-support:
```

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem # changing this to standby prevents the ath0 interface from failing, but it seems like the suspend is incomplete - the fan is still running...

```

I also tried adding a bunch of wireless modules (ath_pci ath_rate_sample ath_hal wlan_wep wlan) to MODULES_WHITELIST, but that made no difference. Removing all the modules manually before suspend and then inserting them again afterwards didn't help either.

I also tried the powersaved-deamon, but then i was unable to resume from suspend at all, so I didn't work on that, as I was already further with the preinstalled packages.

Any help would be greatly appreciated.

---

### Post by JohnsonMR on 2006-06-24
I too have the same problem.  I'm thinking it's related to this: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031)

---

### Post by naked on 2006-07-02
This thread: [http://ubuntuforums.org/showthread.php?t=201960](http://ubuntuforums.org/showthread.php?t=201960) might be helpful to you.  It fixed my wireless woes after suspending.

L

---

### Post by the_blue_pill on 2006-07-03
I have the same problem too. Fortunately I can just reenable the wireless from the system settings > networking but a permanent fix would be great. Please post here if you manage to find a solution.

---

