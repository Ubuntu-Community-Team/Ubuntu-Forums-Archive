---
title: "Acer Aspire 5102 &amp; Hardy Heron issues"
date: 2008-05-12
forum: Hardware
---

### Post by phantom0021 on 2008-05-12
I have an Acer Aspire 5102.  Had Edgy Eft on it and everything worked except the webcam and the camera cards.  Everything else worked fine, including the wireless.

I recently installed new the Hardy Heron.  The issues I have are as follows:

1 - The wireless is detected, but knetworkmanager and wicd doesn't seem to connect to open wireless networks.

2 - The suspend mode, which worked in Edgy, doesn't work here.  I get a bios message and then the system freezes.

3 - The webcam is detected.  lsusb returns the following:
Bus 003 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I've installed cheese, but it doesn't seem to work.

So, those are the essential issues.  Any help and suggestions would be helpful.

Thanks.

---

### Post by roderick on 2008-05-12
Can you explain exactly what you see in issue 1)? Do you see a list of access points in knetworkmanager or none show up at all? What wireless card do you have? provide lspci for it.

Also, for issue 2), what is the error you get?

---

### Post by phantom0021 on 2008-05-13
The lspci info for the ethernets:

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

I'll have to restart the system to get the other message and will do so later.

wicd does show some networks available, but doesn't connect after trying.

knetworkmanager doesn't work the way it did under edgy, which version would show all the wireless networks around.  And, the newer version is more problematic in that it is harder to set up profiles and doesn't show networks.  It has a new thing for "roaming" which is not the way the older version in edgy worked.  The one in edgy was easy to use and easy to set up things.  I wish they hadn't changed it.

---

### Post by phantom0021 on 2008-05-13
The message the system shows after trying to resume from suspended is:

RS485C - TEST BIOS BR#18675

Can anyone offer suggestions for this?

Thanks

---

### Post by phantom0021 on 2008-05-14
I've gotten the system to use the wifi with wicd.  It's not as clean as it was with Edgy and knetworkmanager, but it works.

So, not the things I'd really like to get working are the suspend mode and the webcam.

Mark

---

### Post by AbtZ on 2008-05-27
Phantom, regarding your webcam -- check this out:
[http://ubuntuforums.org/showpost.php?p=5055135&postcount=6](http://ubuntuforums.org/showpost.php?p=5055135&postcount=6)

Hope it helps :)

---

### Post by phantom0021 on 2008-06-07
Tried that fix a couple of times but it doesn't work, or, at least, it doesn't seem to under cheese.  Can't get xawtv to work.

Mark

---

