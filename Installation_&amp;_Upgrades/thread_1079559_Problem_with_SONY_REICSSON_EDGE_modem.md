---
title: "Problem with SONY REICSSON EDGE modem"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by shanto_eee on 2009-02-24
Problem with SONY REICSSON EDGE modem 
hi 
i am trying to use a SONY ERICCSSON EDGE MODEM in UBUNTU

It is connected to 32bit cardbus of my laptop. it was okay in windows xp.
now when i connect it and in terminal i write

lspci
is shows :
------------------------------------------------------------------------
shanto@shanto:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/.................................................. ..........
.................................................. ................
.................................................. ................
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
07:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 03)
07:00.1 Serial controller: Broadcom Corporation EDGE/GPRS data and 802.11b/g combo cardbus [GC89] (rev 03)
shanto@shanto:~$ 
----------------------------------------------------------------------

when i type 
------------------------------------

shanto@shanto:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
shanto@shanto:~$ 
------------------------------------

when:
------------------------------------------------------------------------
shanto@shanto:~$ pccardctl ls
Socket 0 Bridge: [yenta_cardbus] (bus ID: 0000:06:06.0)
shanto@shanto:~$ 
------------------------------------------------------------------------
how shud i configure my EDGE modem for UBUNTU?

---

