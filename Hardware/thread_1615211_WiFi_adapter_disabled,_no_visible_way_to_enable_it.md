---
title: "WiFi adapter disabled, no visible way to enable it"
date: 2010-11-06
forum: Hardware
---

### Post by Sidrabs on 2010-11-06
Hello,

I have this old laptop that has WiFi adapter, and set of buttons along the keyboard, where one of them is supposed to enable/disable WiFi. It's got Kubuntu 10.04 on it.

This WiFi adapter used to be enabled, but after some system update it apparently got broken and disabled. Not sure after which one, though.

So now I have the "Enable wireless" option of KNetwork Manager greyed out, the button by the keyboard is of no good either (no big wonder, cause it required special driver in Windows to enable that set of keys).

I installed Wicd network manager, and it reports that "Wireless Kill Switch Enabled". I see no way how to disable the kill switch via software. However, I assume that it should be possible to disable that kill switch via software, because that windows driver that handles the special keyboard button does exactly that.

Running ifconfig shows no wlan adapters present. The wireless adapter (I can recognise it from MAC address) is shown as inactive eth1 adapter. Even if I boot from Live CD, the adapter is not enabled. Hardinfo identifies this eth1 as Interface Type = Wireless, but I see no way how to perform any activity with that adapter.

Now, is there anything I can do about this? One crazy option would be installing Windows with those special drivers, and go and push that special button to enable the adapter. And then install the Linux again. However, I'd like to find an easier way to solve this.

---

### Post by Sidrabs on 2010-11-07
Woohooo, I've found a setting in BIOS that enabled my WiFi card! Don't know why it was reset, but who cares, if I got it back now.

SOLVED.

---

