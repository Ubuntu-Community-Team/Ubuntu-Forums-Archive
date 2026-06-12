---
title: "Faulty Network Adapter - Slow to Boot?"
date: 2017-07-11
forum: Hardware
---

### Post by Quarkrad on 2017-07-11
I installed Mate 16.04 on a neighbours pc and everything has been great.  Recently it has started to boot slower and slower - today it takes just over 90secs to get to the Desktop.   Changing the subject a little - my brother-in-law had a problem with his win10 pc, it kept dropping his internet connection.  I traced this down a problem with his dhcp - there is an issue with win10 where the dhcp drops out - a way round is ipconfig release/renew. So I put a batch file on his Desktop and when he loses connection he can get it back by renewing the dhcp.  On this win10 machine I installed ubuntu 16.04 in dual boot mode, so my mother-in-law could use this downstairs pc rather than her upstairs ubuntu pc. To my surprise when I launched ubuntu it took ages to boot - whereas her ubuntu pc upstairs (that is hard-wired to the downstairs router) boots normally (less than a minute).   When ubuntu finally booted there was no internet connection - I rebooted and there was a connection after another very slow boot.  The router is new so is the ethernet cable between the pc and router.  Ubuntu should not boot that slowly so I'm wondering is there is a problem with the motherboard/inbuilt network card on this downstairs pc.  Although there is this win10 issues perhaps there is also a motherboard issue (because ubuntu is so slow to boot).  Which gets me back to my neighbours machine - is his slow boot due to failing motherboard?  I have run systemd-analyze blame on the neightbours pc with this result:

```
41.606s apt-daily.service
         32.836s NetworkManager-wait-online.service
          9.599s dev-sda6.device
          9.344s lightdm.service
          7.550s ModemManager.service
          4.588s accounts-daemon.service
          4.115s grub-common.service
          3.755s NetworkManager.service
          3.030s networking.service
          2.994s speech-dispatcher.service
          2.972s systemd-logind.service
          2.894s rsyslog.service
          2.818s ufw.service
          2.478s gpu-manager.service
          1.901s apparmor.service
          1.805s teamviewerd.service
          1.746s keyboard-setup.service
          1.644s systemd-udevd.service
          1.557s systemd-tmpfiles-setup-dev.service
          1.218s colord.service
          1.190s plymouth-start.service
           993ms polkitd.service
           908ms avahi-daemon.service
```

The NetworkManager wait seems long as does the 41secs for apt-daily.service.  On my pc  NetworkManager-wait-online.service takes 7.2227secs and I do have a apt-daily.service running.  Any advice on whether my neighbours pc is hardware related or not would be much apreciated.

---

