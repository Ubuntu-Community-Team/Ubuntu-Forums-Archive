---
title: "Modem Use on Dell Inspiron 6000 laptop with Feisty"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by mrund on 2007-07-10
I could use some help getting in touch with the modem on my Dell Inspiron 6000 laptop running Feisty.

Scanmodem suggests that the modem is an "Intel Corporation 82801FB/FBM/FR/FW/FRW". A Google search indicates that this info may actually refer to the sound card, but I don't know.

I realise that the first step is to find out what chipset the thing uses. lspci reports that the modem is not an Intel536EP one.

The modem works fine under WinXP and allows seamless internet connection there.

Any suggestions?

---

### Post by phidia on 2007-07-10
It's good that you used the scanmodem tool. Have you gone to the linmodem site there is a lot of info there.
[http://www.linmodems.org/](http://www.linmodems.org/) Since you have the scanmodem software maybe you've already been there. There is also info here [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) for setting up a dial-up modem.

You may have an unsupported (winmodem ) however and even if it is supported getting winmodems ( which are really modems designed to work through the windows os software and be produced cheaply ) to work can be time consumming and even a little difficult. You probably can get an external hardware modem very reasonably, and it's what I recommend.

---

