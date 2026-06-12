---
title: "Unable to start apcupsd on Kubuntu (Yakkety)"
date: 2016-11-09
forum: Hardware
---

### Post by bourne.aga1n on 2016-11-09
Hi,

I am trying [k]Ubuntu for the first time, and am loving it.

Everything works very nicely, except that I unable to get apcupsd up. I have a pretty snazzy BAK700Y USB (Powerchute) UPS that I would dearly like to shut down the system in case of power failure.

apcupsd has been installed.

1) /etc/apcupsd/apcupsd.conf has been modified to suit my 700Y APC UPS (USB).

2) apcupsd is enabled.

cat /etc/default/apcupsd 
# Defaults for apcupsd initscript

# Apcupsd-devel internal configuration
APCACCESS=/sbin/apcaccess
ISCONFIGURED=YES

3) apctest works fine

4) '/etc/init.d/apcupsd restart' gets me :
[ ok ] Restarting apcupsd (via systemctl): apcupsd.service.

5) But there is no apcupsd service process anywhere :

ps -ef | grep apc
root      4245  1766  0 21:08 pts/1    00:00:00 grep apc

5) apcaccess gets me connection refused (despite the fact that NIS server is ON in apcupsd.conf) :

apcaccess 
Error contacting apcupsd @ 127.0.0.1:3551: Connection refused

Can someone please help me get apcupsd up and running ? Thanks for any help.
Manish Jain

---

