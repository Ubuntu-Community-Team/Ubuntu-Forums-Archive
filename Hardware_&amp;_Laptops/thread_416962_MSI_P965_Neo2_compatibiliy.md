---
title: "MSI P965 Neo2 compatibiliy"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Halion on 2007-04-21
Has anyone had any problems running Edgy Eft or Feisty Fawn with MSI's [[color=blue]P965 Neo2 motherboard[/color]](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1163&maincat_no=1&cat2_no=170)? I am particularly concerned about the Marvell 88SE6111 which provides the PATA controller.

I would like to know because I have been considering this board for my new system.

---

### Post by Halion on 2007-04-23
So am I the first one here to contemplate this board?

---

### Post by Halion on 2007-04-27
OK, I decided to buy the motherboard together with an Intel E6320 Core 2 Duo processor and 2 gigabytes of RAM. I don't have any SATA devices, so I have to rely on the Marvell.

Having only a PATA DVD-RW drive connected to the Marvell and booting with the "64-bit PC (AMD64) desktop CD" I get the dreaded BusyBox.

What should I do now?

---

### Post by rezafab on 2007-07-25
I have the MSI G33M-FI that uses the same Marvell 88SE6111 for IDE and it is not recognized by Feisty. I hope you don't have the same problem but I still haven't found a solution to my problem.

---

### Post by tricky99 on 2007-08-06
See this thread for a possible workaround to get 88SE6111 working. Not sure yet if it applies to otehr distro's (will let you know ;-)  )

[http://ubuntuforums.org/showthread.php?t=490874&highlight=88se6111](http://ubuntuforums.org/showthread.php?t=490874&highlight=88se6111)

---

### Post by Halion on 2007-08-09
Thanks for the replies and the link. I ended up getting a SATA hard drive and booting with an external USB DVD-RW drive, but getting the Marvell to work would be nice as well.

---

### Post by xlinuks on 2007-08-17
I have bought MSI P965 Neo-F V2 and got the same problem as you did!
I hope this will get fixed in Gutsy.

ps: The issue is that when installing Feisty Fawn I'm getting a blank screen after selecting "Start or install Ubuntu" with the following lines:
----------------------------------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu1) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs) _
----------------------------------------------------
Gutsy Gibbon Alpha 4 yields same results.

---

### Post by forger on 2007-09-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/138046](https://bugs.launchpad.net/ubuntu/+bug/138046) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same here, I filed a bug at ubuntu launchpad, the pata controller is not working, even in gutsy tribe 5 :( MSI P965 Neo2-FI

---

