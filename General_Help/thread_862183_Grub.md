---
title: "Grub"
date: 2008-07-17
forum: General Help
---

### Post by Tisy0 on 2008-07-17
Hi,
Recently I installed Kubuntu and overwrote Windows XP or it made kubuntu boot first or something.

I kept getting the error Grub Loading Error 17 after I formatted the hard disk..

So I formatted it again and I still get the same error..

Can somebody help? All I want to do is install Windows XP instead of Kubuntu,

I checked that the Hard Disk was wiped on another computer but I still get the error

Thanks,
Tisy0

---

### Post by Taxman415a on 2008-07-17
I don't get it. If all you want to do is install XP, it will overwrite the MBR with it's own bootloader and thus wipe out grub. So just go ahead and install.

I don't know what error 17 is off the top of my head, but if you'd like to solve it to set up a dual boot system in the future feel free to ask here.

---

### Post by Tisy0 on 2008-07-17
I have 2 recovery CD's I place NO.1 in when it starts up.. it goes through the process of Cleaning the hard drive, Then place CD NO.2 in and it installs windows..

Then I reboot and it simply comes up with Grub loading stage 1.5
Error 17

I now installed ubuntu to request some help, Ubuntu installs fine,
I have dual boot and when I click Windows NT/Vista/XP/2000 (loader)
It comes up saying something like General Protect~
Then loads of random ****:confused:

I downloaded wine and followed all the steps etc and I place the Wndows XP disc in.. Press install and it gets stuck and crashes on the first step of installing windows xp!!!! (Collecting information)

All I want to do is put Windows XP on the computer Without Ubuntu

It wont bother me if Ubuntu IS on there but i'd like Windows XP to work otherwise i'll have to buy a new computer if I get no help :/

Thanks,
Tisy0

---

### Post by bodhi.zazen on 2008-07-17
The windows CD should fix the MBR.

See also Windows Boot Disk:
    [http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)

The other option is to re-install Kubuntu and configure kubuntu to boot windows.

The third option is to install the windows boot loader from windows.

Knoppix will do this. Boot Knoppix and :

```
sudo install-mbr /dev/hda
```

---

