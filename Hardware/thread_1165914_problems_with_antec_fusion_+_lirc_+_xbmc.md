---
title: "problems with antec fusion + lirc + xbmc"
date: 2009-05-21
forum: Hardware
---

### Post by Lytse on 2009-05-21
Hello,

I almost have my antec fusion with rm200 remote working.

However I still have one problem that I cannot get solved.

When I start the lirc drivers from the init.d during startup and use XBMC as the first application to start from X the remot works fine but only for about 2 minutes.

I found this in the logging:
[INDENT]May 21 10:17:58 aljoshtpc kernel: [    6.915505] lirc_dev: IR Remote Control driver registered, major 61
May 21 10:17:58 aljoshtpc kernel: [    6.962572] lirc_dev: lirc_register_driver: sample_rate: 0
May 21 10:17:58 aljoshtpc kernel: [    6.962682] lirc_dev: lirc_register_driver: sample_rate: 0
May 21 10:17:58 aljoshtpc kernel: [    6.962766] usbcore: registered new interface driver lirc_imon
May 21 10:19:38 aljoshtpc kernel: [  115.461685] lirc_dev: lirc_register_driver: sample_rate: 0
May 21 10:19:38 aljoshtpc kernel: [  115.462063] lirc_dev: lirc_register_driver: sample_rate: 0
[/INDENT]

I was wondering if someone knows why the drivers are registered twice? 

If I start everything by hand it seems to work fine.

---

### Post by Lytse on 2009-05-22
It's an hardware issue, seems that the usb device is restarted by the hub and get's reassigned to the next free ID. Imon creates two new devices.

[INDENT]
May 21 10:19:37 aljoshtpc kernel: [  114.948995] hub 3-0:1.0: port 4 disabled by hub (EMI?), re-enabling...
May 21 10:19:37 aljoshtpc kernel: [  114.949002] usb 3-4: USB disconnect, address 3
May 21 10:19:37 aljoshtpc kernel: [  114.949969] usb_rx_callback: status(-108 ): ignored
May 21 10:19:37 aljoshtpc kernel: [  114.950965] usb_rx_callback: status(-108 ): ignored
May 21 10:19:37 aljoshtpc kernel: [  114.951099] imon_disconnect: iMON device disconnected
May 21 10:19:37 aljoshtpc kernel: [  114.951227] imon_disconnect: iMON device disconnected
May 21 10:19:38 aljoshtpc kernel: [  115.252656] usb 3-4: new low speed USB device using ohci_hcd and address 4
May 21 10:19:38 aljoshtpc kernel: [  115.457035] usb 3-4: configuration #1 chosen from 1 choice
May 21 10:19:38 aljoshtpc kernel: [  115.461677] imon_probe: found iMON device
May 21 10:19:38 aljoshtpc kernel: [  115.461685] lirc_dev: lirc_register_driver: sample_rate: 0
May 21 10:19:38 aljoshtpc kernel: [  115.461731] imon_probe: Registered iMON driver(minor:2)
May 21 10:19:38 aljoshtpc kernel: [  115.461759] imon_probe: iMON device on usb<3:4> initialized
May 21 10:19:38 aljoshtpc kernel: [  115.462059] imon_probe: found iMON device
May 21 10:19:38 aljoshtpc kernel: [  115.462063] lirc_dev: lirc_register_driver: sample_rate: 0
May 21 10:19:38 aljoshtpc kernel: [  115.462088] imon_probe: Registered iMON driver(minor:3)
May 21 10:19:38 aljoshtpc kernel: [  115.462111] imon_probe: iMON device on usb<3:4> initialized
May 21 10:19:38 aljoshtpc kernel: [  115.508834] IR port closed
[/INDENT]

Anyone any ideas? I made sure that the Soundgraph is on a different bus then my mouse/keyboard.

Switching hardware connectors does not change the hub numbering.

---

### Post by Lytse on 2009-05-23
Hello,

I am glad I solved this crazy puzzle. :D

The problem was the usb, I figured this out by interpreting the other loggings in the kern.log.

First I switched some of the connectors on the motherboard but this did not help.

Second I took the usb cable from the remote and the lcd and just put it in one of the usb sockets. It worked. I suspected that the internal connector did not connect well but it happend to be the way I worked away the cable in the casing. It was put above the hard drive and the cable picked up some EMI just as the logging told me :-s. 

Fixed this and it worked, next time i will take more care cabling the computer.

Thanks for the help!

---

### Post by &lt;mike&gt; on 2009-12-01
Thanks for the tip.
I can't get my LCD working (so far) but I was continuously frustrated by this same problem.
Another post suggested this was to do with usb devices going to sleep. Because I'm congenitally lazy and cbf opening up my case, I'm trying the following fix first...

add to /etc/rc.local
```

# The following lines added in an attempt to get imon to stop freezing
echo -1 > /sys/module/usbcore/parameters/autosuspend
sleep 1
/usr/sbin/lsusb

```
(as root, of course) *before* the line ```
 exit 0 
```

Will post to let everyone know if this works. Apparently it will lead to issues with USB devices after suspending the computer... but I don't see that this will be a problem for my mythtv box, which is always on.

---

### Post by &lt;mike&gt; on 2009-12-01
ok, update, that didn't work

---

### Post by &lt;mike&gt; on 2009-12-17
Lytse, thanks!
I re-routed my cables and now my remote is no longer dying after a few minutes and refusing to work until I reboot.
I also fixed my LCD, which was not working, by placing
```

options lirc_imon display_type=2

```
into a file called /etc/modprobe.d/lirc.conf.

The setup has been working now for almost two weeks with no dramas!

Thanks again

---

