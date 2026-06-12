---
title: "USB not working with Dell Optiplex 320 (ATI sb600)"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by btp on 2006-12-12
I just go a Dell Optiplex 320 with the ATI sb600 chipset, and I can't get Ubuntu to recognize the USB ports.  Unfortunately, this model has NO ps/2 ports, so I can't plug in any other kind of keyboard or mouse.

However, when its booting up (and I remove the "splash" and "quiet" boot options, and add "acpi=force irqpoll" (it doesn't see the hard drive otherwise)), I can look at the messages scrolling by, and I see:
```

USB HC takeover failed! (BIO/SMM bug)
can't setup
USB 2 deregistered
```


This occurs with either Edgy (6.10) or Dapper (6.06).  Once it gets past that, it boots into X, just like the normal liveCD should, but I can't use the keyboard or the mouse, so I can't do anything once it gets there.

.. are there any usb options I should try?

Also, both fedora and gentoo boot up correctly, and both the keyboard and the mouse work.  I'm in the process of downloading knoppix now to see if it works as well.

Note:I tried installing fc6, but that has problems of its own, and gentoo is my least favorite option, so I was going to try knoppix first.

Any ideas MUCH appreciated.

Thanks

--Ben

---

### Post by studerby on 2006-12-13
I've got the same problem. It looks the hardware, BIOS and the Ubuntu 6.06 and 6.10 kernels don't play nice together. I've got the latest BIOS from Dell, version 1.0.9. CentOS 4.3 also has a similar problem.

I've got a Knoppix 5.0.1 DVD from this spring that will boot as a live CD just fine. However, when I tried to install it to the drive (which is a beta feature of Knoppix) the result hangs immediately on boot (I formatted as ext3 and Knoppix prefers Reiser; I may try again).

I also tried installing from a Fedora Core 6 cd a coworker had laying around; it would boot into the installer OK, but couldn't recognize the hard drive. Seemed to only probe for SCSI disks; I don't know if that's the way FC is supposed to work.

So far, running a Knoppix LiveCD is the best I've been able to do. That seems to work fine, but has obvious problems. Ideally, I'd like to get Ubuntu installed, but for the moment, I'll settle for any distro that uses apt or rpm...

---

### Post by rlozano on 2006-12-13
this seems to be a common problem for those machines using ATI. i have not tried yet, but re-starting the HAL services maybe able to help.

just not sure how to re-start HAL services when you're in X already. :p

---

### Post by damdull on 2006-12-14
How did you boot on Edgy or Dapper with an Optiplex 320?
I have never managed to boot correctly with none of this distributions. It freezes at the beginning
Thanks
Damien

---

### Post by studerby on 2006-12-14
The alternative CD (not the live CD) will boot into the initial Ubuntu menu (which I don't think is a real kernel); however, when you choose install or media test or antything that boots into a real kernel, I get:

[17179624.508000] ohci_hcd 0000:00:13.0: USB HC takeover failed! (BIOS/SMM bug)
[17179624.508000] ohci_hcd 0000:00:13.0: can't setup
[17179624.508000] ohci_hcd 0000:00:13.0: init 0000:00:13.0 fail, -16

(repeats four more times, for 13.1, 13.2, 13.3, and 13.4)

The live CD just hangs for me.

---

### Post by btp on 2006-12-18
I was able to finally get the machine up, but I had to install lilo, and then after that, recompile the kernel with sata support built-in.

I'm not sure why grub wasn't working, but it would start the grub, but once it started reading the blocklist, it would just quit. Someone at my work guessed a BIOS bug in the Dell BIOS, but we don't know for sure.

In either case, it looks like it works, it's just a PITA.

Also, I had to use Fedora Core 6, neither Dapper nor Edgy worked.

---

### Post by studerby on 2006-12-18
Over on the Dell Linux-Desktops mailing list ( [http://lists.us.dell.com/pipermail/linux-desktops/](http://lists.us.dell.com/pipermail/linux-desktops/) ), they say that you can also get Fedora working the same way, by switching the boot loader to lilo and recompiling the kernel. OpenSUSE seems to have the same problem, so it looks like a general GRUB problem, or a BIOS problem that shows up in GRUB but not lilo. 

Unfortunately, recompiling the kernel's a little bit over my head so far (this week at least), but I found that Mandriva Free 2007 will work, but you have to add "pci=nomsi" to the installer's boot parameters to get through the installation.

---

### Post by Vide on 2007-01-02
btp: how have you managed to install Ubuntu on you Optiplex 320?
What did you do? I'm stuck on it (desktop install hanging on boot "mountig root devices")

---

### Post by coakley on 2007-01-11
Yes yes Dell Optiplex 320.

I keep trying but I can't boot to live CD or start an install

USB HC takeover failed! (BIOS/SMM bug)
can't reset
init 0000:00:13.0 fial, -16

I have tried Ubuntu 6.06, Kubuntu 6.06, the Alternate disc, Xandros, Suse 10.1 etc.

I have tried noapic, nolapic, acpi= force irqpoll, pci=nomsi etc.

Help.

---

### Post by Slade Winstone on 2007-02-12
Hi, I'm running Edgy, 2.6.17-11-generic, and found a strange, kinda, partial work-around, for this problem:
[http://ubuntuforums.org/showthread.php?p=2143128]("http://ubuntuforums.org/showthread.php?p=2143128")

---

