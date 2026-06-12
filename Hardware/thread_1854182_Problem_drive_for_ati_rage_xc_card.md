---
title: "Problem: drive for ati rage xc card"
date: 2011-10-03
forum: Hardware
---

### Post by keymanu on 2011-10-03
I have installed 11.04 on a 950mz cup 384mb ram with a ati rage xc vid card.

my question  is this how can i make sure i am using the right driver?

my xorg.conf file say's 

Section "Device"
    Identifier    "Default screen"
          Driver        "nouveau"
EndSection

I'm not sure that's the right driver for ati.

any help is welcome I don't have money to upgrade an di have to do with what i have and just trying not to burn the card out.

Thanks
Keymanu

---

### Post by mastablasta on 2011-10-04
you should be using the default opensource driver that is loaded upon install.
 
lspci command will give you the exact chip of your card so we can see it (you can copy paste it here).
 
 
if you are having problems wiht graphics you could use unity 2D interface that should work better on these older mashcines.

---

### Post by keymanu on 2011-10-04
Thanks and yes i unintalled unity and went with gnome, besides unity refused ro run on this machine..lol
i did the lspci and here's what came up:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage XC AGP (rev 65)

it shoudl have 8Mb of rem on the board, as stated in my first post that was the installed driver, and it just doesnot look right, i did some more reading last night and jocky show's nothing when it come up.( if that helps) i may also need to know how to change it out

a lot of things have changed since red hat 5. silly learning
Thank You
Keymanu

---

### Post by Mark Phelps on 2011-10-04
Jockey is not going to show anything because your card is so old that it's been relegated to "legacy" status -- meaning there are no restricted drivers for it and Linux anymore.

The default installed open-source drivers are the only ones available now.

I've read that 11.10 has made improvements to the open-source ATI drivers, so you should try booting from a LiveCD of 11.10 to see if that makes any difference.

---

### Post by keymanu on 2011-10-05
Ok, i understand.

Thaksn for the help
Keymanu

---

