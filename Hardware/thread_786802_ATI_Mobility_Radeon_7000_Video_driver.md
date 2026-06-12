---
title: "ATI Mobility Radeon 7000 Video driver?"
date: 2008-05-08
forum: Hardware
---

### Post by ninja82 on 2008-05-08
Hi,
Upgraded to 8.04. Lost the desktop cube / eye candy. Everything was working fine before the upgrade (cube, wobble windows, etc.). It seems like I had to install a special driver (not fglrx) in order to get things to work way back when, but can not remember what it was. Can anyone help me out? I have gone looking for an old ati driver but can't seem to find the one for my card.
Thanks for any advice...
Here are some details:
 lspci
00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP
02:04.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by vavoem on 2008-05-08
Like me with a radeon 9000 you are screwed
i bet you were using 7.04 which supported the radeon 9000 and 7000 in the ati propietary driver but it does not any longer

I wander if there is a way to use the 7.04 propieatary driver Does anyone know?
Graphics are really dreadfully slow with the opensource one.

lspci |grep ati
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

---

### Post by ninja82 on 2008-05-08
This is a shame - I thought linux was about keeping old hardware alive and running???
If I wanted to upgrade my hardware every time I updated the operating system I would have kept microsoft on!
Anyone know if there is a way to "downgrade" back to 7.04? The only reason I don't start from scratch is because I have paid $$ for several programs (mathematica / maple) and I don't want to have to reactivate them (the vendors make it a pain - proving student status etc...).
Thanks...

---

### Post by Ususbuntung on 2008-05-08
I managed to make my T41 (Radeon RV250 FireGL 9000) to have compiz working, using 8.23 driver (installed with EnvyNG), but only for screen resolution of 1024x768. It is not quite right either, because I cannot see the window title, becomes white although buttons function. I got after using the option SKIP_CHECK for the configuration, please google in the launchpad bug.

Cheers

---

### Post by vavoem on 2008-05-11
could you post your xorg.conf for me?

---

### Post by viperf117a on 2009-01-23
I have Toshiba Satellite Notebook A60-166 with on board ATI Mobility Radeon 7000 with 32MB of shared video memory. I have installed Ubunutu Server 8.04 and Ubunutu-desktop with updates. 

My question here is is there a ATI Radeon driver that supports or has supported the Radeon 7000 Chipset ? I have successfully configured X11 to use separate LCD displays (HPw1707) however 
I cannot get a resolution higher than 1024 X 768. Any suggestions or ideas on a driver that might work with this ? 

I know that 7.04 supported that graphics card however I do not wish to downgrade my current install. 

Thanks in advance ! :KS

---

### Post by jocko on 2009-01-23
> **viperf117a said:**
> I have Toshiba Satellite Notebook A60-166 with on board ATI Mobility Radeon 7000 with 32MB of shared video memory. I have installed Ubunutu Server 8.04 and Ubunutu-desktop with updates. 

My question here is is there a ATI Radeon driver that supports or has supported the Radeon 7000 Chipset ? I have successfully configured X11 to use separate LCD displays (HPw1707) however 
I cannot get a resolution higher than 1024 X 768. Any suggestions or ideas on a driver that might work with this ? 

I know that 7.04 supported that graphics card however I do not wish to downgrade my current install. 

Thanks in advance ! :KS

Ati's proprietary driver (fglrx) has never supported radeon 7000 (the earliest versions of it supported cards from radeon 8500 and up, but support for anything below radeon 9500 was dropped a little bit more than two years ago).
So the open source driver (radeon) is the only driver that supports such old cards.
The radeon driver have no problems running higher resolution than 1024x768, you probably need to set up your monitor section in xorg.conf properly to be able to set the resolution higher.

---

