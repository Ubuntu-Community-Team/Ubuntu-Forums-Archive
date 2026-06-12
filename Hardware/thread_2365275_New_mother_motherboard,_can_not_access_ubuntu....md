---
title: "New mother motherboard, can not access ubuntu..."
date: 2017-07-04
forum: Hardware
---

### Post by sardonic2 on 2017-07-04
Hi, I have a  Dell inspiron 15 5000series/ windows 10. For audio problem  they changed the motherboard, of course now it will boot to windows  ignoring ubuntu. See the picture below (1) the ubuntu partition #6 300gb is  grey out the only option is the delete one.The grub page is gone and  ubuntu is not showing either in the boot sequence(2)

I've tried  to boot the usb ubuntu iso file with (try version) did a boot repair but  it failed, the usb needs to be efi not legacy boot mode... I did the  rufus version for usb bootable in uefi mode, will this do the fix?

In  the bigger picture why having windows in uefi and cd/dvd/usb in  legacy(3) and will it cause any problem for new ubuntu re installation?

Thank you.


[ATTACH=CONFIG]275861[/ATTACH] [ATTACH=CONFIG]275862[/ATTACH][ATTACH=CONFIG]275859[/ATTACH]

---

### Post by slickymaster on 2017-07-04
*Thread moved to **Hardware**.*

---

### Post by sardonic2 on 2017-07-04
Got it, thanks.

---

### Post by sardonic2 on 2017-07-05
For info, the rufus version is not working!

---

### Post by sardonic2 on 2017-07-26
I have solved my problem here! In the Bios settings, I unticked the legacy (rom) option so the usb  flash drive is now bootable in UEFI mode making windows visible again...That  simple.

---

### Post by lisati on 2017-07-26
> **sardonic2 said:**
> I have solved my problem here! 

Please mark the thread solved by using the option on the "Thread tools" menu near the top of the page.

---

