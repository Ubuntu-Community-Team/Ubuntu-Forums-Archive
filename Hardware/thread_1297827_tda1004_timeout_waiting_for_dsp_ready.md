---
title: "tda1004 timeout waiting for dsp ready"
date: 2009-10-22
forum: Hardware
---

### Post by Philip Farrugia on 2009-10-22
Keep getting the following error when booting from karmic beta (all updates installed).

tda1004 timeout waiting for dsp ready

After an age (30 seconds?) it then boots. The tda1004 is I think part of my tv-tuner card?

Anyone got any ideas for fixing this?

---

### Post by kem on 2009-11-08
Philip, did you resolved this issue? I am solving same problem.

I manually inserted firmware dvb-fe-tda10046.fw into /lib/firmware and after reboot it worked fine. I setup MythTV completely. However I see now it is unstable as I getting following dmesg now...

[   36.832010] tda1004x: timeout waiting for DSP ready
[   36.872010] tda1004x: found firmware revision 80 -- invalid
[   36.872015] tda1004x: waiting for firmware upload...
[   36.872027] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10046.fw
[   53.692011] tda1004x: timeout waiting for DSP ready
[   53.732015] tda1004x: found firmware revision 80 -- invalid
[   53.732023] tda1004x: firmware upload failed
[   60.006453] glxinfo:2121 freeing invalid memtype f8102000-f8112000
[   60.006470] glxinfo:2121 freeing invalid memtype f8112000-f8122000
[   60.006483] glxinfo:2121 freeing invalid memtype f8122000-f8132000
[   60.006495] glxinfo:2121 freeing invalid memtype f8132000-f8142000
[   60.006506] glxinfo:2121 freeing invalid memtype f8142000-f8152000
[   60.006517] glxinfo:2121 freeing invalid memtype f8152000-f8162000
[   60.006529] glxinfo:2121 freeing invalid memtype f8162000-f8172000
[   60.006540] glxinfo:2121 freeing invalid memtype f8172000-f8182000

---

### Post by Philip Farrugia on 2009-11-15
No cure yet.  Sometimes it boots fine but mostly it stops for 30-60 seconds.  I suspect the problem is the tv-card is slow to initialise or respond to the driver in the kernel. Hoping a kernel update one day may fix it.

---

### Post by kem on 2009-11-17
Philip, what kind of software do you run to see digital tv? I had trouble with MythTV. I have found simple mythtv uninstall (and reinstall) may resolve this issue.

I described my issue here [http://ubuntuforums.org/showthread.php?p=8281808]("http://ubuntuforums.org/showthread.php?p=8281808")

I also contacted driver developers and got this explanation ...
> This issue is at least partly known:
The problem is that the MythTV frontend initializes the (analog) tuner in a very early state (nothing wrong with that). If the driver for the tda10046 really needs to download the firmware, this takes a number of seconds. If any software tries to program the tuner in this time, this causes a bus conflict on the card. As a result, the DSP on the 10046 crashes and will not recover. A clean solution would be to implement a locking mechanism on board layer but i never did that (not a simple task).

Hope it may be of some help for you.

---

### Post by kem on 2009-11-23
Philip,

I reported this issue in launchpad. Could you please support this report and enter your comments there?

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264")

---

### Post by Philip Farrugia on 2009-12-08
Hi, still have this issue. I'm using ubuntu9.10 and kaffeine from karmic repositories. As the problem is erratic and occurs at boot I assume it's in the kernel somewhere. don't think it's the harware as openSuse11.2 and win7 are fine.

---

### Post by kem on 2010-06-10
Workaround indicated in [https://bugs.launchpad.net/mythbuntu/+bug/556204](https://bugs.launchpad.net/mythbuntu/+bug/556204) resolved my issue. Modify /etc/init/mythtv-backend.conf as follows:

Replace line

start on (local-filesystems and net-device-up IFACE=lo)

with

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)

My mythtv is working now for several restarts. The only drawback is the boot is a bit longer.

---

