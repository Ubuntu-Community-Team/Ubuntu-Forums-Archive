---
title: "How do I install Nvidia 9600 GT in Xubuntu 12.04?"
date: 2014-08-25
forum: Hardware
---

### Post by Guyofdoom42 on 2014-08-25
A friend of mine got a new Graphics card, and gave me his old one. The problem is, I don't know how to install it. Anyone know how?

---

### Post by Guyofdoom42 on 2014-08-25
My friend gave me a Nvidia GeForce 9600 GT card, and I don't know how to install it. How do I do that?

---

### Post by oldfred on 2014-08-25
I have that card. I bought it back in 2009 when my 7600gtx card literately blew up. Capacitors popped.

With every live installer boot and first boot after install, I have to use nomodeset and get low graphics. 
Then I install the most current nVidia driver from the repository. Currently 331.38. 
Nvidia did announce that by next year the 340.xx series will become legacy for that card and many other older cards. Or the newest version you can install will be 340.xx. 

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
      
 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    After install:
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset. 

 NVIDIA is ceasing to support their older GeForce 8, 9, 200, and 300 series from their mainline driver but the NVIDIA 340.xx driver series will become a long-term legacy driver that they will commit to supporting until April of 2016. 
[http://nvidia.custhelp.com/app/answers/detail/a_id/3473](http://nvidia.custhelp.com/app/answers/detail/a_id/3473)
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by SeijiSensei on 2014-08-25
It depends on how old your machine is.  Look up its specs and make sure it has a "PCI Express" slot.  The machine's user manual might also have instructions on how to install a video card.

If you're currently using the graphics adapter on the motherboard, then the PCIX slot should probably be empty.  You just insert (carefully!) the card into the slot, close up the box, and connect the video cable to the new card.  Most of the time the computer will automatically discover the card and use it.  Otherwise you might need to change a setting the BIOS at boot.  Use whatever key combination your machine reports for the setup function when it first boots up.

Linux should discover the card as well and will use the open-source NVIDIA driver to talk to it.  You should, however, install the proprietary NVIDIA driver for this card, especially if you intend to watch videos on the machine.  Just run the command "sudo apt-get install nvidia-current" at the command prompt.  You'll need to reboot when it's finished.

---

### Post by overdrank on 2014-08-25
Hi and welcome, Please do not create multiple threads on the same issue. Threads merged.
Are you asking how to install the drivers or the installation of the card itself?

---

### Post by grahammechanical on 2014-08-25
I suggest that first you revert Ubuntu to using an open source video driver. Then physically install the card into the motherboard. Then load Ubuntu. When you get to the desktop activate a proprietary video driver if the open source video driver is not doing the job sufficiently.

---

### Post by Guyofdoom42 on 2014-08-29
> **SeijiSensei said:**
> It depends on how old your machine is.  Look up its specs and make sure it has a "PCI Express" slot.  The machine's user manual might also have instructions on how to install a video card.

If you're currently using the graphics adapter on the motherboard, then the PCIX slot should probably be empty.  You just insert (carefully!) the card into the slot, close up the box, and connect the video cable to the new card.  Most of the time the computer will automatically discover the card and use it.  Otherwise you might need to change a setting the BIOS at boot.  Use whatever key combination your machine reports for the setup function when it first boots up.

Linux should discover the card as well and will use the open-source NVIDIA driver to talk to it.  You should, however, install the proprietary NVIDIA driver for this card, especially if you intend to watch videos on the machine.  Just run the command "sudo apt-get install nvidia-current" at the command prompt.  You'll need to reboot when it's finished.

It's a custom built machine, but I didn't build it. Someone else did.

---

### Post by Guyofdoom42 on 2014-09-10
Nevermind, it was pretty easy.

For someone who dosen't know:

-Install the driver

-Open up the computer

-Take one of those metal tab thingies out

-Put the card in

-Boot up.

---

