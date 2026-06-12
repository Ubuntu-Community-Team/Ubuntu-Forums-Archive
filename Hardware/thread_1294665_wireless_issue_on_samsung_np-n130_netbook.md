---
title: "wireless issue on samsung np-n130 netbook"
date: 2009-10-18
forum: Hardware
---

### Post by eikichionizukait on 2009-10-18
Hi! I bought a samsung np-n130 netbook a couple of days ago and i was going to put ubuntu on it, but unfortunately  it doesn't detect wireless, and for a netbook it's pretty bad thing. Do you know how i cuold fix it?? in case of negative answer, can you suggest me a properly working (at least for wireless) distro?
thanks a lot
eikichi
p.s. i wasn'y sure about posting this thread here or in the wireless connection, in case i'll move it

---

### Post by jamiemcbuntu on 2009-11-07
Do you have the realtek wireless NIC? If so I got it working by installing ndisgtk,(gui for ndiswrapper). Make sure you use the driver found at the Samsung website for the nic, not the one from realtek.

---

### Post by Barry Carroll on 2009-11-08
Have a look here for more ndiswrapper information:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The n130 has a Realtek 8192e wireless nic and I think the drivers were rejected from inclusion in the kernel.  I found ndiswrapper to be unstable when I was testing the alpha build of karmic.  It might be better now though.

---

