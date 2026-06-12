---
title: "No Wi-Fi: ThinkPad SL410 2874-32U with Ubuntu 9.10 x64"
date: 2009-12-19
forum: Hardware
---

### Post by raparks on 2009-12-19
I just installed Ubuntu 9.10 x64 on a ThinkPad SL410 2874-32U and am not seeing any wireless functionality.  All of the information I've seen on this machine mentions 802.11b/g/n, but never lists a brand or model of the wireless adapter.

My skill level is such that I don't normally have difficulty setting up wireless in Ubuntu on a machine on which the Wi-Fi is directly supported, or supported with restricted drivers.  If NDISwrapper or another manual approach is necessary, I hope to find step-by-step instructions for the particular machine.

Alternately, has anyone had good luck with a particular ExpressCard/34 Wi-Fi adapter?

Any help is very much appreciated.

r.a.parks

---

### Post by prshah on 2009-12-19
> **raparks said:**
> this machine mentions 802.11b/g/n, but never lists a brand or model of the wireless adapter.

If NDISwrapper or another manual approach is necessary, I hope to find step-by-step instructions for the particular machine.

You can find out the details on the wireless adapter with the terminal (Applications-Accessories-Terminal) command```
lspci | grep -i **-E** ethernet\|wireless
```

If you post back the output, someone can probably suggest the correct steps to take to activate the wireless.

I recommend you use ndiswrapper only as a last resort; here's a step-by-step guide with expected outputs: [ [SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless  ]("http://ubuntuforums.org/showthread.php?t=756260")

Please post back here with more info if you require any additional assistance.

---

### Post by raparks on 2009-12-19
> **prshah said:**
> ```
lspci | grep -i -e ethernet\|wireless
```

That command didn't produce any results for me, however when I ran lspci by itself, I believe that the following two lines are the relevant information.  

05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Thanks,
r.a.parks

---

### Post by raparks on 2009-12-19
Ok, I found the answer.

'mrgoose' provided a great step-by-step here: [http://forum.novatech.co.uk/showpost.php?p=208517&postcount=10]("http://forum.novatech.co.uk/showpost.php?p=208517&postcount=10").  Unfortunately he may have linked to the 32-bit version of the file while describing the 64-bit version.  I downloaded the following to my desktop and then followed his instructions, with a satisfactory outcome: [http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz]("http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz").

---

### Post by prshah on 2009-12-20
> **raparks said:**
> That command didn't produce any results for me

Oops, my mistake; the "-e" was supposed to be "-E" (now corrected in original post as well).

---

