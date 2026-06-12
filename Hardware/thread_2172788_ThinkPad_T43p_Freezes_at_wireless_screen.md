---
title: "ThinkPad T43p Freezes at wireless screen"
date: 2013-09-06
forum: Hardware
---

### Post by alan_coleman2 on 2013-09-06
Hello everyone,

I'm trying to install Desktop 12 on a ThinkPad T43p, I've checked the docs and the specs are up to scratch.

The process works okay up until the wireless screen, which connects to my wireless and then hangs indefinitely.

I've had a look around online and there are suggestions that this issue may be down to partitions.

There's nothing on this machine I need so I'm happy to reformat the thing before installing Ubuntu.

What's the best way to take my hard disk back to a reformatted partitioned state before installing Ubuntu Desktop 12?

Many thanks

---

### Post by tgalati4 on 2013-09-06
I happen to have one of these (T43p) and I'm happily running 9.04.  I also plan to upgrade to Linux Mint Mate 14 (based on 12.10).  The wireless should be supported, but requires some proprietary firmware.  Turn off the wireless in BIOS and use a cable to connect to the internet while you are installing.

Once you have a successful install and you have tested basic functionality, then turn on the wireless and troubleshoot from there.

To start over, boot a Live USB and reformat your partitions.  There is no going back.  There is no downgrade.  If you need data off of the disk because you didn't back up, then you will need to use the Live USB and another USB disk to mount the drive and remove data from it.

If you turn off the wireless, you should be able to just reinstall, but I would start with a clean partition.

---

### Post by alan_coleman2 on 2013-09-07
Thanks for replying,

I think I can remember doing this a few years ago, I had a little disc utility that I used to boot from a CD for formatting and partitioning, Called Grub or something like that?

If I boot a Live CD of Ubuntu I should be able to partition the drive from there?

Then follow your wireless - cable connect procedure from there?

Thanks again.

---

### Post by tgalati4 on 2013-09-07
Correct.  Any way you can boot a Live session:  DVD, USB key, it doesn't matter.  But turn off the wireless first in BIOS.  Then you can run gparted and reformat your partitions.  You must reboot after this, to get the new partitions recognized, then perform your install after getting back into the Live Session.

Once you have installed, rebooted and now running your new distro, perform some updates while plugged in with the cable.  It will be faster than using wireless.

Then turn the wireless back on in BIOS, reboot and hit the esc key or alt-F1 key to see the boot messages scroll by.  You will see some instructions for getting your wireless back up and running.

Alternatively, open a terminal:

```
dmesg | more
```

There were 3 wireless cards put in those machines.  So you need to identify your card and use the correct instructions:  [http://www.thinkwiki.org/wiki/Category:T43](http://www.thinkwiki.org/wiki/Category:T43)

I have an Intel ABG card that uses the *ipw2200* module:

tgalati4@Dell600m-mint14 ~ $ modinfo ipw2200
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     B0A1B7C62D58999D6D67C20
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
alias:          pci:v00008086d00004223sv*sd*bc*sc*i*
alias:          pci:v00008086d00004221sv*sd*bc*sc*i*
alias:          pci:v00008086d00004220sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002762bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002761bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002754bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002753bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002752bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002751bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002742bc*sc*i*
alias:          pci:v00008086d00001043sv0000103Csd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002732bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002731bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002722bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002721bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002712bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002711bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002702bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 686 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

It requires some proprietary firmware to be downloaded and installed as part of the installation procedure.

---

### Post by alan_coleman2 on 2013-09-08
okay, that did it. Here are the steps I took.

1) Used[ Darik's Boot And Nuke]("http://www.dban.org/") to format the hard disk. 90 GB took about 3 hours.
2) Boot into BIOS and switch wireless hardware to Hidden.
3) Plug some internet in via Cat 5
4) Install Ubuntu
5) Reboot and run updates
6) Boot into BIOS and switch wireless to Enabled
7) Reboot into Ubuntu and connect to wireless network.

That simple. Thanks [tgalati4]("http://ubuntuforums.org/member.php?u=241895") for your help, much appreciated!

---

### Post by tgalati4 on 2013-09-08
I'm glad it worked for you.  Now I will print out this procedure when I do it.  You should get several more years out of your machine.

---

