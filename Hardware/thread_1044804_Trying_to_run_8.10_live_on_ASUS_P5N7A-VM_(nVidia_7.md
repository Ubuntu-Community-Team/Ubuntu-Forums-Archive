---
title: "Trying to run 8.10 live on ASUS P5N7A-VM (nVidia 730i chipset)"
date: 2009-01-19
forum: Hardware
---

### Post by king minger on 2009-01-19
Hi all

I'm trying to get 8.10 up and running on the above MB however, trying to run the Live CD, I keep getting the following error looping:

```
[nn.nnnnnnnn] end_request: I/O error, dev sr0 sector 1431184
[yy.yyyyyyyyy] buffer I/O error, dev sr0, logical block 178898
```
nn.nnnnnnn and yy.yyyyyyy are long numbers

This goes away if i disable the SATA controller in the BIOS (up to date v.0407) which is unfortunate as i want to install to a SATA drive and the DVD ROM is SATA too. if I change the SATA mode to AHCI it makes no difference.

to make sure it's not the MB, the board runs fine under WinXP, Win7 Beta build 7000, XBMC live (based on ubuntu 8.04 - which also doesn't work live) and Knoppix live 5.3.1.
in knoppix, i looked at the device list and it showed the appropriate hard drive and DVD ROM on scsi_host -> scsi_generic and it's running 2.6.24.4 kernel.

any help would be much appreciated, even if it's just that i need to get the alternate install CD/DVD.

Thanks

---

### Post by stdPikachu on 2009-01-20
On my board there's a BIOS option called something like "Change AHCI DID for Linux" - I've no idea what it is or does, but I left it off (default) and my rolling upgrade worked - but it might have summat to do with booting from a SATA CD.

Which SATA controller is your CD plugged in to? The nVidia (red ports) or the JMicron (black ports)?

---

### Post by king minger on 2009-01-20
hi pikachu

i have played with those settings to no avail, but without any real explanation of what they are, i have left them as they were.

the drives are all plugged into the red ports- 0 and 1

---

### Post by king minger on 2009-01-20
Ok, I found the problem....
Impatience!

i tried 8.04 and got a similar error but regarding fd0 instead of sr0

however after about a minute, it took off and went in smoothly.

so i tried the same in 8.10 and after nearly 10 mins, it booted up, able to see and access all the drives!

so i don't know what the problem is/was, but it gets there eventually.

---

