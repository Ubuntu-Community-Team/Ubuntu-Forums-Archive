---
title: "Ubuntu does not recognize my Nvidia GeForce GT730"
date: 2017-02-10
forum: Hardware
---

### Post by mirclay on 2017-02-10
Hi, 
I recently built a brand new desktop computer with Intel I7 and installed ubuntu 14.04.

Ubuntu doesn't recognize my Nvidia Geforce GT730 at all. 

lspci, dmesg recognize the in-built Intel GPU, but not Nvidia gpu. Secure Boot & Windows Fast Boot is disabled in my BIOS.

I tried many many different things on the forums, but none of them seem to work. 

Can anyone help?

Thanks in advance.

---

### Post by Bashing-om on 2017-02-10
mirclay; Hello;

Did you enable the PCI slot in bios ?
I run an old box and legacy bios, and I do have to set in bios which slot to use . ( PCI Express).

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by oldfred on 2017-02-11
UEFI or BIOS install?
What brand motherboard.

Are you using nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

One or two users installed using Intel video out port, then manually installed nVidia driver from Ubuntu repository or the ppa and then enabled nVidia card.

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648)

Do not install nVidia driver from nVidia directly. Only use Ubuntu repository which should have a new enough driver for your card.

If you want very newest driver use ppa.

 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 


 If already installed nVidia driver and want to change, you must totally purge all traces of old driver or else you get conflicts.

---

### Post by mörgæs on 2017-02-11
A low-tech solution is to try a fresh install of 16.10 in stead of the stale 14.04. Mixing new hardware and old software means asking for problems.

---

### Post by mirclay on 2017-02-14
Thanks for the response oldfred. I have a gigabyte motherboard and I did a BIOS install. 

about "One or two users installed using Intel video out port, then manually  installed nVidia driver from Ubuntu repository or the ppa and then  enabled nVidia card": 

Do you mean to say remove the GPU, install the Nvidia drivers and then put it back on the motherboard?

I tried the nomodeset option, it still did not recognize the GPU.

---

### Post by oldfred on 2017-02-14
I have a bit older nVidia 620GT on my Illinois Haswell system, and had to always use nomodeset. But I think with 16.04 it worked without nomodeset and I cannot tell any real difference between the open source driver & the correct nVidia driver. But I do not play games or do anything that needs high powered video.
My Florida build just uses Intel video from Skylake i5 and that just works.

You do not have to Physically remove card. May have to change setting in UEFI to un-enable card or in effect turn on internal video and then plug video cable into motherboard video out connector.

I am a retired snowbird or one who heads south for the Winter. :)

---

