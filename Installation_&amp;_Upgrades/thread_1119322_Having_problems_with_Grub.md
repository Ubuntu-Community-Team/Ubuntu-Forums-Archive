---
title: "Having problems with Grub"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by poohter on 2009-04-07
I am currently dual booting windows,mandriva 2009 and recently added another hd and installed Jaunty...when I restart it starts in the mandriva grub and not the newly created grub for jaunty.

can anyone help me sort mygrub problem out?

---

### Post by Peasantoid on 2009-04-07
Try re-installing Grub to point to the Ubuntu installation. Instructions are [here](http://ubuntuforums.org/showthread.php?t=224351).

---

### Post by poohter on 2009-04-07
thank you for thatlink! one other problem, how do I know which hard drive number it is? I know its partition 0(used entire drive for jaunty)

---

### Post by Peasantoid on 2009-04-07
Install GParted (sudo apt-get install gparted, it'll be in System > Administration > Partition Editor) and take a look at your drives. Your internal one is usually /dev/sda (Grub calls it hd0).

---

### Post by jonny5tails on 2009-04-07
](*,)Just a stupid question...
Do you have your bios set to boot off the Jaunty drive?:lolflag:

---

### Post by poohter on 2009-04-08
> **jonny5tails said:**
> ](*,)Just a stupid question...
Do you have your bios set to boot off the Jaunty drive?:lolflag:

Not a stupid question at all, lol. I did change the boot order in bios but I believe I managed to screw things up by editing grub. In my case where I have 3 internal HD's with Mandriva on one and Windows XP and a third with freshly installed Jaunty, would it have been better to (noticed second time around after I had installed) use advanced options in Jaunty and not install a bootloader (since mandriva had already previously installed grub)?

I may just have a bad HD on my hands...wouldn't take a second reinstall. But if someone could answer the question about the bootloader to help me undertand how this works...Thanks for all the help.

---

