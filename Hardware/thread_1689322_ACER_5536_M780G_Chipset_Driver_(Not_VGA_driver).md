---
title: "ACER 5536 M780G Chipset Driver? (Not VGA driver)"
date: 2011-02-16
forum: Hardware
---

### Post by ario on 2011-02-16
Hi all,
I installed Windows 7 and Ubuntu 10.04 on my Acer Aspire 5536 laptop.
Without those proprietary drivers provided by Acer.com temperature of CPU, GPU and HDD were too High. about 60 degrees. Installed All drivers from ACER site for windows and it reduced temperatures there. Also reduced power usage and thus longer battery duration.
ACER does not provide any driver for Linux. So I searched AMD.com site. There I only found a driver for my VGA. It reduced Temperature of the GPU from 60~70 down to 40 to 50.
I didn't find the M780G driver and now my Hard-drive and South Bridge chip (SB700) are too high under linux only and I can't continue using my laptop on linux because HDD temperature goes up to 62C!
What can I do to solve this problem? 
----------------------------------------------
PS: On ACER 5536 HDD is installed right under south bridge chip. So that temperature of one affects the other.
PS: CPU,GPU,HDD under windows: 40,45,40 (All drivers installed)
CPU,GPU,HDD under linux: 40,45,62 (Only fglrx driver installed)

---

### Post by ario on 2011-02-17
Bump!

---

### Post by ario on 2011-02-27
Bump!

---

### Post by Kilz on 2011-10-03
I know this is an old thread, but I am placing this info on the forums in case others needs it.
I inherited a Acer Aspire 5536 and, of course I put linux on it immediately to replace the Windows Vista that was running slow as molasses in January. But the temperature was running real hot, topping out at 80c. Here is what I did.

1. I updated the bios using a [ freedos usb stick]("http://samiux.blogspot.com/2010/06/howto-make-bootable-freedos-usb-dongle.html") and the latest bios from acer. 
2. I updated the video driver manually to the [latest ATI drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually"). 

That got the laptop down to the 65-70c range, still to hot. The next move is not fort the faint of heart or those that lack the ability to follow directions to the letter.

3. I disassembled the laptop  using a [pdf of the service manual]("http://www.azbooki.ru/literatura.php?name=instrukcii-po-razborke-noutbukov-acer.txt"). Cleaned the fan and the old thermal paste, then applied new thermal paste to the cpu and gpu. 

This got the laptop down to the 60c range at idle.
This next step is really not for those that fear change. I do not suggest everyone is capable of this step. Do it at your own risk.

4. I found this thread on a forum on [air flow in the Acer Aspire line]("http://forum.notebookreview.com/acer/481690-acer-5738g-bottom-vent-built-closed.html"), and drilled out sealed air vents in the laptop case after disassembling it again. The laptop now idles at 46c and had a temp of 65c under heavy load.

---

