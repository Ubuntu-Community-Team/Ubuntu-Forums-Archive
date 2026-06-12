---
title: "Help me sell my wife on the linux option.."
date: 2008-09-12
forum: Hardware
---

### Post by Dasien on 2008-09-12
Okay I want to make the switch from Microsoft to Linux on my Toughbook cf-29. I have to sell this to my wife and show her that Linux is a reasonable option so long as every thing works and she can find where everything is at.
My problems are the Touch screen is all screwy, I have seen that it can be fixed just not specifically how. Also I can't get any sound to work and last but not least the DVD I can't get it to read DVDs. 
Thank you guys for any of your suggestions
Nick

---

### Post by EDH1981 on 2008-09-12
test

---

### Post by cariboo on 2008-09-12
Have you had a look at this howto:

[http://www.musicinfo.org/node/61#s6](http://www.musicinfo.org/node/61#s6)

for help with your touchscreen.

For help with your soundcard could you post the output of:

```
lspci
```

in your next post.

Jim

---

### Post by knattlhuber on 2008-09-13
My girlfriend loves her Mac and the only way I could get her interested in Linux was when I got a new router and her Mac wouldn't connect to the internet anymore... and she started using on of our Ubuntu laptops. But then I fixed the wireless issue and it was back to Mac :)

Anyways. The reason your DVDs aren't playing might be just because of missing codecs. There is an excellent Multimedia HOWTO that shows you what to install for the full audio/video experience under Linux
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

HTH

---

### Post by Dasien on 2008-09-13
Hello Jim
Here is the read out
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
Thanks for the help
Nick

---

