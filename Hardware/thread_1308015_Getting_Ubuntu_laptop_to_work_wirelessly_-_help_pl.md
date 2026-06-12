---
title: "Getting Ubuntu laptop to work wirelessly - help please"
date: 2009-10-31
forum: Hardware
---

### Post by mjp29 on 2009-10-31
My Uncle has an HP Pavillion zv6130us laptop and a Linksys Wireless G   WRT54 GS  router.

He has Ubuntu partitioned on the laptop.  He is unable to use it wirelessly.  He thinks he needs special software installed to be able to get this router to work wirelessly with his computer.

ms windows xp is on the other partition of the same laptop and it will work wirelessy.  He says that he recalls installing from a cd disk special software to get the cpu to work with windows xp.

However, his wife's newer computer did not special software installed on its ms windows to recognize the router.

help please.  perhaps there is a package or applet that needs to be downloaded for his Ubuntu to get the wireless to work for him.

---

### Post by Bucky Ball on 2009-10-31
Router does NOT require special software.

Have you plugged in an ethernet cable? First thing to getting wireless happening is to make a wired connection and download all updates. This should pick up the card if it is going to and offer you the restricted drivers. They are not included in the install for legal reasons.

We can not give much more help without the details of the wireless card. If you don't know what it is open a terminal and run:

```
lspci
```You will find it toward the end of that list. You should also include the Ubuntu release you are using.

---

### Post by CylnZ on 2009-10-31
Probably has a BCM4306 chip. A lot of  hp zv6130us did

Do the lspci to check and if you do, here's a hardy - karmic fix

[http://ubuntuforums.org/showthread.php?t=939658&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=939658&highlight=BCM4306)

---

### Post by mjp29 on 2009-10-31
> **Bucky Ball said:**
> Router does NOT require special software.

Have you plugged in an ethernet cable? First thing to getting wireless happening is to make a wired connection and download all updates. This should pick up the card if it is going to and offer you the restricted drivers. They are not included in the install for legal reasons.

We can not give much more help without the details of the wireless card. If you don't know what it is open a terminal and run:

```
lspci
```You will find it toward the end of that list. You should also include the Ubuntu release you are using.

He has updated his version of Ubuntu with an ethernet cable [as far as he knows].  I'll have him go to update manager and double check.  His version of Ubuntu is the one before the very latest release days ago [jauntelope?].

When he types the code into terminal, this is what is reported:

Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by mjp29 on 2009-10-31
> **CylnZ said:**
> Probably has a BCM4306 chip. A lot of  hp zv6130us did

Do the lspci to check and if you do, here's a hardy - karmic fix

[http://ubuntuforums.org/showthread.php?t=939658&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=939658&highlight=BCM4306)

I will have him do the hardy karmic fix if you and folks on this forum please examine what lspci reported below and agree karmic fix is the thing to do.  See his terminal code below after typing lspci:

Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by karimruan on 2009-10-31
> 
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


That is your wireless card.  You are using an Airforce One 54g by Broadcom. Let me see if that is a supported card.

---

### Post by mjp29 on 2009-10-31
> **karimruan said:**
> That is your wireless card.  You are using an Airforce One 54g by Broadcom. Let me see if that is a supported card.

thanks for your assistance - we patiently await your reply

---

### Post by teward on 2009-10-31
There seems to be multiple issues with Broadcom cards and Ubuntu... seen these issues listed all over these forums.

I'm not sure if there's a fix for this issue yet, as I haven't really seen one posted yet.

---

### Post by mjp29 on 2009-10-31
> **TrekCaptainUSA said:**
> There seems to be multiple issues with Broadcom cards and Ubuntu... seen these issues listed all over these forums.

I'm not sure if there's a fix for this issue yet, as I haven't really seen one posted yet.


Do you think we should try the hardy karmic fix someone linked us to in this thread - it wouldn't hurt anything to try that would it?

If no one can find a fix, do you think it's a possibility to bypass the internal wireless in the computer and put a Linksys PCMCIA card in the side of the laptop to make it work with that same router.  If so, could someone suggest the type of Linksys card to look for or where they might sell the exact one we need.

Thanks

---

### Post by mjp29 on 2009-10-31
> **CylnZ said:**
> Probably has a BCM4306 chip. A lot of  hp zv6130us did

Do the lspci to check and if you do, here's a hardy - karmic fix

[http://ubuntuforums.org/showthread.php?t=939658&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=939658&highlight=BCM4306)


After doing an update manager update, he now can see other wireless networks in his neighborhood (all are password protected), yet when he tries to connect to his own personal wireless network with his password it says "connecting" then after a minute or 2 it says "disconnecting."

I will tell him to try the hardy karmic fix now and see what happens unless someone else has another idea.

I still think that perhaps him buying a pcmcia linksys card and bypassing his internal wireless hardware may do the trick to.

Or perhaps updating to the latest version of Ubuntu would do the trick, but being new there are some posts about problems with hardware (like printers) with it and he tends to want to wait a little while so the bugs can be worked out of it - but the fix may be built into it.

---

### Post by ublintu on 2009-11-01
Hi,
In my dell vostro 1000 I have BCM4328 802.11a/b/g/n (broadcom card). In the live CD System-administration-hardware drivers it was listed and I could get it work from the cd. After a clean install it wasnt in the hardware drivers list, but [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)   the first post solved my problem. My card is working now!

I have xpress 200m... It isn`t in the hardware list, but I installed the open source driver  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)    I didnt configure X.org and the other thigs under it. Am I need to? Compiz is working!

Good luck

---

### Post by ublintu on 2009-11-01
ahh I forget something: When I did my first clean install with karmic and when I solved my broadcom problem, reboot, a window come up with something like this: Do you want to report the problem with your kernel? - ok - blabla. I did an other install. After the second one, I didn`t have this. Now, at boot, before and after the white ubuntu logo, just for a sec I have black screen and the up left corner I can see this: _ 
Is it normal? Everyone has it? Exept this karmic is perfect and fast.

---

### Post by Bucky Ball on 2009-11-01
Plug in an ethernet cable and make sure you are online. 

System->Administration->Hardware Drivers. 

Anything in there for the Broadcom? B43 by any chance? Enable it if there is but take note: you must be online already for it to retrieve the wireless Hardware Drivers.

---

### Post by zclinux on 2009-11-01
Great thread, I wish I'd found this sooner. It took me a few days to find the hardware driver with the info posted above. Cheers

---

### Post by frprovis on 2009-11-01
> **Bucky Ball said:**
> Plug in an ethernet cable and make sure you are online. 

System->Administration->Hardware Drivers. 

Anything in there for the Broadcom? B43 by any chance? Enable it if there is but take note: you must be online already for it to retrieve the wireless Hardware Drivers.

What you want is the STA driver, not the B43. The B43 is older and doesn't work nearly as well as the STA package. Either the STA driver or Karmic 9.10 blacklists B43 in favor of STA. 

Obviously, you'll need a wired connection to download the STA driver using System->Administration->Hardware Drivers. Sort of catch-22 for people whose only connectivity option is wireless.

As for the original poster's concern about not wanting to upgrade until the bugs are worked out--you're still thinking in Windows terms. It is definitely better to upgrade Ubuntu to 9.10, which fixes many of the bugs in 9.04 and older releases. Install 9.10 and 9.04 side-by-side initially. If 9.10 works, then reinstall as a clean install (wiping out both the older 9.04 and the trial 9.10). Obviously, you'll need to back up your data before doing this. Upgrading, as opposed to clean install, is inadvisable, IMO, when you are having driver problems. Better to do a clean install of the fixed version.

---

