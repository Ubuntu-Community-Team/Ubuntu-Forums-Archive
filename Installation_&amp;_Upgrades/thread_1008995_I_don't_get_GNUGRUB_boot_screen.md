---
title: "I don't get GNU/GRUB boot screen"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by zombrax on 2008-12-12
ahh so finally installed dual boot with my existing XP. Now the setup is that

Ubuntu is installed totally on a NEW 100GB HDD.  I made sure that GRUB was installed and was pointed to the hd0 to start with.

Now when I boot; it goes straight into Windows logon screen as per before. How do i get the GRUB menu? How can i fix this from here?

Do I need to tweak my BIOS for the SATA disk on ch0 (which contains the installation of ubuntu)?

many thanks

---

### Post by howlep on 2008-12-12
is hd0 your boot disk? grub needs to be installed on the primary boot disk.

hope this helps

---

### Post by zombrax on 2008-12-12
damn oops prob no, I didnt do this! ahh how can I change the GRUB settings now to boot from C:\

---

### Post by caljohnsmith on 2008-12-12
> **zombrax said:**
> ~dang~ oops prob no, I didnt do this! ahh how can I change the GRUB settings now to boot from C:\
To boot from a different drive on start up, you would have to go into your BIOS and change the boot order; changing Grub won't determine which drive gets booted on start up. I would recommend installing Grub to the MBR (Master Boot Record) of your Ubuntu drive, and just changing your BIOS to boot the Ubuntu drive on start up; that way you can keep your drives independent of each other, so if something happens to Ubuntu or the Ubuntu drive, you should still be able to boot Windows. 

If that sounds like something you would want to do, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Reboot, set your BIOS to boot the Ubuntu drive, and then you should at least get a Grub menu on start up. Let me know if you make it that far or if you run into problems. :)

---

### Post by zombrax on 2008-12-17
ok, after playing around it for a while and changing the boot priority to the 3rd SATA drive, I finally get the GRUB screen.  But I when I choose the option to go into the Ubuntu, I got get the normal x-window screen rather than just the prompt. How do i get x-window as my usual logon?

secondly, the USB keyboard is not recognised with GRUB menu... whats the go with that?

helppp pleaseeee :(

---

### Post by zombrax on 2008-12-18
bump.. can anyone help me please? :)

---

