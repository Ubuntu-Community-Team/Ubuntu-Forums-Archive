---
title: "asus n90sv - hard freeze - possibly BIOS or ACPI problem?"
date: 2009-11-10
forum: Hardware
---

### Post by mimmozzo on 2009-11-10
Hello,

a friend of mine has an Asus n90sv laptop... I've tried to install Ubuntu 9.10 on it and there's a freeze issue... I guess could be an ACPI or BIOS problem, coz seems to go away when putting acpi=off at boot. I just wanna know if there's everyone else experiencing these problems with this laptop, and if anyone found a solution... googled it, but no luck.

The freeze usually happens after installation, when trying to install language packs. Then I've to reset the machine, and language-selector does not work anymore... that's very annoying ](*,)

To those who can give me some advice, thanks in advance :)

---

### Post by tomashpl on 2009-11-16
I have had the same problem. This bug depends on built-in wifi card and network-manager, so if You want to fix it You should plug ethernet cable into wired card, connect with **wired** internet, run terminal and type:

sudo aptitude install wicd

after that network-manager will be removed and wicd will be installed.
For now You can connect to WLAN without any issues

Sorry for my english ;) 
I hope it will works :)

---

### Post by tomashpl on 2009-11-17
> **tomashpl said:**
> if You want to fix it You should plug ethernet cable into wired card, connect with **wired** internet

And if You want to do this, probably You should type in Your /etc/rc.local the following line:

ifconfig eth0 mtu 1492

'cause SiS LAN card's driver is buggy too. 
Have a nice day :)

---

### Post by Sylslay on 2009-11-17
thomaspl, your English is perfect!
I think so.

---

