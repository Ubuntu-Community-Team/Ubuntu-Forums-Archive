---
title: "Toshiba Satellite A70 Hardware"
date: 2009-04-30
forum: Hardware
---

### Post by irvingleonard on 2009-04-30
There is a little diference with toshiba site compared to ubuntu linux kernel, maybe it is important maybe not.
The toshiba web says that my Toshiba Satellite A70 model PSA70C-DD100E ([http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=3150&part=2631#spectop](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=3150&part=2631#spectop)) has an Ati Mobility Radeon 9000 IGP, it also use to have a sticker that checks it; however the lspci command in kubuntu jaunty (and hardy too) says that it have an ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]. The question is: who's mistake?
here is my lspci -nn output
00:00.0 Host bridge [0600]: ATI Technologies Inc RS300 Host Bridge [1002:5831] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:13.2 USB Controller [0c03]: ATI Technologies Inc EHCI USB Controller [1002:4345] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 18)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
00:14.6 Modem [0703]: ATI Technologies Inc IXP AC'97 Modem [1002:434d] (rev 01)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]
02:02.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)

---

