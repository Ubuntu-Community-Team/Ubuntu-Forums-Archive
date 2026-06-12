---
title: "Black screen after installing Nvidia binary driver on Ubuntu 12.04."
date: 2013-10-01
forum: Hardware
---

### Post by x10n2 on 2013-10-01
As stated in the title, I get a black screen after installing the Nvidia binary driver from 'Additional Drivers' under System Settings. The Nouveau driver also crashes on starting the Unity desktop from a LiveUSB (unless booted with the 'nomodeset' option). The card in question (a GeForce 8800 GTS 320MB) works just fine on Windows XP Pro, so I know it's not a faulty card.
When I reboot after installing the Nvidia binary driver, and am presented with the black/blank screen, I can't even get to a command prompt via CTRL+ALT+F1. I can only get to it by holding down shift at boot to bring up the Grub menu, then selecting recovery mode, *then* selecting continue with normal boot. This allows me to get to the command prompt via CTRL+ALT+F1, but trying to kill and restart the LightDM service via; [PHP]sudo service lightdm stop && sudo service lightdm start[/PHP] just brings me to a black/blank screen again - albeit one I can actually CTRL+ALT+F1 back to the prompt with.

I'm currently running via the onboard Intel 915GV graphics chip which functions fine, but is unable to play anything on Steam as it's far too underpowered for that...

ANY help would be very much appreciated with this issue. I've tried searching Google, but unfortunately none of the posts I've found have yielded a working answer! :(

---

### Post by x10n2 on 2013-10-02
Bump..

---

### Post by papibe on 2013-10-02
Hi x10n2.

Have you tried booting your installation with the nomodeset option, as you did with the Live CD?

This [thread]("http://ubuntuforums.org/showthread.php?t=1613132") describe how to set the option both temporarily or permanently.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by x10n2 on 2013-10-02
No I haven't, but I would prefer any suggestions that didn't include borking my install. With the Nvidia driver installed I cannot boot to a prompt or desktop on the Intel 915GV chip. If possible I would like some ideas that didn't include having to install from scratch yet again! =)

---

### Post by papibe on 2013-10-02
Booting with nomodeset won't damage your system, as the worst it could happen is getting a black screen again.

Regards.

---

### Post by x10n2 on 2013-10-02
I'll try..

---

### Post by x10n2 on 2013-10-02
Yeah, now it's all kinds of messed up. I can't even login to my account now as it throws me back to the login screen. I can only access anything via Guest Account. I think I'll roll back to an older version of Ubuntu or Windows XP. This is ridiculous.

---

