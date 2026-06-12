---
title: "error loading acx100"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by timkoop on 2007-04-22
Hi everyone.  When Feisty loads, it displays this error: (I think I got this error even before I started fiddling with things)

* Loading hardware drivers...
firmware helper[3599]: main: error loading '/lib/firmware/acx/default/tiacx100c00" for device '/class/firmware/0000:03:00.0' with driver '(unknown)'

I'm not exactly sure what this means, but I think it says that it can't get my network card to work.  I have a D-Link AirPlus DWL-650+, which is actually a Texus Instruments acx100.

If someone would like to help me with this, I'm actually trying to use the ndiswrapper instead of the open source acx100 driver, because I'm trying to get WPA encryption working.  I have read rumours that wpa_supplicant works with ndiswrapper, so I'm trying to get that working.

Using the Package Manager, I downloaded and installed the ndiswrapper gui and used that to install the Windows driver which I downloaded from D-Link's website.

But it still doesn't work.  Obviously I'm doing something wrong.  I still get that error on start up, so Ubuntu is still probably looking for the open source acx100 driver.  I have tried adding "blacklist acx100" to my /etc/modprobe.d/blacklist file, but that doesn't do anything either.

Does anyone have the answer for me?  I think there's something I'm not doing, but I don't know what it is.  Thanks a lot!

Details:

Error message at startup:
* Loading hardware drivers...
firmware helper[3599]: main: error loading '/lib/firmware/acx/default/tiacx100c00" for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
                                                                [ OK ]

# lspci -v -nn

03:00.0 Network controller [0280]: Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]
        Subsystem: D-Link System Inc DWL-650+ PC Card cardbus 22Mbs Wireless Adapter [AirPlus] [1186:3b00]
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at 3400 [size=32]
        Memory at 48010000 (32-bit, non-prefetchable) [size=4K]
        Memory at 48000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2



# ndiswrapper -l
airplus : driver installed
        device (104C:8400) present (alternate driver: acx)


p.s. Does the Network Manager use wpa_supplicant?

---

### Post by timkoop on 2007-04-22
Does anybody know how to tell Ubuntu which driver it should use for a certain device?

Can I assign a certain driver (ndiswrapper) to my network card?

Tim

---

### Post by thornomad on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94280](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94280) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi -

I don't have a solution for you, but did want to confirm that it is a problem with fiesty.  You can view the bug report at:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94280](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94280)

If you find a solution, please post it.  I noticed it during the testing phases (as did others) ... I haven't tried a full version of feisty though.  Sorry.

---

