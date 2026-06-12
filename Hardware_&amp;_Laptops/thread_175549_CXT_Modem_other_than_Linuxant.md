---
title: "CXT Modem other than Linuxant?"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by netejr_v on 2006-05-13
I have a Compaq Presario with Ubuntu 2.6.10-5-386 and it's got a Conexant winmodem. After some trouble I managed to install the free linuxant driver. When I try to connect with the Networking tool and then try "Modem Connection" it says connection is active, but I'm not connected; but then I did *sudo wvdial* and it worked ( I tried to install a smartlink driver earlier without success ). 

Is there a way to use the Networking tool to connect instead of opening a new terminal every time and doing *sudo wvdial*?

Are there any known free modem drivers that give 56 Kbps for this?

p.s. Newbie to Linux, so be gentle. :D

---

### Post by chettyk on 2006-05-13
LIke you, I have used a Linuxant modem driver. I have opted to stick to the 'sudo wvdial' route. I find that it works fine for me and haven't bothered with the Networking tool.

My understanding is that there are open-source drivers available for many such modems; but I haven't tried them.

Maybe this entry in Ubuntu Wiki might interest you:
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF)

Sorry that I couldn't be of more help.

---

### Post by netejr_v on 2006-05-14
[QUOTE=chettyk]Maybe this entry in Ubuntu Wiki might interest you:
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemConexantHSF)
[/QUOTE]
Yes I've read that wiki. I went along with its instructions. It says there aren't any free Conexant drivers.

[QUOTE=chettyk]My understanding is that there are open-source drivers available for many such modems; but I haven't tried them.[/QUOTE]
Do you know any place where I can donwload such drivers?

---

### Post by chettyk on 2006-05-15
[QUOTE=netejr_v]
Do you know any place where I can donwload such drivers?[/QUOTE]

Nope. But I vaguely remember reading a post somewhere in this forum about how it was possible to get such drivers. I didn't bother to follow up; I decided that I'd rather pay Linuxant's license fee.

---

