---
title: "LiveCD 9.0.4 fails with &quot;corrupted_low_memory&quot;"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by alfabravoteam on 2009-07-16
Hello everybody, 

i've been searching all over the forums and couldn't find a workaround for my current problem. I've a PC at home with the following config:

Board Intel d946gzis
core2duo 6300 @ 1.8GHz
2GB ram ddr2
HD Maxtor SATA 200GB

I had a Debian testing/Windows XP 'grubbed' boot and it was working pretty fine with the 2.6.29-2 kernel. I wanted to improve from my old CRT monitor, so I bought a Samsung LCD monitor and this Asus EAH4670 graphic card. From the moment I installed the card, Debian refuses to work and i'm trying to run the Ubuntu 9.0.4 live CD, either amd64 o i386.

It dies on me whether i choose the noapic, nolapic, acpi=off options, or if I add the noirqpoll parameter. The error message (which I can't get completely) says:

[FONT=Courier New]init: rc-default main process(xxxx) exits with code 127.[/FONT]

Then, a bunch of messages shows up, similar to this

[FONT=Courier New]/var/log/[/FONT][FONT=Courier New]kern.log.[/FONT][FONT=Courier New]0:Jul 16 05:10:35: [time value] Corrupted low memory at ffff88000000cf78 (cf78 phys) = 00420000[/FONT]

and it ends with "*corrupted low memory*". It doesn't matter if I try to run LiveCD or install Ubuntu, it dies anyway.

How come my BIOS is useless now? Could it be something else related to the HW change? Thanks in advance for your help.

---

### Post by dstew on 2009-07-16
> How come my BIOS is useless now?I don't think you have any problem with your BIOS. It seems that the Ubuntu Live CD, and your installed system, cannot work with your graphics card as presently configured. That is, the Linux kernel and its collection of drivers cannot function in the system with the card present. I assume Windows works fine, which would exclude any serious hardware problem with the card, or that it is not seated properly etc.

Assuming the Live CD is good (it works in other systems, and in your system before you installed the Asus card, right?), you could try to get the proper driver for the card by trying a Recovery Mode boot, then **xfix** to see if you can get a simple display. Then, see if there is a driver available in Hardware Drivers.

If you can't get it to boot at all with the card in there, you are probably out of luck. You can try kernel parameters as you are doing. You could also try to re-install Ubuntu using the Alternate Install CD. Do you know of anyone who has been able to get that card to work with Ubuntu?

---

### Post by alfabravoteam on 2009-07-16
> **dstew said:**
> I don't think you have any problem with your BIOS. It seems that the Ubuntu Live CD, and your installed system, cannot work with your graphics card as presently configured. That is, the Linux kernel and its collection of drivers cannot function in the system with the card present. I assume Windows works fine, which would exclude any serious hardware problem with the card, or that it is not seated properly etc.

Assuming the Live CD is good (it works in other systems, and in your system before you installed the Asus card, right?), you could try to get the proper driver for the card by trying a Recovery Mode boot, then **xfix** to see if you can get a simple display. Then, see if there is a driver available in Hardware Drivers.

If you can't get it to boot at all with the card in there, you are probably out of luck. You can try kernel parameters as you are doing. You could also try to re-install Ubuntu using the Alternate Install CD. Do you know of anyone who has been able to get that card to work with Ubuntu?
1. yes, the Ubuntu CDs do work properly. I've tried them on my laptop and they boot flawlessly.

2. Yes, Windoze is working fine.

3. Yes, I do feel out of luck :(  Thanks for your answer :)

---

### Post by ktechman on 2009-12-18
I had the same issue I pulled the PCI video card (GeForce FX5200) in a Dell 2350 and the install went ahead flawlessly. Thank you Dstew for your reply.

Ktechman

---

