---
title: "wireless (Asus WL-167g) not connecting"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by g00fy on 2006-04-09
Hi all,


I have a very weird problem here ](*,) .

everything is compiled, and insmod'ed in the kernel...

```
iwconfig rausb essid "myessid"
```
Nothing different shows up in 'iwconfig'... It seems like I didn't issue any command...

```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

# cd ~/RT25USB-SRC-V2.0.4.0

# insmod rt2570.ko

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Channel=0
          RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# iwconfig rausb0 essid myessid

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Channel=0
          RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

then I saw the channel was 0 (automatic?), so I thought like... Mmmm, maybe that's the problem? So I changed it to be channel 6... That changed. Very weird. I tried again to change the essid, but no luck :confused:.

Another weird thing is that I did 'insmod rt2570', and after a reboot, I have to do insmod again? Is there some place where I have to copy the compiled driver to (and add it to /etc/modules ofcourse) to load automatically?

I really don't know what I am doing wrong here... Could anyone help me?

This is some more information you might need:

```
# cat /proc/version
Linux version 2.6.12-10-686 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:22:51 UTC 2006

# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
rt2570

# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
```

Thanks for any help!

---

### Post by karthik085 on 2006-04-09
Is the essid you want is being broadcasted?
sudo iwlist wlan0 scan 

If you see in the list, try this
iwconfig interface ap <wireless_router_ap>

If you do not see in the list, there wireless router is not broadcasting (probably disabled).

---

### Post by g00fy on 2006-04-10
No,

The AP broadcasting is disabled, but I know the name because I enabled it myself ;-).


I don't know what I did but I think it's something like this [just writing down for other peoples reference]:

1) copy the compiled driver to /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2570/rt2570.ko
2) depmod (took me a 4h to find this command! :@)
3) modprobe rt2570
4) /etc/network/interfaces:
```
iface rausb0 inet dhcp
      pre-up ifconfig rausb0 down
      pre-up iwconfig rausb0 essid "myessid"
      pre-up iwconfig rausb0 mode Managed
      pre-up ifconfig rausb0 up
      wireless-essid myessid
auto rausb0
```
5) /etc/init.d/networking restart


Seems to work like a charm now!

---

