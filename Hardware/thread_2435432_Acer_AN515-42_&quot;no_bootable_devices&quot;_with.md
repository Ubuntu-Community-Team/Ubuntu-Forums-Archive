---
title: "Acer AN515-42 &quot;no bootable devices&quot; with linux drive."
date: 2020-01-20
forum: Hardware
---

### Post by allusernamestaken on 2020-01-20
So, I've got a 19.10 64 bit drive that is loaded with all of the OSS drivers needed to boot anything and does, except for this damn acer laptop because their UEFI is so broken it doesn't even give me options for legacy boot or AHCI settings. Apparently ctrl+s is supposed to show hidden options in the UEFI but it doesn't, so I'm currently left with this brick that only wants to boot Windows 10 when it apparently should by multiple other threads about it boot Ubuntu just fine.

If you need more info just tell me what you want.

I've got a parallel thread on Acer's site, but they are very Windows centric over there. [https://community.acer.com/en/discussion/comment/778592](https://community.acer.com/en/discussion/comment/778592)

---

### Post by CorporateMonkey on 2020-01-21
You should be able to open a boot menu during startup with F12 and choose to boot from your device.

---

### Post by CorporateMonkey on 2020-01-21
Also maybe this thread can help you [https://askubuntu.com/questions/904884/usb-not-shown-in-uefi-boot-option](https://askubuntu.com/questions/904884/usb-not-shown-in-uefi-boot-option)

---

### Post by yancek on 2020-01-22
I'm not clear about your setup.  Do you have 19.10 on a separate drive?  Is it a Legacy install or UEFI?  I don't use Acer but if this is a newer machine you will likely need to set a supervisor password in the BIOS firmware and set trust to enable booting other than windows 10.  See the 3rd post at the link below for more details.

 [https://ubuntuforums.org/archive/index.php/t-2400735.html](https://ubuntuforums.org/archive/index.php/t-2400735.html)

---

