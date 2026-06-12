---
title: "Initng Bootup"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by ankitmalik on 2005-12-01
Hey

I installed INITNG and my boot time is down from 80 to 50 secs. But I think I can bring it down further. I checked out the list of daemons.

```
acpid.i           dnsmasq.i      klogd.i          rsyncd.i
agetty.i          entranced.i    mdnsd.i          samba.i
anacron.i         esound.i       mDNSResponder.i  sendmail.i
apache2.i         fakeidentd.i   metalog.i        slapd.i
apache.i          famd.i         mingetty.i       slmodemd.i
atd.i             fcron.i        mpd.i            spamd.i
athcool.i         fetchmail.i    mysql.i          splash_update.i
avahi-daemon.i    firestarter.i  nifd.i           sshd.i
avahi-dnsconfd.i  gdm.i          nscd.i           svnserve.i
bluetooth         getty.i        ntpdate.i        syslogd.i
cardmgr.i         gpm.i          ntpd.i           syslog-ng.i
cpufreqd.i        hald.i         oidentd.i        udhcpc.i
cupsd.i           hald.i~        openvpn.i        vixie-cron.i
dbus.i            hddtemp.i      portmap.i        vmware.i
dbus.i~           hpiod.i        postgres.i       wdm.i
dcron.i           hpssd.i        powernowd.i      wpa_cli.i
dhclient.i        ifplugd.i      printconf.i      wpa_supplicant.i
dhclient-old.i    instant-gdm.i  privoxy.i        xdm.i
dhcpcd.i          ivman.i        proftpd.i        xfs.i
distccd.i         kdm.i          pump.i           xinetd.i

```

Can anyone tell me what daemon perform what function so that I can remove the ones I don't need.

Oh and one more question [it sounds a bit absurd]
- I have setup automatic login for a user in GDM . So what happens is X Starts --> GDM Starts --> Automatic Login.

To save a further 2-3 seconds :P, can the procedure be cut down to

Automatic Login in CLI and then startx

if so, can anyone tell me how?

---

### Post by r0ll3r on 2005-12-01
Hi there,
booting time depends on your hardware and your needs. Only your needs can be easily changed :) Anyway, check out these files:
/etc/initng/default.runlevel
/etc/initng/system.runlevel

Use "sudo ng-update" to alter InitNG.

These files contain what services to start. So if you have too many in these files, you may start to think about, do i really need this or that?
In the InitNG install thread, they suggest to replace hotplug with coldplug. Try it.
And the last thing, on my box, initng's boot time (which is written on the screen during boot) is 16-20 seconds. Clevo notebook, Intel Celeron 1.5Ghz, 256MB RAM. Of course real boot time from powering on until starting firefox and the firefox window popping up is more (40-50 sec).

---

### Post by ankitmalik on 2005-12-02
I checked out the two files

System Runlevel states

```
system/initial
system/mountroot
system/mountfs
system/bootmisc
system/clock
system/hostname
system/modules
system/static-modules
system/hdparm
system/keymaps
system/urandom
system/consolefont
system/swap
net/lo
daemon/getty
system/makedev
system/discover
system/coldplug

```

And Default.runlevel states

```

system
daemon/dbus
daemon/hald
daemon/vixie-cron
net/eth0
system/alsasound
system/laptop-mode
daemon/syslogd
daemon/klogd
daemon/gdm

```

So what all shal I remove ? My initng boot time is 50 seconds and 1:20 mins before I can actually use the mouse cursor in KDE! So I think the 50 secs can be brought down.

BTW should I change my kernel from 386 to 686 version ? - I am running Celeron 851 Mhz ?

```
nitng's boot time (which is written on the screen during boot) 
```

Couldn't locate that.

---

### Post by r0ll3r on 2005-12-30
I cannot recommend any service to remove, because most of them are vital. Your config seems to be OK. InitNG boot time is written on the screen if you hit alt+f1 during splash screen (if you have one). I recommend upgrading to i686 kernel. But I think this boot speed is pretty ok for a celeron 850. I wouldn't say it cannot be improved, just i don't have any idea :)

---

