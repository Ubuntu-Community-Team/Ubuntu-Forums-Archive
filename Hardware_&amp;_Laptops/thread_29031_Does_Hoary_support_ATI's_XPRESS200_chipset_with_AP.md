---
title: "Does Hoary support ATI's XPRESS200 chipset with APIC enabled???"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by psully73 on 2005-04-22
Just wondering if anyone knows if Hoary supports the new ATI chipset XPRESS 200 with the APIC option enabled? 

If I boot off of Hoary 5.04 cd the install complains of APIC or ACPI. If I disable APIC in the bios the setup will get to selecting the cdrom driver but I only have sata cdrom drive and it wont continue with the install no matter which option I give it for a cdrom driver.

---

### Post by buz on 2005-04-23
Interesting, you got the chipset I'm currently interested in the most (but still couldn't figure out if it works on Linux). If you get it to work, could you please tell me so?

As for your problem: I heard that Linux often doesn't like SATA if PATA emulation (some boards have that enabled in the BIOS by default). You could try messing with that stuff...

Also I think APIC and ACPI is quite a difference: ACPI  is for power saving whereas the APIC is a hack for IRQ troubles [http://en.wikipedia.org/wiki/Apic](http://en.wikipedia.org/wiki/Apic)

---

### Post by psully73 on 2005-04-23
hmmm... it's not looking good so far.... I can't get anything to boot on this MSI RS480M2-IL board with the ATI XPRESS 200 chipset. Well I can't say anything because I'm only uising SATA for all my drives. I thought ATI's chipset would have better support but I guess it's relatively new....oh well one of these day's I'll get it to work....Ubuntu and Kubuntu just plain ol' kick ass!

---

### Post by buz on 2005-04-23
For what I hear, the ATI SB400 on that board isn't supported on Linux so far :-(


Though look for you, and as for me, I need to go luck further for a decent fan less PCI express board...

---

### Post by griffith on 2005-05-16
I've got a MSI RS480 mobo running hoary. I had some problems installing due to some IRQ problems with the USB2.0 ports. but after installing with noapic set the install operation worked flawless. But when trying to startx it wouldn work. So I reconfigured xorg.config. shoosing vesa as video card instead of ATI. and then installed fglrx-driver.
After that everything worked. even 1600x1200 on my 19" CRT monitor.

---

### Post by nandhu on 2005-06-06
Hi,

There is an ATI Driver for XPRESS 200 Chipsets.

[http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=822344](http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=822344)

Give it a try. It might help.

If you are unable to download the driver, let me know, I can email it to you.

- Nanda.

---

### Post by tseliot on 2005-06-23
I have a MSI RX480 ATI XPRESS200P, with a serial ATA harddisk. I had to buy an additonal PATA harddisk in order to install Ubuntu. Then I had to Install 2.6.12 kernel (from Breezy repositories, but a recompiled kernel would be better). There are some problems with apic (expecially with other distros, for example I can't install Fedora Core 4).

My Ubuntu isn't flawless yet but I'll make things work (somehow...).

I would like to know how to turn apic off (not acpi!) so as to see if this could solve a problem I can't solve in Ubuntu 32bit (the double clock speed of my Athlon CPU on Gnome).

If you know how to disable it (by modifing modules?) please tell me.

Thanks

---

### Post by Jiilik on 2005-06-30
In xorg.conf, under the 'ati' driver section, enter in Option "NoAccel" "true" and the ati drivers will work - do this instead of using crappy vesa :P

---

### Post by zue on 2005-07-12
[QUOTE=tseliot]

I would like to know how to turn apic off (not acpi!)

Thanks[/QUOTE]


Me too!  I'm having all kinds of problems (also running xpress200 chipset) and I think at least most of them have to do with apic.  I keep reading in different places that it is possible to pass noapic as a kernel parameter, but nowhere does it say how.  Would someone a little more enlightened than me help me out?  Please?

Thanks,
Zue

Edit:  Ok, nevermind.  I found it.  You have to edit /boot/grub/menu.lst like so:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12.2.071005 Default 
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 no_timer_check[COLOR=Green] noapic[/COLOR] quiet splash
savedefault
boot
```

..except if you're running the 32bit version of ubuntu I don't think the no_timer_check option will work for you.  The noapic is supposed to turn apic off though.

---

