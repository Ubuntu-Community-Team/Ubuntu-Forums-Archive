---
title: "LIRC configuration  needs to be changed after reboot"
date: 2018-09-19
forum: Hardware
---

### Post by NHerby on 2018-09-19
Hi,

For info, I have a logitech universal RC and use a Creative x-fi USB soundcard as IR receiver. OS is Kubuntu 18.04LTS.
Here is my /etc/lirc/lirc_options.conf file:
```
# These are the default options to lircd, if installed as
# /etc/lirc/lirc_options.conf. See the lircd(8) and lircmd(8)
# manpages for info on the different options.
#
# Some tools including mode2 and irw uses values such as
# driver, device, plugindir and loglevel as fallback values
# in not defined elsewhere.

[lircd]
nodaemon        = False
driver          = alsa_usb
device          = hw:CARD=2,DEV=0
output          = /var/run/lirc/lircd
pidfile         = /var/run/lirc/lircd.pid
plugindir       = /usr/lib/x86_64-linux-gnu/lirc/plugins
permission      = 666
allow-simulate  = No
repeat-max      = 600
#effective-user =
#listen         = [address:]port
#connect        = host[:port]
#loglevel       = 6
#release        = true
#release_suffix = _EVUP
#logfile        = ...
#driver-options = ...

[lircmd]
uinput          = False
nodaemon        = False

# [modinit]
# code = /usr/sbin/modprobe lirc_serial
# code1 = /usr/bin/setfacl -m g:lirc:rw /dev/uinput
# code2 = ...


# [lircd-uinput]
# add-release-events = False
# release-timeout    = 200
# release-suffix     = _EVUP

```The problem is the device number changes randomly at reboot. Now it is set to ***hw:CARD=2,DEV=0. ***But sometime, after a reboot, I need to change it to ***hw:CARD=1,DEV=0 ***or vice versa.
Is there a way to make this device number permanent? Alternatively, I can find the device number with the command ***mode2 --list-devices***. Is it possible to create a script that would check the device number at boot and change the configuration file accordingly before starting lircd daemon?

---

