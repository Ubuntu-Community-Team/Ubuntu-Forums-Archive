---
title: "Screen Brightness Control"
date: 2009-06-26
forum: Hardware
---

### Post by cneil on 2009-06-26
Hello,
I'm running Jaunty on a Dell Studio 1737 Laptop with an integrated graphics card.  

The screen brightness control looks like it is working, but nothing happens.  When I hold the function button and the down arrow and attempt to decrease the brightness, the meter lowers like it is supposed to be the screen brightness remains constant.  I think it, randomly, worked properly once, but it didn't work after my initial install and it isn't working now.

Anyone have any suggestions?  Thanks.

---

### Post by Logorrhoe on 2009-07-05
I have a suggestion!  open /boot/grub/menu.lst with an editor (you need root rights)  search the line "defoptions=" and add "acpi=force"right behind.  After a reboot everything worked for me, brightnesscontrol, ac-adapter events (when removed) on my Dell Studio 1555  Hopes it works for you,  Logorrhoe

---

### Post by nishant.singh28 on 2009-07-06
I have a Studio 1555(ATI Radeon HD4570 512 MB) with dual boot( vista home premium and ubuntu 9.04 ). I use easyBCD 2.0 Beta build 63 to keep Vista in control. At startup, I have noticed a message that there is some error in ACPI but it is displayed too briefly for me to read. I tried to modify the defoptions as mentioned in both the original menu.lst and the menu.lst used by Neogrub but still I am unable to change the screen brightness. I also tried to add this option to the kernel line while booting.That took care of the acpi error message but the brightness problem stays. I have the proper display drivers installed.. Please help as the brightness is blinding!!!:confused:

---

### Post by bucik85 on 2009-07-07
I tested to add "acpi=force", but it didn't work. As well I tested other options:[LIST]
[*]"acpi=force nolapic" - didn't work;
[*]"acpi="off" - I been able to change brightness, but no battery status and other options;
[*]"noapic" - it's work on my Dell Studio 1555.
[/LIST]
I added to menu.lst:```
# defoptions=quiet splash noapic

```
and after used "update-grub" as root and reboot.

---

### Post by cneil on 2009-07-09
Thanks!
This fixes the screen brightness control issue for me! 

However, I think on this setting, the fan runs a little more.

My Dell 1737 rocks with Ubuntu!

---

### Post by dynamics on 2009-09-04
To **[COLOR="Red"]bucik85[/COLOR]**

Thanks a lot... I was struggling to get this done since last one month and now its solved. 
One of the reason for loving Ubuntu is it has a great forum with lot of helping friends :-)

:popcorn:

---

### Post by DaJL on 2009-09-17
I just got the same laptop  with the ati radeon HD 4570.   
Anyone else noticed Xorg  using a lot of ram?  1.6G on my system.  I'm using the xorg-driver-fglrx that comes with jaunty.  Is it better with the radeonhd driver?

---

### Post by katie24 on 2009-10-09
I have a Dell 1555 and it worked for me too.  Thanks!

---

### Post by mocillo on 2009-12-04
> **Logorrhoe said:**
> I have a suggestion!  open /boot/grub/menu.lst with an editor (you need root rights)  search the line "defoptions=" and add "acpi=force"right behind.  After a reboot everything worked for me, brightnesscontrol, ac-adapter events (when removed) on my Dell Studio 1555  Hopes it works for you,  Logorrhoe
defoptions=acpi=force

worked for me...

Thank you a lot :D

---

### Post by mocillo on 2009-12-04
> **mocillo said:**
> defoptions=acpi=force

worked for me...

Thank you a lot :D

Later it failed again, so i'm trying defoptions=noapic....

It's working for now... :P

---

### Post by chenxiaolong on 2009-12-22
AWESOME NEWS EVERYBODY!!! Kernel 2.6.32 supports the brightness control natively and any software based brightness control. You can download the new kernel at the Ubuntu Kernel PPA ([COLOR="SeaGreen"]http://kernel.ubuntu.com/~kernel-ppa/mainline/[/COLOR]).

---

