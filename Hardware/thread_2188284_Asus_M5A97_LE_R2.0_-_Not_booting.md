---
title: "Asus M5A97 LE R2.0 - Not booting"
date: 2013-11-16
forum: Hardware
---

### Post by Zendoin on 2013-11-16
Hello :)

I just built a new PC using the above mentioned mainboard. I succesfully (no errors) installed Ubuntu 13.10 first on a ssd. After BIOS, where usually grub appears, there comes just a blinking cursor. So I tried another installation (again no errors) on another hdd (not the one intended, just for testing) - same thing here. (On both discs I made a / and a /home partition manually, on the ssd also a swap partition.)

I already checked in gparted whether the "boot" flag has been set - it had NOT, whysoever. So I manually set it (on both / partitions) - changed nothing. Also tried manually reinstalling grub after normal installation which gave the same result again.

To me it seems I just missed something important in the BIOS... Of course I always took care of the boot order. There is an option to set the sata discs to AHCI or IDE (I don't know the exact difference to be honest...) - makes also no difference.

(Live system from USB stick is working.)

Any ideas anyone?

---

### Post by Zendoin on 2013-11-16
I can not find any more usefull BIOS settings to vary...
tried so far:
- secure boot: windows / other os (set to other os of course)
- csm: legacy / uefi / both ("works" only with legacy or both, otherwise error message instead of blank screen with cursor)
- sata mode: ahci / ide / raid (tried ahci and ide as already said)
- with ahci: esp on / off (no effect)

There seems to be nothing more concerning hard disks and booting behaviour...
Before buying that mainboard I was looking for potential trouble with Ubuntu on it and only found about its good compatibility.
??

---

### Post by Zendoin on 2013-11-16
I just reinstalled again (on SSD). Now after BIOS I get this message:
"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

Now I remember that I got this message the other time, too. I just can't remember what I did that changed it to just a blinking cursor...

---

### Post by heir4c on 2013-11-16
Maybe you installed the Grub on the USB and not on your HD/SSD. I have had that once.
So when you install Ubuntu you get the diskmanager to create the partitions. See at the screenshot below. (It's in Dutch but you see that there is a button where you can choose where to install the bootloader (grub) (you see the Dutch text: "Apparaat voor opstartlader-installatie")
Choose the disk where you install Ubuntu. Normally is that sda, but check that good. (So don't use sda1 or so, it's without a number):

[IMG]http://i.imgur.com/bQwOnVbl.png[/IMG]

---

### Post by Zendoin on 2013-11-17
Thanks, I did check that...

I now found out: when I use a GUID partition table I get the error message after bios, when I use DOS partition table I get this blank screen with cursor.

When I press shift after bios: no grub either (I read it could be that grub is just not to see because there is only one single operating system).

---

### Post by Zendoin on 2013-11-17
Ok, found the problem. Feel a little stupid now...

When installing with GPT (not using gparted) one needs to make this special EFI partition. Now I did that and I can finally boot into the new system :)

---

### Post by heir4c on 2013-11-17
Don't feel like that. 
I have no experience with GPT and EFI, that's all new for me. I don't use it even I have new a motherboard with UEFI but I use only Ubuntu and have no Windows on it, so...

---

