---
title: "Will Ubuntu run on ThinkPad 10, a Bay Trail-T tablet?"
date: 2014-09-03
forum: Hardware
---

### Post by Nickolai_Leschov on 2014-09-03
I would like to be able to run Ubuntu on [ThinkPad 10]("http://shop.lenovo.com/us/en/tablets/thinkpad/thinkpad-10/"), a tablet with a Bay Trail-T Intel Atom chip.

Will Ubuntu work on this computer?

---

### Post by Nickolai_Leschov on 2014-10-31
Still no information? Anyone?

---

### Post by oldfred on 2014-10-31
The issue was that configurations used 32bit UEFI and there was no 32bit Linux UEFI. And they were updated or changed to UEFI class 3 which has no BIOS boot mode.

The only Bay Trail info I have seen:
Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
 [http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
 ASUS Transformer Book T100TA that was one of the early Intel Bay Trail convertible laptops/tablets. 
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

---

