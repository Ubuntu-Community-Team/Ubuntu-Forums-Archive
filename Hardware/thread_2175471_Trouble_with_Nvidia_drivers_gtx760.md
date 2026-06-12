---
title: "Trouble with Nvidia drivers gtx760"
date: 2013-09-19
forum: Hardware
---

### Post by quantumduck2 on 2013-09-19
Hi I am a little new to Linux.

I built a computer hoping to use it for play and physics simulations.(This is a desktop) I will list the hardware and Linux kernel version now. 
So I am using Ubuntu 12.04LTS kernel 3.8.0-30. The the hardware is as follows 

Mother Board -Gigabyte Z87MX-D3H chipset
Bios Version   - 04.06.05
Processor      - Intel i5-4670k quad @ 3.4 GHz
GPU              - EVGA GTX 760
HD               - Samsung 120GB SSD for my OS hard drive

Now I know this particular Intel processor is Haswell and it has integrated graphics which may be part of the problem. I followed the Ubuntu's site directions on installing the Nvidia drivers because the nouveau drivers didn't seem to pick up my Nvidia card. Everything worked fine while I was using the graphics form the Intel processor. Now that I have installed the drivers when I boot and tell the bios to look at PCIe-1 slot I see grub then I get black screen after hearing the Ubuntu drums sound. I have been all over the forums and tried many things and cannot get the nvidia card to work and I am very frustrated. Note I can however tell the bios to run graphics from the processor I still get a black screen but I can use tty. So I still have a way work on things. This a dual boot system with Window 8. I really want to be able to use the power of GPU to do simulations. Any help would be much appreciated!

---

### Post by oldfred on 2013-09-19
Did you install in BIOS with MBR partitioning or in UEFI with gpt partitioning? Probably does not make any real difference but how you may need to fix thing may.
Not sure if any of this applies to a desktop, most is info on dual video with laptops.

The very newest nVidia driver that works with Optimus needs the very newest kernel.
 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
      
 Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)
The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working
Some BIOS
turn off discrete graphics
turn off "os optimus detection"


 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

---

### Post by quantumduck2 on 2013-09-19
Ok thanks! I will get back to you once I have sifted through the info.

---

### Post by Yellow Pasque on 2013-09-19
@oldfred: this is not an Optimus setup :?
@qduck: you need nvidia 319.32 or later: [http://www.phoronix.com/scan.php?page=news_item&px=MTM5NTI](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NTI)

---

