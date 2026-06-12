---
title: "Lean system"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by rusi_pathan on 2005-02-27
Right now the following services are started during the boot process. I prefer a lean system and would like to know if any among these aint necessary. I have already shut cupsys and ntp-simple. Btw is fetchmail necessary for evolution to work.

sysklogd
klogd
ppp
portmap
acpid
alsa
apmd
dbus-1
fam
inetd
makedev
pcmcia
postfix
powernowd
rsync
mdadm
atd
cron
acpi-support
fetchmail
gdm
rmnologin
stop-bootlogd
vpnclient_init

And here are all the processes...

  PID %CPU    SZ   VSZ USER     COMMAND
    2  0.0     0     0 root     ksoftirq
    3  0.0     0     0 root     events/0
    4  0.0     0     0 root     khelper
    5  0.0     0     0 root     kacpid
   34  0.0     0     0 root     kblockd/
   44  0.0     0     0 root     pdflush
   45  0.0     0     0 root     pdflush
   47  0.0     0     0 root     aio/0
   46  0.0     0     0 root     kswapd0
   48  0.0     0     0 root     kpnpbios
  189  0.0     0     0 root     kseriod
  284  0.0     0     0 root     kjournal
 2132  0.0     0     0 root     khubd
 2547  0.0     0     0 root     pccardd
 2589  0.0     0     0 root     ipw2200/
 4506  0.0     0     0 stali    netstat
  359  0.0   368  1472 root     udevd
 3171  0.0   371  1484 root     inetd
 3452  0.0   371  1484 root     powernow
 3784  0.0   372  1488 root     getty
 3785  0.0   372  1488 root     getty
 3786  0.0   372  1488 root     getty
 3787  0.0   372  1488 root     getty
 3788  0.0   372  1488 root     getty
 3789  0.0   372  1488 root     getty
    1  0.0   373  1492 root     init
 3099  0.0   375  1500 root     acpid
 3270  0.0   378  1512 root     cardmgr
 3013  0.0   385  1540 root     syslogd
 3464  0.0   385  1540 root     mdadm
 2756  0.0   399  1596 daemon   portmap
 3475  0.0   417  1668 daemon   atd
 3486  0.0   434  1736 root     cron
 4238  0.0   476  1904 stali    vpnclien
 4098  0.0   484  1936 stali    dbus-dae
 3128  0.0   510  2040 message  dbus-dae
 2744  0.0   522  2088 root     dhclient
 4233  0.0   542  2168 stali    gnome-pt
 4106  0.0   554  2216 stali    gnome-ke
 3024  0.0   595  2380 root     klogd
 4534  0.0   618  2472 stali    ps
 4480  0.0   671  2684 stali    firefox
 4491  0.0   680  2720 stali    run-mozi
 3153  0.0   682  2728 stali    famd
 3371  0.0   725  2900 root     master
 3389  0.0   727  2908 postfix  pickup
 4094  0.0   730  2920 stali    ssh-agen
 3390  0.0   734  2936 postfix  qmgr
 4234  0.0   751  3004 stali    bash
 4239  0.0   852  3408 root     cvpnd
 4122  0.0   931  3724 stali    xscreens
 4240  0.0   955  3820 nobody   cvpnd
 4217  0.0  1014  4056 root     gconfd-2
 3132  0.0  1102  4408 hal      hald
 4110  0.0  1310  5240 stali    bonobo-a
 4108  0.0  1392  5568 stali    esd
 4179  0.0  1482  5928 stali    mapping-
 4146  0.0  1911  7644 stali    gnome-sm
 3576  0.0  2148  8592 root     gdm
 3586  0.0  2234  8936 root     gdm
 4100  0.1  2711 10844 stali    gconfd-2
 4148  0.1  2972 11888 stali    metacity
 4150  0.0  3667 14668 stali    gnome-vo
 4211  0.0  3717 14868 stali    notifica
 4209  0.0  3906 15624 stali    wireless
 4169  0.0  3908 15632 stali    gnome-vf
 4207  0.2  3932 15728 stali    battstat
 4160  0.0  4129 16516 stali    clock-ap
 4048  0.0  4213 16852 stali    x-sessio
 4198  0.1  4316 17264 stali    wnck-app
 4205  0.0  4510 18040 stali    mixer_ap
 4112  0.0  4656 18624 stali    gnome-se
 4154  0.0  4669 18676 stali    gnome-pa
 4164  0.0  6198 24792 stali    trashapp
 4152  0.0  8708 34832 stali    nautilus
 4232  0.1  9326 37304 stali    gnome-te
 4452  0.0 14985 59940 stali    evolutio
 4462  0.0 15016 60064 stali    evolutio
 4496  7.6 23745 94980 stali    firefox-
 3755  2.8 39715 158860 root    XFree86

Thanks in advance
Rusi

---

### Post by mdmcginn on 2005-03-29
Since I can send and receive email without Postfix, I'm leaving the service disabled. I don't know why the service is activated by default if it isn't necessary for lowly desktop users like me.  And mdadm is for RAID devices, which lowly desktop users don't own. I disabled them both. I think powernowd only works on certain laptops, but I could be wrong.

---

