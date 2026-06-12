---
title: "taking 8 minutes to boot from Toshiba external usb drive"
date: 2014-07-01
forum: Hardware
---

### Post by Dreamer Fithp Apprentice on 2014-07-01
Freshly installed 14.04 from mini.iso with Openbox as both WM and sole DE on a Toshiba Canvio 1 "TB" external usb-connected hard drive. I've booted the same kind of setup from Western Digital external drives with no problem.

This takes about 8 - 9 minutes to get to login. After that, it's fine. Since it does eventually deal with the hardware it finds and boot, it CAN do so. What I need is to
figure out how to tell it to not waste time trying to do whatever "enumeration" (per log, see below) it's failing at, and go ahead and use whatever fallback mechanism it is useing to boot. Here is the part of dmesg that looks like what I see on the monitor (I replaced "quiet splash" with "" in grub) when booting slows to a crawl:
```
[   28.533298] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   31.428846] usb 6-2: new full-speed USB device number 29 using ohci-pci
[   31.569036] usb 6-2: device descriptor read/64, error -62
[   43.292478] usb 6-2: new full-speed USB device number 34 using ohci-pci
[   43.432573] usb 6-2: device descriptor read/64, error -62
[   44.845775] usb 6-2: new full-speed USB device number 36 using ohci-pci
[   44.985899] usb 6-2: device descriptor read/64, error -62
[   45.802577] usb 6-2: new full-speed USB device number 37 using ohci-pci
[   45.942696] usb 6-2: device descriptor read/64, error -62
[   50.670615] usb 6-2: new full-speed USB device number 45 using ohci-pci
[   50.810762] usb 6-2: device descriptor read/64, error -62
[   51.564079] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:ec:1a:59:3d:dc:8e:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=50240 PROTO=2 
[   54.609933] usb 6-2: new full-speed USB device number 51 using ohci-pci
[   62.480509] usb 6-2: new full-speed USB device number 64 using ohci-pci
[   69.778603] usb 6-2: new full-speed USB device number 76 using ohci-pci
[   71.684188] usb 6-2: new full-speed USB device number 79 using ohci-pci
[   73.017312] usb 6-2: new full-speed USB device number 81 using ohci-pci
[   73.157428] usb 6-2: device descriptor read/64, error -62
[   73.401632] usb 6-2: device descriptor read/64, error -62
[   73.641834] usb 6-2: new full-speed USB device number 82 using ohci-pci
[   73.781941] usb 6-2: device descriptor read/64, error -62
[   74.026139] usb 6-2: device descriptor read/64, error -62
[   74.266335] usb 6-2: new full-speed USB device number 83 using ohci-pci
[   74.674677] usb 6-2: device not accepting address 83, error -62
[   74.810810] usb 6-2: new full-speed USB device number 84 using ohci-pci
[   75.219195] usb 6-2: device not accepting address 84, error -62
[   75.219451] hub 6-0:1.0: unable to enumerate USB device on port 2

```It's the only working drive I have right now, so I need to make this work. Thanks for reading.

Any ideas?

---

### Post by oldfred on 2014-07-01
Is there some reason why it is only seeing full speed device?
Either computer port or caddy for external drive?

 USB 1.0 - 1.5 Mbit/s "Low Speed" and 12 Mbit/s "Full Speed"
USB 2.0 specification Hi-Speed - 480 Mbit/s
USB 3.0 specification Super-Speed  - up to 5Gbps

---

### Post by Dreamer Fithp Apprentice on 2014-07-01
> **oldfred said:**
> Is there some reason why it is only seeing full speed device?
Either computer port or caddy for external drive?

 USB 1.0 - 1.5 Mbit/s "Low Speed" and 12 Mbit/s "Full Speed"
USB 2.0 specification Hi-Speed - 480 Mbit/s
USB 3.0 specification Super-Speed  - up to 5GbpsThanks for answering, Oldfred. I'm sorry - but I don't follow you. The drive, according to the box it came in, is supposed to be compatible with USB 2.0 or 3.0 ports with higher transfer speeds when plugged in to the latter. It is connected by a cable with the older form-factor style (rectangular cross-section about a cm long by about the width of a pencil lead) of usb connector at the computer end, plugged in to one of a gang of 4 such ports at the back of my computer, and one of the newer style, smaller connectors with a groove in one side plugged into the drive. I'm not sure if the computer is supplying USB 2 or 3. There is nothing I would call a caddy. The drive comes in a houseing that isn't meant to be normally removed (although I have had occasion to with another drive and it isn't hard - still, though I'd call it a "housing"). The only other drive in the machine ATM is the cd/dvd reader/burner. Is any of that to the point?

---

### Post by oldfred on 2014-07-01
Something does not seem correct as it is reporting only Full speed or USB1, not USB2 even.

Did you try other ports?
What is port supposed to be USB2 or USB3?
There have been some compatibility issues with USB3 ports.

And some have just found that the USB drive caddy/case was not as good as it was supposed to be.

---

### Post by Dreamer Fithp Apprentice on 2014-07-02
Thanks much, Oldfred.

Since they are all slow, it hadn't occured to me the details might be different depending on which port my hd is connected to. BTW, I should note in passing I am at all times using the word "port" to refer to a physical, observable, pointable-to, mechanical structure consisting of a hole into which some kind of male data connector can be plugged into. I know the word is used to refer to more abstract things as well, but I'll abjure that usage because I don't really understand it. It took me a while to sort it out to the extent that I have. Here is what I've figured out so far:

In all cases, the last thing before a substantial slowdown is:
```
Cloud-init v. 0.7.5 running 'init' at Wed, 02 Jul 2014 19:15:18 +0000. Up 32.42 seconds.
```followed by a table, made of lines beginning "ci-info: "
That seems fine.

In the tty visible during boot what comes next varies. Sometimes it's lines like:
```
[   13.861363] usb 6-2: device descriptor read/64, error -62
```
Sometimes like:
```
2014-07-02 15:16:48,527 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [50/120s]: request error [(<urllib3.connectionpool.HTTPConnectionPool object at 0x7fb94ed14790>, 'Connection to 169.254.169.254 timed out. (connect timeout=50.0)')]
```

In all boot.logs this sort of thing comes next and takes a couple of minutes:
```
2014-07-02 15:16:48,527 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [50/120s]: request error [(<urllib3.connectionpool.HTTPConnectionPool object at 0x7fb94ed14790>, 'Connection to 169.254.169.254 timed out. (connect timeout=50.0)')]
2014-07-02 15:17:39,580 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [101/120s]: request error [(<urllib3.connectionpool.HTTPConnectionPool object at 0x7fb94ed14290>, 'Connection to 169.254.169.254 timed out. (connect timeout=50.0)')]
2014-07-02 15:17:57,600 - url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [119/120s]: request error [(<urllib3.connectionpool.HTTPConnectionPool object at 0x7fb94ed14a50>, 'Connection to 169.254.169.254 timed out. (connect timeout=17.0)')]
2014-07-02 15:17:58,601 - DataSourceEc2.py[CRITICAL]: Giving up on md from ['http://169.254.169.254/2009-04-04/meta-data/instance-id'] after 120 seconds
2014-07-02 15:17:58,665 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [0/120s]: empty response [404]
2014-07-02 15:17:59,685 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [1/120s]: empty response [404]
2014-07-02 15:18:00,705 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [2/120s]: empty response [404]
2014-07-02 15:18:01,725 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [3/120s]: empty response [404]
2014-07-02 15:18:02,745 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [4/120s]: empty response [404]
2014-07-02 15:18:03,765 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [5/120s]: empty response [404]
2014-07-02 15:18:05,865 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [7/120s]: empty response [404]
2014-07-02 15:18:07,965 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [9/120s]: empty response [404]
2014-07-02 15:18:10,065 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [11/120s]: empty response [404]
2014-07-02 15:18:12,165 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [13/120s]: empty response [404]
2014-07-02 15:18:14,265 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [15/120s]: empty response [404]
2014-07-02 15:18:17,365 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [18/120s]: empty response [404]
2014-07-02 15:18:20,465 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [21/120s]: empty response [404]
2014-07-02 15:18:23,565 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [24/120s]: empty response [404]
2014-07-02 15:18:26,665 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [28/120s]: empty response [404]
2014-07-02 15:18:29,765 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [31/120s]: empty response [404]
2014-07-02 15:18:33,865 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [35/120s]: empty response [404]
2014-07-02 15:18:37,965 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [39/120s]: empty response [404]
2014-07-02 15:18:42,065 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [43/120s]: empty response [404]
2014-07-02 15:18:46,165 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [47/120s]: empty response [404]
2014-07-02 15:18:50,265 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [51/120s]: empty response [404]
2014-07-02 15:18:55,365 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [56/120s]: empty response [404]
2014-07-02 15:19:00,465 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [61/120s]: empty response [404]
2014-07-02 15:19:05,565 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [66/120s]: empty response [404]
2014-07-02 15:19:10,664 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [72/120s]: empty response [404]
2014-07-02 15:19:15,764 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [77/120s]: empty response [404]
2014-07-02 15:19:21,864 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [83/120s]: empty response [404]
2014-07-02 15:19:27,964 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [89/120s]: empty response [404]
2014-07-02 15:19:33,984 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [95/120s]: empty response [404]
2014-07-02 15:19:40,064 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [101/120s]: empty response [404]
2014-07-02 15:19:46,164 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [107/120s]: empty response [404]
2014-07-02 15:19:53,264 - url_helper.py[WARNING]: Calling 'http://192.168.2.1//latest/meta-data/instance-id' failed [114/120s]: empty response [404]
2014-07-02 15:20:00,271 - DataSourceCloudStack.py[CRITICAL]: Giving up on waiting for the metadata from ['http://192.168.2.1//latest/meta-data/instance-id'] after 121 seconds
 * Starting Signal sysvinit that local filesystems are mounted[234G[ OK ]
 * Starting configure network device security[234G[ OK ]
```

In all the dmesg, I find at least some of this:
```
 [   13.861363] usb 6-2: device descriptor read/64, error -62
```

With all ports but the top right, dmesg has this:
```
 device not accepting address
```

With both bottom ports, but neither top, dmesg has this repeatedly:
```
 [   17.540090] systemd-udevd[355]: Error calling EVIOCSKEYCODE: Invalid argument
```

Looks like maybe I ought to use the top right port but that's still slow. I'm not sure what to make of the rest of it.

---

### Post by Dreamer Fithp Apprentice on 2014-07-03
@ Oldfred: Of course it's a vacation - you vacated your previous location. Of course by that logic, going to jail or being thrown out of an apartment or a bar would be a vacation too. I hope yours is more pleasant.

I'm glad you got me questioning my assumptions. I have made progress.  Right now I'm on the top left port which is where I finished up the previous round.  I'll test on other ports later but I started focusing on the```
- url_helper.py[WARNING]: Calling 'http://169.254.169.254/2009-04-04/meta-data/instance-id' failed [50/120s]: request error [(<urllib3.connectionpool.HTTPConnectionPool object at 0x7fb94ed14790>, 'Connection to 169.254.169.254 timed out. (connect timeout=50.0)')]
```stuff more and found this:
[http://askubuntu.com/questions/461942/fresh-install-ubuntu-14-04-server-slow-boot-due-to-failure-to-connect-169-254-16](http://askubuntu.com/questions/461942/fresh-install-ubuntu-14-04-server-slow-boot-due-to-failure-to-connect-169-254-16)
So I followed the suggestion in Michael Kropat's post and ran this:```
dpkg-reconfigure cloud-init
``` It didn't go quite as expected. That command doesn't make something else take notice of what you've written in that file (like update-grub does for instance) - instead it writes that file overwriting any manual changes after stepping through one of those semi-gui curses type dialogues and the result was not the expected "[ None ]" but "[ ]". The repetitive ```
url_helper.py[WARNING]
``` lines are gone, replaced by ```
[   33.604792] init: cloud-config main process (890) terminated with status 1
``` in dmesg and ```
2014-07-03 01:46:35,775 - util.py[WARNING]: No instance datasource found! Likely bad things to come!
``` in boot.log, which don't sound real good but certainly don't slow down my booting as much. After I study it a bit I may just uninstall Cloud-init completely. I don't know why I have it. I did NOT install "cloud version of Ubuntu server" spoken of in that post but the plain mini.iso. I'll post more when I know more.
================
edited in, more:
I'm finding a lot of stuff, much of it tracing back to this,
[http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error](http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error)
that suggests that both this error```
 [ 13.861363] usb 6-2: device descriptor read/64, error -62
```and this one```
 device not accepting address
```are likely to be results of high power usage by the device and that the fix is probably something like this:
[http://www.amazon.com/eForCity-dual-Micro-B-Cable-Black/dp/B005M0ICG2](http://www.amazon.com/eForCity-dual-Micro-B-Cable-Black/dp/B005M0ICG2)
Cheap enough. I'll order and install one and see. But the largest part of my slow booting seems to have come from cloud-init. I'm going to check a couple of things about that and expect to mark this [solved] shortly.
=====================
and again:
Solved.
I purged cloud-init. Virtualbox still seems unaffected as far as I can tell, and that's the only thing I have that I could imagine cloud-init helping.

Booting from the top right port, the only boot error messages remaining are the 2 likely to be fixed with the y-cable mentioned above. My boot speed is now normal. Fast actually, since I use plain Openbox as the sole DE.

Hopefully these details may help someone finding their way to this thread searching for related issues.

Thanks again Oldfred. I hope your vacation is superb.

---

