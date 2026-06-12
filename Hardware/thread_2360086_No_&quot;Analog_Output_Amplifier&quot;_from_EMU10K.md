---
title: "No &quot;Analog Output Amplifier&quot; from EMU10K1 Chip (SB Live! CT4760P)"
date: 2017-05-01
forum: Hardware
---

### Post by Djzn.BR on 2017-05-01
There is a regression in Ubuntu as far as this sound card is concerned.
In 16.04.2, everything works fine. The sound works properly from both Installed System and LiveCD.

Something have happened in 17.04, I can't get sound for the life of me in 17.04.
In other terms, the Analog Outputs have disappeared from 17.04.

Some screens to compare:

**Control Center**

[IMG]http://www.upl.co/uploads/controlcenter160421493669663.png[/IMG]

[IMG]http://www.upl.co/uploads/controlcenter17041493669671.png[/IMG]

lsmod | grep snd

[IMG]http://www.upl.co/uploads/lsmod160421493669663.png[/IMG]

[IMG]http://www.upl.co/uploads/lsmod17041493669671.png[/IMG]

aplay -l 

[IMG]http://www.upl.co/uploads/devices160421493669663.png[/IMG]

[IMG]http://www.upl.co/uploads/devices17041493669671.png[/IMG]


I have deleted ~/.config/pulse - does not work.
Have installed pauvcontrol, and it does not work.

Somebody help me figure this out!
Thank you.

**Update:**
I figured that the problem is actually with the Linux Kernel.
Both in Ubuntu 16.04.2 and Fedora 25, which used the 4.8 kernel series, the sound card was showing the Analog Output.
Now that Fedora 25 has got an upgrade to kernel 4.10 series, it happens the same as in Ubuntu 17.04, which comes with the 4.10 series.

**Solution**
The problem is related to AMD chipsets. In my case, I have a 990XA-UD3 board.
This hardware has a particular problem with the Kernel: You have to set IOMMU as ENABLED in the UEFI Bios, otherwise, you don't get Mouse or Keyboard functioning.
Turns out that reading this article below, helped me understand what cause could possibly be, since I was getting the same crazy AMD messages.
[https://answers.launchpad.net/ubuntu/+question/234598](https://answers.launchpad.net/ubuntu/+question/234598)

The solution for me was to KEEP the IOMMU Enabled in BIOS, but also adding to /etc/default/grub the appendix:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=pt"**

Kernel previous to 4.8 series would handle this without intervention. But the 4.10 series from now on may require you to use this option with this hardware.
In AMD crazy messages, the specific page fault was pointing to the Southbrigde "PCI to PCI Bridge". After adding that line to grub, it seems to have mapped it correctly.
I hope I helped others, helping myself.


[IMG]http://www.upl.co/uploads/Screenshot-from-20170503-1627451493839690.png[/IMG]

---

