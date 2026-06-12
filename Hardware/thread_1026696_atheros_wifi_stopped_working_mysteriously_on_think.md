---
title: "atheros wifi stopped working mysteriously on thinkpad t61"
date: 2008-12-31
forum: Hardware
---

### Post by oldmanstan on 2008-12-31
Wifi has always worked reasonably well on my thinkpad. It was working yesterday too until it mysteriously died.

Here's what happened: I was having some issues with avahi/zeroconf not working properly so I was messing around with that. It occurred to me that my laptop might not be visible to other machines (which was the problem) because it was connected over the wireless.

So, I plugged in a network cable and kept messing around with it. In order to make sure the laptop wasn't still really using the wireless I unchecked the wireless in the network manager applet.

After while I gave up and decided to go back to the wireless (the ethernet cable running across the floor needed to go) so I re-checked enable wireless in the NM and then let it start connecting to my network.

It never connected. I got a WPA passphrase box, which sometimes happens, I clicked 'ok' and let it keep going. After awhile it failed and gave up. I was confused so I tried again, no luck. Then I rebooted (which really shouldn't matter but...) and after the reboot there's no wireless in the network manager.

I had been meaning to switch to the 64 bit version anyway so I did a fresh install. Still no wireless. lspci -v shows no wireless adapter. ifconfig and iwconfig both show no wireless adapters.

Any ideas of what this could be? Maybe the wireless hardware died? That seems pretty unlikely to me, the machine is less than a year old.

machine is a thinkpad t61 with the atheros wireless chipset. this is on ubuntu 8.10. the problem first occurred on the 32 bit version and now persists with the 64 bit version.

---

### Post by girark on 2009-01-11
I am having a similar problem.

I put 8.10 on my ThinkPad R61 about 10 days ago. From the onset, I was getting kernel panic (blinking caps lock LED while frozen). I found a solution in another thread, installing linux-backports-modules-install. While that fixed the kernel panic, it caused my wireless connection to intermittently become dreadfully slow or fail altogether. I believe I tried to upgrade the driver (ath5k_pci) yesterday. When I rebooted today, the network tool did not show a single wireless network (there are about 8 in my neighborhood). I toggled the physical wifi button to no effect. I am trying to find a device manager akin to that in Windows but have not been able to.

Help?

---

### Post by birdy on 2009-01-14
There is a bug report for this problem [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760") (without solution).

---

