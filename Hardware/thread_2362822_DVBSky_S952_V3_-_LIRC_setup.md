---
title: "DVBSky S952 V3 - LIRC setup"
date: 2017-06-02
forum: Hardware
---

### Post by vs-ruthless on 2017-06-02
Hi,

I been using the [DVBSky S952 Dual DVB-S/S2 PCIe (V3) ]("http://www.dvbsky.net/Products_S952V3.html")for a while now to record satellite TV,  but never bothered setting up the remote that came with it. Today I thought I'll see if I can get it working, but running into a few difficulties. The remote the came with it is cheap and doesn't have a model number etc. (see attachment) 

I've installed LIRC but cannot get IRW to run and I get the following error```
connect: No such file or directory
``` I'm believe this is because I've not configured the hardware.conf file?

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

```

The issue is I don't know what to put in it, as there nothing is /dev/ showing up relating to this card. I've looked on the [http://lirc-remotes.sourceforge.net/remotes-table.html](http://lirc-remotes.sourceforge.net/remotes-table.html) remote database and my card is not listed.

This is the output from dmesg | grep -i dvb
```
dmesg | grep -i dvb
[    3.912572] SMI PCIe driver 0000:04:00.0: card detected: DVBSky S952 V3
[    4.015888] DVB: registering new adapter (SMI_DVB)
[    4.397241] SMI PCIe driver 0000:04:00.0: DVB: registering adapter 0 frontend 0 (Montage Technology M88RS6000)...
[    4.405356] SMI PCIe driver 0000:04:00.0: DVBSky SMI PCIe MAC= 00:18:42:54:55:52
[    4.406626] DVB: registering new adapter (SMI_DVB)
[    4.680854] SMI PCIe driver 0000:04:00.0: DVB: registering adapter 1 frontend 0 (Montage Technology M88RS6000)...
[    4.687601] SMI PCIe driver 0000:04:00.0: DVBSky SMI PCIe MAC= 00:18:32:54:55:53
[    4.711710] Registered IR keymap rc-dvbsky
[    4.711825] input: IR (DVBSky S952 V3) as /devices/pci0000:00/0000:00:15.0/0000:04:00.0/rc/rc0/input15
[    4.711923] rc0: IR (DVBSky S952 V3) as /devices/pci0000:00/0000:00:15.0/0000:04:00.0/rc/rc0
[    8.190376] m88ds3103 9-0069: downloading firmware from file 'dvb-demod-m88rs6000.fw'
[   13.023507] m88ds3103 10-0069: downloading firmware from file 'dvb-demod-m88rs6000.fw'
```

I was tempted to purchase another remote, but I'm determined to find a away to get this one working. 

Any assistance would be must appreciated.

---

