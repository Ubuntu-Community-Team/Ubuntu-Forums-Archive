---
title: "bluetooth not working in 10.10"
date: 2011-05-08
forum: Hardware
---

### Post by akos.maroy on 2011-05-08
Hi,

I can't seem to be able to get bluetooth working on my HP Evny 15 laptop, with Ubuntu 10.10 64 bit.

When I go for System -> Preferences -> Bluetooth, I see a big 'Turn on Bluetooth' button. I press it, it gets disabled for a while, and then nothing else happens. at the same time, I get the following in syslog:

```
May  8 09:32:45 tonkachi kernel: [  693.330516] ACPI Error: Needed [Buffer/String/Package], found [Integer] ffff880233a47d38 (20100428/exresop-590)
May  8 09:32:45 tonkachi kernel: [  693.330530] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20100428/dswexec-460)
May  8 09:32:45 tonkachi kernel: [  693.330544] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880236c590e0), AE_AML_OPERAND_TYPE
May  8 09:32:45 tonkachi kernel: [  693.330657] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880236c591e0), AE_AML_OPERAND_TYPE

```

bluetooth used to work well with 10.04 and 09.10.

all help would be welcome.


Akos

---

### Post by Zingam on 2011-05-08
[http://ubuntuforums.org/showpost.php?p=10785910&postcount=2](http://ubuntuforums.org/showpost.php?p=10785910&postcount=2)

Check this above. Google for more info.

I have HP ProBook 4320s and I've managed to make it work. It's not nice solution but at least it does work.

---

### Post by akos.maroy on 2011-05-08
> **Zingam said:**
> [http://ubuntuforums.org/showpost.php?p=10785910&postcount=2](http://ubuntuforums.org/showpost.php?p=10785910&postcount=2)

Check this above. Google for more info.

I have HP ProBook 4320s and I've managed to make it work. It's not nice solution but at least it does work.

thanks for the pointer. restarting the bluetooth service doesn't make it work, as rebooting doesn't either. I've been google-ing around, found a few bug reports on launchpad, but nothing conclusive :(

this is annoying, bluetooth used to work fine in previous ubuntu releases...

---

### Post by Meghana H on 2011-05-26
Hello eveyone...
I have the same problem here..
 im using ubuntu 10.10 and when i connect the bluetooth USB dongle n click preferences, it says "bluetooth disabled".. even after rebooting, its not working..
Please help .

---

### Post by mouhammad88 on 2011-10-09
After a long wasting time in complicated tuto and tips , i found an easy magic solution :D look at this : [http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/](http://www.edwardcrosby.com/2011/06/17/bluetooth-fix-in-linux-mint-11ubuntu-11-04/)

---

