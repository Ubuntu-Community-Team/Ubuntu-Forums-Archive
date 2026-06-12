---
title: "trying to turn off secure boot"
date: 2015-02-14
forum: Hardware
---

### Post by DougieFresh4U on 2015-02-14
I got a new computer a while back that came with Windows 8.1 installed.
I want to use my beloved UBUNTU but seem to be having problems turning off 'secure boot'.
I followed the steps given [here ]("http://itsfoss.com/disable-uefi-secure-boot-in-windows-8/")
and I am not getting the 'UEFI utility'
I am not sure if I have an  ARM pc
the pc is:
[B]AMD A4-5000 APU
Quad core[/B]
I have read that it's not possible to change secure boot on ARM pc's
Could some one please help with what ever I am not getting right?
Thanks

---

### Post by carl4926 on 2015-02-14
Check
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by DougieFresh4U on 2015-02-14
Thanks, I've managed to get secure boot disabled.
I am trying to make room on my hard drive now, which is 1TB but it
appears that it's already chopped into 4 'blocks'
and the only one that it will let me change is the 
windows 919 GB
[ATTACH=CONFIG]259963[/ATTACH]

---

### Post by carl4926 on 2015-02-14
Windows 8 is probably, almost certainly, no it must be GPT table and UEFI enabled, given what we know from you already said.
And you should look carefully at the requirements. Because I'm pretty sure it will need to remain in EFI mode and Linux must be installed in EFI mode.
It will need to shrink your windows install in order to create the necessary partitions.
Always backup important files first.

---

