---
title: "Wee Bit o' trouble"
date: 2009-07-10
forum: Hardware
---

### Post by Diofan on 2009-07-10
I have a toshiba Satellite 1105 Laptop comes with the OEM Windows XP Home edition.
I want to have this machine run solely on linux. but Ubuntu won't install on it. I think it may be due to the Laptop's extensive use of Onboard PCI Devices as it hangs trying to find the display adapter. 

Here's the hardware on the laptop:
*Realtek RTL8139/810X Family PCI Fast Ethernet NIC
*O2Micro OZ6933 CardBus Controller
*Intel(R) 82801BAM/CAM PCI Bridge - 2448
*Intel(R) 82801CA/CAM USB Universal Host PCI PCI Sound: Avance *AC97 Audio
*TOSHIBA Software Modem AMR
*Intel(r) 82801CAM Ultra ATA Storage Controller-248A
*Intel(R) 82801CAM LPC Interface Controller - 248C
*Intel(R) 82830 Processor to I/O Controller - 3575 
*Intel(R) 82830M Graphics Controller-1

The Toshiba Software Modem I could care less about as I never use it.
Is there any way I can put Ubuntu or another Distro of Linux on this machine or am I stuck with Windoze on it?

---

### Post by celticbhoy on 2009-07-10
Have you tried the alternate install CD, or just the live CD install?

---

### Post by Diofan on 2009-08-02
> **celticbhoy said:**
> Have you tried the alternate install CD, or just the live CD install?
I've tried the Standard Install like I did on my Desktop PC (Which I'm using to post this), and the live CD install. When going into Live CD Mode it asks for a username and password. (Which I have no clue what it is)

I have no idea how to do the alternate install. 

When I try the Standard Install I get the Following Message:

> SQUASHFS Error: unable to read Fragmant cache Block 
SQUASHFS error: sb_bread failed reading block 0x8272Does this all the way through the total amount of Ram Addresses before it stops with:

Tried to get to the DMA settings in Bios, no luck there.

---

### Post by Diofan on 2009-08-09
I've tried Ubuntu, xubuntu, Open Suse, Mandriva & Fedora for this laptop. No luck. Then tried Puppy, it works. So now I got puppy in the laptop and Ubuntu on the desktop. Now I gotta figure out how to get Puppy to work like ubuntu in the customization department.

---

### Post by Diofan on 2009-08-14
Didn't care for Puppy. Not as easily customizable as Ubuntu.

Tried the Alternate Install. Worked great! Thanks for the heads up celticbhoy, you rock!!!

---

### Post by lisati on 2009-08-14
The first time I installed Ubuntu on a Toshiba laptop I used an "alternate" CD that I downloaded. You can get one here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

By the way, the "standard" installation CD is also known as a "Live CD"


edit: great to read that it worked!

---

