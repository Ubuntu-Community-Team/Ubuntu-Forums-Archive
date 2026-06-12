---
title: "Cannot transfer files between phone and pc over bluetooth"
date: 2008-11-30
forum: Hardware
---

### Post by rvbhute on 2008-11-30
I am using Intrepid with all updates applied and trying to transfer files between my Sony Ericsson T700 and my PC.

The BT dongle is detected fine - seen in **hcitool dev**. I can see the mobile if I do a **hcitool scan** or **hcitool inq**. I can also see my PC from the mobile when I search for devices.

1. I can't pair from the PC, the BT applet's setup device wizard *doesn't show the phone*. 

2. I can pair from the phone - the BT applet prompts for the PIN and the pairing occurs. But I when I try to connect, I get "Bluetooth Connection Failed" on the phone.

3. If I try to directly send a file from my phone to PC, it says no devices found.

4. When I try to send a file from the PC to the phone, the error in screenshot 1 appears.

When I try to browse files on the phone, error in screenshot 2 appears.

---

### Post by liniaal on 2008-11-30
what i did since 7.10 - just apt-get install gnome-bluetooth. this is in my opinion the easiest way to get good bt functionality on your ubuntu install. i also work this way with my xubuntu install. i work with a SE s500i - i just sent a file over. what i did was:
* put in the bt dongle
* open a terminal and launch bluetooth-properties
* set it visible forever (i take the dongle out if i'm done)
* click the big plus and select my device if it shows the phone's BT name correctly (might take a reload of the bluetooth-properties window)
* enter the code that the gnome bt app gives on your phone
* ping! paired.

from now on i add bluetooth-applet to the autostarted apps so it will show directly (if i'm correct) when i plug in a BT device. the bluetooth-applet command is useful for receiving files, use bluetooth-sendto to, well you guessed it.

---

### Post by rvbhute on 2008-11-30
I have already installed gnome-bluetooth and bluez. Bluetooth worked in ubuntu 8.04. Not working in 8.10.

---

### Post by liniaal on 2008-12-04
ok but then describe exactly where it goes wrong?

---

### Post by rvbhute on 2008-12-04
I have filed a bug report. This seems to be a widespread problem. 

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/305208](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/305208)

---

### Post by tqft on 2008-12-31
I just added a comment to the bug with some more detail confirming stuff.

anyone had luck getting it to work yet?

---

### Post by southerngeek on 2009-04-01
I have the same problem with my phone, on 8.10. I can send files from the the phone to the PC, but when I try to go the other way, I get the same error as rvbhute did. I can send files to the phone from my Windows box,  though, so I know it's not the phone or dongle.

---

### Post by tqft on 2009-04-01
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

Is the bug with most of the comments and workaround which appears to be nearing fixing in 8.10 - all ready to go and will fix stuff for most people

---

