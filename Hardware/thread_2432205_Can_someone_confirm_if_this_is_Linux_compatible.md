---
title: "Can someone confirm if this is Linux compatible?"
date: 2019-11-28
forum: Hardware
---

### Post by msjackieelle on 2019-11-28
[COLOR=#1A1A1B][FONT=&amp]We need to replace a laptop, and we found one on sale tomorrow (Black Friday Door Crasher). My gf uses Kubuntu/Mate for her work (basic graphics & writing). I think the specs should give her lots of room to grow, but also most bang for the buck!
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]The system we are looking at is an [MSi GL65 9SE-055CA with RTX 2060]("https://www.canadacomputers.com/product_info.php?cPath=710_1894_1897&item_id=140949"). Are there any known issues with installing a *buntu (I know I will probably have to upgrade BIOS first off). I have looked through the "compatible" and not compatible lists here, along with searching various versions of the product name.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Thanks in advance.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]*~Jackie*[/FONT][/COLOR]

---

### Post by CatKiller on 2019-11-28
Optimus (using both Intel & Nvidia graphics) can be a complete pain. It might work well right away, or it might be a complete nightmare. It's set to get a bit easier in the future, but not yet. You'll definitely need a recent driver for the Turing part. 

The Intel wireless will probably be fine; Intel are heavily invested in open source software and they have the resources to get timely support included before their hardware is released.

I have no idea if the audio will work at all. It's some MSI-branded "value add" nonsense, and they've got no interest in supporting Linux. Someone might have reverse-engineered whatever quirks it has in order to get it working, or they might not.

---

### Post by oldfred on 2019-11-28
Often issues are common by brand. And then similar models have similar issues.
Bigger differences if AMD or Intel based.

Similar models:
       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)

---

### Post by todd-meade-gmail on 2019-12-01
> **msjackieelle said:**
> [COLOR=#1A1A1B][FONT=&amp]We need to replace a laptop, and we found one on sale tomorrow (Black Friday Door Crasher). My gf uses Kubuntu/Mate for her work (basic graphics & writing). I think the specs should give her lots of room to grow, but also most bang for the buck!
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]The system we are looking at is an [MSi GL65 9SE-055CA with RTX 2060]("https://www.canadacomputers.com/product_info.php?cPath=710_1894_1897&item_id=140949"). Are there any known issues with installing a *buntu (I know I will probably have to upgrade BIOS first off). I have looked through the "compatible" and not compatible lists here, along with searching various versions of the product name.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Thanks in advance.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]*~Jackie*[/FONT][/COLOR]

I'm running replying from Ubuntu (PopOS derivative) on that model I picked up on Black Friday from Canada Computers.

I haven't dug into how get Nvidia card/driver working with the Intel/Nvidia Optimus card (yet)

Audio, WiFi and LAN all working fine for me.

---

### Post by todd-meade-gmail on 2019-12-01
Ok, got the Nvidia driver installed and working fine too.

---

