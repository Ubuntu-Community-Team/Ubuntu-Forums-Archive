---
title: "Managing several network devices..."
date: 2005-11-16
forum: General Help
---

### Post by kkinder on 2005-11-16
I have several goals here. I want to setup my laptop to be a little smarter about connecting. For example, it should really *not* be trying to use wifi when I have regular ethernet plugged in. I don't want it to try endlessly to bring up wifi when it boots when no such wifi is available. So far, that's a reasonable goal, right? Ok, here's another thing: I have an EVDO cell phone wireless card that I want it to behave intelligently with.

Goal 1: **Get Ubunto to Scan for Wifi networks, but not hold up the boot process if it can't find any**

If I boot up and ifup finds itself a nice little network to connect to, there is no delay. However, if it doesn't find a network, it stalls until dhcp gives up. Certainly there is a more intelligent way to do this.

Goal 2: **Figure out hotplug system, ifup/down scripts for EVDO Card**

Right now, I insert the right kernel modules and run pppd. I have a shell script that looks like this:

[INDENT]
ifdown eth1
modprobe ohci-hcd
modprobe usbserial vendor=0x106c product=0x3701
sleep 3
pppd call 1xevdo
tail -f /var/log/messages
[/INDENT]

I'm know that there are databases for devices that auto-insert modules. I also know you can somehow hook those up to ifup/down scripts. How would I go about in making my evdo card more like a normal device that comes up automatically when the pccard is inserted and can be manipulated with ifup/ifdown?

Goal 3: **Only use one network device**

I want to have priorities. ethernet and should take precedence over wifi. Because they have to be plugged in and wifi is built into the laptop. The rules should be something like...

[INDENT]
  if ethernet:
    ignore wifi
    ignore evdo
  else if evdo:
    ignore wifi
  else:
    use wifi
[/INDENT]

I'm not really interested in connection profiles. If I don't have evdo plugged in and I don't have ethernet plugged in, I want to use wifi. Otherwise, since those devices have to be plugged in, I want to give them priority. Can that be made simple? I promise I'll put together a little HOWTO if I can figure out how to set up my networking more intelligently. :)

---

### Post by kkinder on 2005-11-16
Aha, for automaticly taking up/down ppp, you add this to /etc/network/interfaces

```

iface ppp0 inet ppp
        provider 1xevdo

```

---

