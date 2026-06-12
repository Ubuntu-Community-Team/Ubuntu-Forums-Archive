---
title: "Ubuntu installation problem on my new laptop"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by ]Spectre[ on 2007-08-05
Hi to all.
I have just bought the following laptop:

ASUS X51R AP005A - Celeron M 520 / 1.6 GHz - RAM : 512 MB - HD : 80 GB - DVDÂ±RW / DVD-RAM - WLAN : 802.11b/g - Microsoft Windows Vista Home Basic - TFT 1280 x 800 ( WXGA 

I have burned the ubuntu 7.04 on the cd,the installation process starts,I get all [OK],but when the graphical interface starts,the system is halted. I can only move the mouse pointer on the screen.

I tried two times but with the same results

Can you help me please ?



thanks

---

### Post by wjp.reg on 2007-08-05
> **']Spectre[ said:**
> Hi to all.
I have just bought the following laptop:

ASUS X51R AP005A - Celeron M 520 / 1.6 GHz - RAM : 512 MB - HD : 80 GB - DVDÂ±RW / DVD-RAM - WLAN : 802.11b/g - Microsoft Windows Vista Home Basic - TFT 1280 x 800 ( WXGA 

I have burned the ubuntu 7.04 on the cd,the installation process starts,I get all [OK],but when the graphical interface starts,the system is halted. I can only move the mouse pointer on the screen.

I tried two times but with the same results

Can you help me please ?



thanks

Can we assume that you did not try running the Live CD before attempting an install?

Can you tell us more about the video driver in your system?

---

### Post by ]Spectre[ on 2007-08-05
Dear man,

No, I tried directly to install the ubuntu on the hard drive.
Is the live cd on the same install cd ?

thanks

The video board is an Ati xpress 1100

---

### Post by logos34 on 2007-08-05
try safe graphics mode, or hit F1 key for boot options.  Or download the text-mode Alternate install CD.

---

### Post by ]Spectre[ on 2007-08-05
Thank you,I'll try now.

See you later

---

### Post by wjp.reg on 2007-08-05
> **']Spectre[ said:**
> Dear man,

No, I tried directly to install the ubuntu on the hard drive.
Is the live cd on the same install cd ?

thanks

The video board is an Ati xpress 1100

The Live CD is a separate download and is helpful in determining what hardware hurdles might exist before you attempt an install.  You can also do an install from this disk or use the ´alternate´ disk.

---

### Post by ugm6hr on 2007-08-05
It might be helpful if you told us where you got the Ubuntu CD from if you don't understand what a LiveCD is.

I have a feeling that this might be helpful though:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

My laptop has an ATI Radeon Xpress1100 sticker on it, but it seems to be recognised as a 200M.  So I was OK booting from a LiveCD - but I gather most are not.

From my laptop (for interest):
```
lspci -nn
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]

```

---

### Post by ]Spectre[ on 2007-08-05
Dear Ubuntu users,

the problem was solved.

It was a bad iso file.

Thanks to all

Spectre

---

