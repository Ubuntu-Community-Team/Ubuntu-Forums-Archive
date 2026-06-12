---
title: "HELP! hp dv6-6135dx No webcam Mic or fingerprint scanner!"
date: 2012-02-05
forum: Hardware
---

### Post by SJerry421 on 2012-02-05
Hello Ubuntu community I have been between another Distro and Kubuntu for a while. Downloaded Kubuntu 11.10 and it is finally stable enough for me to use as my main Distro. I have run into a few problems that I would like to see if you guys could help me out with.
1. Webcam - Is not detected by Kubuntu 11.10 64bit by Default.
2. Mic- Same issue
3. Finger Print Scanner - Also not detected
Was wondering if anyone could assist me with a guide to get this working as stated above I have a dv6-6135dx thanks!

---

### Post by gordintoronto on 2012-02-05
Please tell us how you know these things? For example, if you install Cheese, does it show only a black screen? If so, could you please open a terminal window and run this command: lsusb
It will display your USB devices, including the webcam. One line of output might look like this:
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

In my case, the really useful information is "0ac8:303b" which uniquely identifies the brand and model of my webcam.

In my experience, when the mic doesn't work, 90% of the time it is muted and can be enabled in sound preferences.

Sorry, I have no suggestion for the fingerprint scanner. It might show up in the lsusb, in which case you can get some information to plug into Google.

---

