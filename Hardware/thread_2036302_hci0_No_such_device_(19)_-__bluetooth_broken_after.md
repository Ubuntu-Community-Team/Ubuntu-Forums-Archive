---
title: "hci0: No such device (19) -  bluetooth broken after debugging kernel Oops"
date: 2012-08-01
forum: Hardware
---

### Post by bbogart on 2012-08-01
Hello all,

I did not use bluetooth on this machine, running 12.04, until I recently replaced my dead wireless keyboard with a bluetooth one. The adapter was available and I used blueman-manager to pair and it appeared to be working fine. After a while it became unstable (would often not send keystrokes to the machine), and after some debugging I found many soft lockups and kernel Oops in the log, so I filed this bug report: [https://bugs.launchpad.net/bugs/1023723](https://bugs.launchpad.net/bugs/1023723)

I installed a 3.5.0 RC mainline kernel for testing, which I left on over a weekend with the keyboard attached, and everything seemed to work fine. I could not keep this config because I was unable to get the nvidia drivers to work with that kernel. So I went back to the original kernel (and have tried many stable kernels since, using the RC again) and I have not seen the bluetooth device come back. blueman-manager says that bluetooth is "off" (and will not let me turn it "on" and hcitool dev shows no devices. This is what I see in the logs (after stopping bluetoothd, and restarting with -d:

(attached)

If I boot my 12.04 liveDVD, I get the same problem:
Aug  1 10:34:47 ubuntu bluetoothd[17393]: Can't init device hci0: No such device (19)

Questions:

1. Does /dev/hci0 not exist because bluetooth does not find a device, and does not tell udev to generate a device? Or is /dev/hci0 not existing the root of the problem (bug in udev?)

2. I used a bluetooth keyboard on this machine, I filed a bug report, it was working, could the hardware have failed during the debugging process? (seems far-fetched)

3. Could switching to the RC kernel have switched some flag in the device that broke the bluetooth on this machine?

---

### Post by bbogart on 2012-08-09
bump

---

