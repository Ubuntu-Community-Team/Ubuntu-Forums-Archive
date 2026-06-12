---
title: "update : Kernel systemd critical-chain"
date: 2016-10-17
forum: Hardware
---

### Post by valereguerin on 2016-10-17
Hello,


```
freeman@freeman-Sniper-one:~$ sudo systemd-analyze critical-chain
[sudo] Mot de passe de freeman : 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @1min 52.676s
&#9492;&#9472;multi-user.target @1min 52.676s
  &#9492;&#9472;**libvirt-guests.service @1min 52.636s +39ms  :confused:**
    &#9492;&#9472;l**ibvirt-bin.service @1min 48.188s +4.410s   :confused:**
      &#9492;&#9472;network.target @1min 48.149s
        &#9492;&#9472;**NetworkManager.service @1min 47.252s +896ms  :confused:**
          &#9492;&#9472;**firewalld.service @1min 33.420s +13.795s     :confused:**
            &#9492;&#9472;dbus.service @1min 31.843s
              &#9492;&#9472;basic.target @1min 31.826s
                &#9492;&#9472;sockets.target @1min 31.826s
                  &#9492;&#9472;cups.socket @1min 31.826s
                    &#9492;&#9472;sysinit.target @1min 31.776s
                      &#9492;&#9472;**apparmor.service @6.368s +1.741s   :confused:**
                        &#9492;&#9472;local-fs.target @6.302s
                          &#9492;&#9472;run-cgmanager-fs.mount @1min 33.792s
                            &#9492;&#9472;local-fs-pre.target @4.125s
                              &#9492;&#9472;**lvm2-monitor.service @1.761s +2.363s  :confused:**
                                &#9492;&#9472;lvm2-lvmetad.service @2.552s
                                  &#9492;&#9472;system.slice @1.748s
                                    &#9492;&#9472;-.slice @1.735s 
```


16.04.1  Unity ; Gigabyte G1 Sniper i7 930 ; 8g ram ; session cairo-dock

update & upgrade..... install new kernel 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Thanks for regards,

---

### Post by deadflowr on 2016-10-18
What's the question?

---

### Post by valereguerin on 2016-10-27
2 minutes to show my login & 40s more to show my desktop....system"d" ? start a job 1mn30 for beginning.....at boot

---

