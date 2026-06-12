---
title: "Possible Power Mangement Bug: HP DM1Z"
date: 2011-04-15
forum: Hardware
---

### Post by Redblade20XX on 2011-04-15
Hey everyone,

I recently bought a dm1z and posted on this forum the power problem I had. The dm1z would drain the battery about 10% per day that it wasn't used. After looking into this problem a little more, I found out that the wireless card and ethernet card still had power after shutting down any variant of ubuntu. After completing a fresh install of allot of ubuntu variants with an ethernet cable plugged in, I would remove the power supply, shut down the system and still see that power is being supplied to the ethernet port after shutdown (the dm1z has an led to signify that the port is still receiving power). The led would only shut off if I removed the battery and reinserting it meaning that it continually drained the battery even after shutdown . So I was just wondering if anyone with the dm1z has a similar power problem which would mean that's its either a hardware problem, a software problem or just my configuration?

Thanks for any help,

-Red

---

### Post by i_grok on 2011-04-24
Yes, I can confirm this problem. Left my DM1Z on the shelf for 2 weeks and the battery drained to 0%.

---

### Post by i_grok on 2011-04-24
Possible work-around. The laptop seems to properly power off if you hold the power button down for 4 seconds. So:

[LIST=1]
[*]From within Linux, select "Reboot" instead of "Power Off".
[*]When the system has restarted and gotten to the BIOS, hit escape (to keep it from going further).
[*]Hold down the power button for 4 seconds.
[/LIST]

---

### Post by Redblade20XX on 2011-04-26
> **i_grok said:**
> Possible work-around. The laptop seems to properly power off if you hold the power button down for 4 seconds. So:

[LIST=1]
[*]From within Linux, select "Reboot" instead of "Power Off".
[*]When the system has restarted and gotten to the BIOS, hit escape (to keep it from going further).
[*]Hold down the power button for 4 seconds.
[/LIST]


Thanks for the confirm! I'm guessing this is a temp fix?

---

### Post by i_grok on 2011-04-26
> **Redblade20XX said:**
> Thanks for the confirm! I'm guessing this is a temp fix?

Yes, this is definitely temporary! But it should work until the Linux kernel/Ubuntu shutdown is fixed. It's beyond my expertise - I would not expect a quick fix.

---

### Post by lem79 on 2011-05-21
Just confirming that as of Ubuntu 11.04 (desktop AMD64 version), the DM1-3010AU (E-350 1.6GHz, Radeon 6310, 320Gb HD, 2Gb DDR3, gigabit ethernet, wireless and bluetooth), which is similar to the DM1Z, also suffers this bug. The ethernet port stays lit up even though the machine should be off, and the battery loses about 10% per day, and will go to 0% (this happens even if no ethernet cable is plugged in, to be clear).

Removing the battery and putting it back in turns it off properly. I never thought about the 4 second power button thing  (even though I'm well aware of it) .. thanks, nice workaround :)

---

### Post by fbachofner on 2011-05-22
This all probably has something to do with Wake-On-LAN.

If the networking hardware does not have power, WOL will not work.

I would say that this will NOT be fixed in a future version.

The trick is to learn how to disable WOL, at which point the networking hardware should shut down completely.

---

### Post by Redblade20XX on 2011-05-23
> **fbachofner said:**
> This all probably has something to do with Wake-On-LAN.

If the networking hardware does not have power, WOL will not work.

I would say that this will NOT be fixed in a future version.

The trick is to learn how to disable WOL, at which point the networking hardware should shut down completely.

It maybe but I'm suspecting the wireless driver first, we had to patch it with unofficial "non-ubuntu developer" patches to get it to function on the dm1z. The Bios has an option for WOL but it's disabled.

---

### Post by i_grok on 2011-05-31
I had been forgetting about the workaround from time to time, so I decided I needed something better.

You can force Ubuntu to shutdown without powering off the system, which then allows you to use the power button. To achieve this, you need to edit /etc/default/halt to contain:

```
HALT=halt
```

I should also mention that I've been keeping a running tab of these [DM1Z issues on my blog]("http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010") and it appears that users of other distros are seeing the same problems.

---

### Post by deflagmator on 2011-06-13
> **i_grok said:**
> I had been forgetting about the workaround from time to time, so I decided I needed something better.

You can force Ubuntu to shutdown without powering off the system, which then allows you to use the power button. To achieve this, you need to edit /etc/default/halt to contain:

```
HALT=halt
```

I should also mention that I've been keeping a running tab of these [DM1Z issues on my blog]("http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010") and it appears that users of other distros are seeing the same problems.

I sent you some questions  (in your blog) regarding an existing opened bug. 
In my case I think I only have the poweroff problem.

---

### Post by i_grok on 2011-06-13
> **deflagmator said:**
> I sent you some questions  (in your blog) regarding an existing opened bug. 
In my case I think I only have the poweroff problem.

I'm not aware of an open bug for this issue. It appears that many distributions are exhibiting the issue, so I don't know if opening an Ubuntu bug would be productive. The bug either resides in the Linux kernel or - more likely - is a hardware issue the kernel would have to work around.

---

### Post by deflagmator on 2011-06-15
May be we have a solution,:o

Today I will try experiment with it:

[http://forum.videohelp.com/threads/333527-Ubuntu-10-10-draining-my-battery?p=2076325&viewfull=1#post2076325]("http://forum.videohelp.com/threads/333527-Ubuntu-10-10-draining-my-battery?p=2076325&viewfull=1#post2076325")

Post: #21

---

### Post by Redblade20XX on 2011-06-15
> **deflagmator said:**
> May be we have a solution,:o

Today I will try experiment with it:

[http://forum.videohelp.com/threads/333527-Ubuntu-10-10-draining-my-battery?p=2076325&viewfull=1#post2076325](http://forum.videohelp.com/threads/333527-Ubuntu-10-10-draining-my-battery?p=2076325&viewfull=1#post2076325)

Post: #21

Currently testing out this fix. Note: If anyone wants to mess around with initi.d scripts, please make backups of them before modifying!

---

### Post by psusi on 2011-06-15
Yep, sounds like the driver is enabling WOL.  What does cat /proc/acpi/wakeup show?

---

### Post by Redblade20XX on 2011-06-15
6 hours in and battery is still at 100%. Looking good!!:guitar:

---

### Post by Yellow Pasque on 2011-06-15
Can't you turn off Wake-On-LAN in the BIOS?

---

### Post by Redblade20XX on 2011-06-15
12 hours in and the battery dropped 8%.:-|

> **psusi said:**
> Yep, sounds like the driver is enabling WOL.  What does cat /proc/acpi/wakeup show?

Here are the contents of wakeup:

```

DeviceDevice    S-state   Status   Sysfs node
PB4       S5    *disabled  pci:0000:00:04.0
XPDV      S5    *disabled  pci:0000:01:00.0
PB5       S5    *disabled  pci:0000:00:05.0
USB0      S3    *disabled  pci:0000:00:12.0
USB4      S3    *disabled  pci:0000:00:12.2
P2P       S5     disabled  pci:0000:00:14.4


```

> **Temüjin said:**
> Can't you turn off Wake-On-LAN in the BIOS?

Don't see that option on the bios.

---

### Post by psusi on 2011-06-15
Interesting that some of those can wake up from S5 ( off ).  Does one correspond to your ethernet port?  What does sudo lspci show?

It looks like this is a bios problem... it is indicating that the ethernet port can wake the system even when it is totally off, and probably also enabling wol, which means it doesn't shut off.

I assume this is with the fix you have been testing?  Can you disable the fix and check /proc/acpi/wakeup again to see if one of those changes to enabled?

---

### Post by psusi on 2011-06-15
Also what does sudo ethtool eth0 show for the wol status?

---

### Post by Redblade20XX on 2011-06-15
> **psusi said:**
> Interesting that some of those can wake up from S5 ( off ).  Does one correspond to your ethernet port?  What does sudo lspci show?

It looks like this is a bios problem... it is indicating that the ethernet port can wake the system even when it is totally off, and probably also enabling wol, which means it doesn't shut off.

I assume this is with the fix you have been testing?  Can you disable the fix and check /proc/acpi/wakeup again to see if one of those changes to enabled?

Here is the output of lspci.

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Device 1513
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: RaLink Device 539f

```

Maybe I should update the bios then...Here is the wakeup file after undoing the fix.

```

Device  S-state   Status   Sysfs node
PB4       S5    *disabled  pci:0000:00:04.0
XPDV      S5    *disabled  pci:0000:01:00.0
PB5       S5    *disabled  pci:0000:00:05.0
USB0      S3    *disabled  pci:0000:00:12.0
USB4      S3    *disabled  pci:0000:00:12.2
P2P       S5     disabled  pci:0000:00:14.4

```

> **psusi said:**
> Also what does sudo ethtool eth0 show for the wol status?

Here is the ethtool output.

```

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no

```

---

### Post by psusi on 2011-06-16
Strange, wol is enabled, but /proc/acpi/wakeup doesn't show that wakeup is enabled.  They should agree.

At any rate, if your bios does not have an option to disable WOL, then check for an update and/or complain to the manufacturer.

---

### Post by Redblade20XX on 2011-06-16
> **psusi said:**
> Strange, wol is enabled, but /proc/acpi/wakeup doesn't show that wakeup is enabled.  They should agree.

At any rate, if your bios does not have an option to disable WOL, then check for an update and/or complain to the manufacturer.

Ironically, I've found an advance bios menu for the dm1z and under this advance bios menu there is a setting called wake up on pme and external network adapter that was enabled. Currently, I've disabled those setting and testing whether or not this has an effect on the battery life.

Anyways thanks for your help, psusi!!!! =D>

- Red

---

### Post by psusi on 2011-06-16
Can you check if /proc/acpi/wakeup and ethtool changed because of that setting?

---

### Post by Redblade20XX on 2011-06-16
After 12 hours of testing with the external network adapter and wake on pme disabled, the battery is still at 100%. It's looking good so far but a couple more hours of testing won't be bad. 

For anyone who wants to try this out by getting into the advanced bios mode,

***Note***: My bios version is F.03 but the most current one is F.12. I've heard rumors that the upgraded bios blocks the advance mode option so if it doesn't work, check your bios version. Don't really know if it's true since I haven't updated the bios. Also if your bios doesn't allow the advance mode option, you can google to mod the bios to allow the advance mode but be careful, you can screw up your computer really bad and also void the warranty, if any!!!


After shutting down or restarting the system, during start up when the bios screen boots, press the escape button and you'll be in a menu with configurations such as boot order. Press the "F10" key and immediately after press the "A" key. This will enable the advance bios option and unlock more menus for configuration. Under the advance tab, there is an option for "AMD PBS Option" and under that tab there will be options that will enable certain functions on the motherboard such as bluetooth, camera, wifi, etc. Look for an option called "external lan controller" and disable it (I think this has to due with wol). After wards, press "escape" key to return to the main bios configuration menu and move to a tab called "Power". Under that menu look for an option called "Wake on PME" (also has something to do with wol) and disable it also. Afterwards, press the "F10" key to save the bios. From this point on, you can test to see if there still is that 10% drain per day.


Here is a a youtube video pertaining to the bios advance mode:
[http://www.youtube.com/watch?v=8-9XFejk0_w](http://www.youtube.com/watch?v=8-9XFejk0_w)

In the description box there is also the instructions on how to activate it without reading my wall of text. ;)

Good luck to all who wish to test this out!!

-Red

---

### Post by Redblade20XX on 2011-06-16
> **psusi said:**
> Can you check if /proc/acpi/wakeup and ethtool changed because of that setting?

Sure! Here is the contents of wakeup:

```

Device  S-state   Status   Sysfs node
PB4       S0    *disabled  pci:0000:00:04.0
XPDV      S5    *disabled  pci:0000:01:00.0
PB5       S0    *disabled  pci:0000:00:05.0
USB0      S3    *disabled  pci:0000:00:12.0
USB4      S3    *disabled  pci:0000:00:12.2
P2P       S0     disabled  pci:0000:00:14.4

```

And ethtool:

```

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000033 (51)
        Link detected: no

```

Looks pretty good so far!!

---

### Post by Redblade20XX on 2011-06-17
Alright!! After 24 hours of testing, the battery is still at 100% (\\:D/) therefore I can conclude that the power management bug was due to wake on lan being enabled by the bios and the fix is to get into the advance bios menu and disable the two items I've stated before. I'm guessing the os, for some reason, couldn't handle management of the wake on lan process and shutting it off in the bios is a remedy.

Thanks for all the responses by all the people in this thread because without you guys I wouldn't have snooped around more and get a fix!!!! ;)

Again thanks and finally, thread closed!=D>

-Red

---

### Post by psusi on 2011-06-17
> **Redblade20XX said:**
> I'm guessing the os, for some reason, couldn't handle management of the wake on lan process and shutting it off in the bios is a remedy.

No, the problem is that you had WOL enabled, and that takes power.  The OS doesn't really have anything to do with it.

---

### Post by Redblade20XX on 2011-06-17
> **psusi said:**
> No, the problem is that you had WOL enabled, and that takes power.  The OS doesn't really have anything to do with it.

Oh, okay! Btw, the advance bios menu was hidden with no indication that it existed so I didn't know you could disable it which caused the origin of this thread. Also this computer came with it enabled so "I" didn't "enable" it.

---

### Post by Yellow Pasque on 2011-06-17
LOL. I'm glad I responded to this topic. I just realized that my dv6 laptop has the same crippled BIOS.

---

### Post by i_grok on 2011-06-19
I have BIOS version F.05 and was still able to get into the advanced BIOS options. For reference, my DM1Z laptop was ordered in March 2011.

Also, I'd like to note that disabling "External lan controller" in the advanced settings does not actually disable the wired ethernet device. It's clearly just a poorly named setting.

---

### Post by agentsteel on 2011-09-25
For those who have a latter BIOS version which does not allow WOL to be disabled, you can use ethtool in order to do it :

# ethtool -s eth0 wol d

see here how to make this permanent 

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

