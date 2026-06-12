---
title: "Bluetooth not working"
date: 2011-10-25
forum: Hardware
---

### Post by Diskdoc on 2011-10-25
Upgraded to Oneiric. Nice Bluetooth icon in the taskbar now. I can enable/disable Bluetooth there but it seems impossible to connect to my Bluetooth speakers like in Natty. Also, although the panel icon says enabled, it's always DISABLED in the Bluetooth settings dialogue box.

Anyone else with the same problem?

---

### Post by campbelt on 2011-10-25
I can't get Bluetooth to recognize devices (mouse, keyboard, cellphone).  When I open the icon on the taskbar and select "set up new devices" and then scan, nothing turns up.

---

### Post by scarleo on 2011-10-25
I had some trouble at first to connect my phone via bluetooth but got it working after reinstalling everything already installed when searching for "blue" in synaptic and doing a reboot. It seems that there is still a problem on my laptop to control the hardware via bluetooth indicator, it showed that it was on when it was actually off. After fiddling around with the hardware switch it actually came on and connected my phone.

However, after connnecting the phone I still can't send files to it (bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044)). I just get  Permission denied message and pretty much nothing in the logs, this is all:

```
Oct 25 18:37:03 oscar-laptop bluetoothd[1306]: Mode session 0x7f1d90aa0530 with :1.63 activated
Oct 25 18:37:07 oscar-laptop obex-client[2467]: Permission denied (13)
Oct 25 18:37:12 oscar-laptop bluetoothd[1306]: Mode session 0x7f1d90aa0530 with :1.63 activated
Oct 25 18:37:15 oscar-laptop obex-client[2467]: Permission denied (13)
```

---

### Post by Pahanilmanlintu on 2011-11-17
Same thing with my attempts at sending files between phone and computer. I should also mention that bluetooth connections worked quite well in previous ubuntu versions (i probably didn't use it with Natty, but did use with either maverick or lucid) with the same bluetooth usb dongle. Since updating to Oneiric, can't browse files on phone (Nokia 3720 and now also N9), and can't send either.

I guess i should see if i get the same lines in system log when i get home.

edit: Syslog says: "Nov 17 18:02:31 mustikki obex-data-server: sdp_extract_seqtype: Unexpected end of packet" when trying to browse, and the same as above in scarleo's post when trying to send to phone, except with "connection refused (111)" instead of "permission denied".

---

