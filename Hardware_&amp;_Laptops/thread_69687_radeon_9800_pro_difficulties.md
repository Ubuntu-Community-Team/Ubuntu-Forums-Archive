---
title: "radeon 9800 pro difficulties"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by sensoph on 2005-09-27
hello, i have been trying on and off fora  few months now to get the ati drivers working. from what i can tell i have them installed correctly thanks in part to many members of this forum and their suggestions to help other people. hopefully someone may be able to help me as well. basically after i install the driver, and then change my config (be it fglrxconfig, or dpkg-reconfigure or even just the switching of the ati -> fglrx) i still come up with the outcome, a complete lockup of x which is only fixed by rebooting again. its not a normal blank screen like i was used to in the past, now its usually garbled graphic output similar to what the back drop looks like when you boot up into ubuntu normally. 
i attached my xorg.conf file since the log file was too large i did a "grep fglrx Xorg.0.log  > xorglog.txt" to hopefully just show the fglrx info

by the way i have a radeon 9800 pro 256meg card

thanks
~jeremy

---

### Post by mlomker on 2005-09-27
>  which is only fixed by rebooting again.

If you are unable to Ctrl-Alt-F2 to another terminal then this is a hardware problem and not a video driver issue.  Pull everything off of your machine that you can unplug and still have the machine boot as a test...I've issues like this with TV cards or some other device that is trying to 'share' memory or IO space with the video card.

---

### Post by sensoph on 2005-09-28
i took my tv tuner out, as well as my soundcard which is basically all i can take out and still boot.  i have a ata controller card in still but i think it has my root drive on it. i can boot ok as long as i dont try to use the fglrx module. i tried tinkering with the bios settings for agp and other hardware but all it really did was either change the colors of the garbled graphics to white/black horizontle lines. i am wondering if its a possible conflict with the kernel or some default kernel setting and maybe i should try to install a custom kernel? 

the motherboard itself is an asus a7v8x-x with the via kt400 chipset i believe not that this will help by knowing this but i guess it might.

---

### Post by mlomker on 2005-09-28
Many people (myself included) run the drivers with the stock kernel.  If the machine is locking up hard then it's probably a hardware problem...memory, cpu, etc.

Have you tried an alternate kernel (search for linux-image in Synaptic)?

---

