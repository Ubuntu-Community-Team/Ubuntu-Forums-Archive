---
title: "hardware conflict of ATI mobility 5470 with intel HM57 chipset?"
date: 2010-07-17
forum: Hardware
---

### Post by chairman.nirvana on 2010-07-17
Yesterday I met a critical problem when doing routine work under Ubuntu desktop 10.04 on my laptop. That is:
Suddenly, the screen seems no-responding, and pressing Ctrl-Alt-F1 could not let me enter Terminal mode. I had to hard-reboot the laptop. The worse thing showed up, that the screen had some green points blinking on it, and as the time went on, more and more green points appeared, even during bios POST phase. And Ubuntu system could not be entered as normal.
I could still enter WinXP (VGA mode or Safe mode), but not for normal mode, which would enter blue-screen crash mode and reports a hardware driver error of ATI card. And the green points are always there in the screen.

This problem continues till right now.

My laptop's hardware is as below:
- Brand: Dell Inspiron N5010
- CPU: intel i3-350m
- Memory: 2G DDR3
- Chipset: Intel HM57
- VGA: ATI mobility 5470 HD

It's said that HM57 chipset has an embedded intel graphics accelerator with it. And Win7 system supports display-switching function(but WinXP not supports). Is it a clue that the ATI 5470 might conflict with the embedded graphic accelerator under Ubuntu?
And if anyone meets same problem or has any solution for this problem, thanks in advance to bring any help.

I've posted a question at launchpad request, at [https://answers.launchpad.net/ubuntu/+question/118024](https://answers.launchpad.net/ubuntu/+question/118024).

---

### Post by chairman.nirvana on 2010-07-18
And I've recalled that in Win7, when I tried to install Intel Graphics Accelerator driver for Dell N5010 which was downloaded from Dell official website, it reported fail because of "not fulfill necessary requirements".
It seemed that N5010 had no internal graphics accelerator within its HM57 chipset (or has masked it out), so that the crash down in Ubuntu should be due to something wrong with the ATI 5470 driver. 
My ATI display driver in Ubuntu 10.04 is auto-installed, with Ubuntu's System Menu: Administration=> Hardware Drivers.

---

### Post by chairman.nirvana on 2010-07-18
And I've recalled that in Win7, when I tried to install Intel Graphics Accelerator driver for Dell N5010 which was downloaded from Dell official website, it reported fail because of "not fulfill necessary requirements".
It seemed that N5010 had no internal graphics accelerator within its HM57 chipset (or has masked it out), so that the crash down in Ubuntu should be due to something wrong with the ATI 5470 driver. 
My ATI display driver in Ubuntu 10.04 is auto-installed, with Ubuntu's System Menu: Administration=> Hardware Drivers.

---

