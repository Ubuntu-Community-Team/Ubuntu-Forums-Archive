---
title: "Can't get DMA on K7S746FX M/B. Tried everything!"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by clueless on 2005-04-28
I have been following all threads for a solution to the DMA problem in this forum but unfortunately none of the solutions here have worked for me (I haven't tried compiling a new kernel because I am not at all confident doing such thing, at least I want to make sure there's no easier way).

My motherboard is a QDI K7S746FX, with an Athlon XP 2500+ on it. Specifications from QDI's site say: Northbridge SiS 746FX, Southbridge 963/963L. I have an additional PCI SATA controller with a Maxtor hard drive on it. And then I have on the IDEs another Maxtor HD as primary master, a DVD-ROM primary slave and a CDRW as secondary master. Among the solutions that I have tried are changing the order of the modules to be loaded (infact I have set it as last) and adding amd74xx, via82cxxx, or both of them, above all modules and, finally, commenting out ide-generic (with that one the computer will not boot) at /etc/modules. I am thinking that maybe for my motherboard I should just add another module (something like SiSxx, just guessing here).

doing hdparm -tT on /dev/hda I get:
 Timing cached reads:   1096 MB in  2.01 seconds = 546.17 MB/sec
 Timing buffered disk reads:   14 MB in  3.27 seconds =   4.28 MB/sec
and on /dev/sda:
 Timing cached reads:   1116 MB in  2.00 seconds = 557.53 MB/sec
 Timing buffered disk reads:   78 MB in  3.03 seconds =  25.71 MB/sec

The results are very near, that makes me think that my SATA drive is working really slow too. And same applies for my CD drives.

I don't know what other information to include here so please tell me if I have to post other info.

All help would be greately appreciated!

---

### Post by heimo on 2005-04-28
Correct module to add (to best of my knowledge) is sis5513

```

filename:	   /lib/modules/2.6.10-5-386/kernel/drivers/ide/pci/sis5513.ko
author:		 Lionel Bouton, L C Chang, Andre Hedrick, Vojtech Pavlik
description:	PCI driver module for SIS IDE

```

---

### Post by clueless on 2005-04-28
Hello again and thanks for your reply
I tried adding the module you suggested in /etc/modules and commented out the other ones but after the reboot the computer just "stuck" during the boot sequence in "starting RAID devices". It didn't freeze, because the keyboard was responding but it just stuck there, not going further. I had to reboot with the ubuntu live CD to re-edit the /etc/modules file to have ubuntu start again. But I'm feeling that the solution must be something like this.

---

### Post by heimo on 2005-04-28
Sorry to hear that. I'm quite sure that is the correct module. Can you try to *modprobe sis5513 *to see if it gives any error messages?  In case it would hang, you should be running *tail -f /var/log/messages *in another terminal.

I tried searching for similar problem, but nothing helpful was found. Do you load that module before all the other ide-stuff? If not, you should try that.

---

### Post by clueless on 2005-04-29
Strange things are happening...
I added again the module you suggested in /etc/modules but this time I changed the sequence, putting it a bit lower in the sequence but before all other ide* modules. I rebooted and this time it just sat there for some time, like 3 minutes, in "Starting RAID devices" and then went on to "Setting up LVM Volume Groups" and stayed there for another 10 minutes. I got away from the computer for a few minutes and I just found a black screen (sneaky!) but I think I hear some hard disk activity every now and then so I'm just waiting to see what next. 
About the other thing you suggested, modprobing, I did it but it did nothing... I tried then switching DMA to on but with the same results.

---

### Post by heimo on 2005-04-29
Ah... I always forget to explain. If modprobe "does nothing" it actually just loaded the module successfully. So the module can be loaded. I bet that if you'd try the other modules (which you tried before), you'd get errors of some kind.

I have my chipset module at the beginning of modules:
 ```
**via82cxxx**
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

``` 

If something seems to take forever while booting, you may be able to skip with ctrl+c. It's possible that you need some parameters, but I've never had to use any for chipset modules - only for sound and network modules.

After booting, run *dmesg | less *to see bootlog. Search what's taking so long, any errors by the time module is loaded or hard disks / other IDE devices detected.

---

### Post by clueless on 2005-04-30
Hello again Heimo,

I don't know if I'm ever going to make it but I really appreciate your help (I'm learning, which is yet much)!

So, my /etc/modules file:
sis5513
sd_mod
psmouse
mousedev
ide-core
ide-cd
ide-disk
ide-generic
lp
nvidia

I tried doing modprobe via82cxxx to see what would happen and I got no error messagge either, but I think that it means that the module can be loaded even if it is not being used (my guess since I have very very little understanding of all this stuff!). Anyway, then I reboot...

I press control-C at "Starting RAID devices" (just to see if that would work, I have no RAID devices"

Than I press control-C at "Setting up LVM Volume Groups" and get a message
"hda: timeout waiting for DMA"

(It makes me think it might have something to do with me adding some lines to some configuration file of hdparm for turning DMA on at boot up, which didn't work at the time but just kept it unchanged since then and I was getting the message during boot "can't set DMA on, permission denied" or something like tha)t.

Then it sticks at "Starting Enterprise Volume Management System" and press Control-C and nothing happens for a long period of time (more than 30 minutes and having pressed Ctrl+C more times).

So, I just boot with the Ubuntu live CD to comment out the module I added, but I think at this point the output of dmesg|less will be the one of the last boot and will not include the boot that went wrong. 

And another thing: using the Ubuntu live CD I can switch DMA on and hdparm -tT /dev/hda gives me:
Timing buffer-cache reads: 1400 MB in 2.00 seconds = 699.06 MB/sec
Timing buffered disk reads: 168 MB in 3.02 seconds = 55.55 MB/sec

Any ideas?

---

### Post by heimo on 2005-04-30
You may want to go straight to point ***2***

Hmm.. ok. You've done good troubleshooting.

Oh, yes - you're correct. I don't know why I said you should get errors if loading wrong module. Yes, you can load modules even if they don't get used.

You could run lsmod after booting to Live CD. Check that you have sis5513 loaded and in use. Running lsmod | grep sis should give you something like:```

sis5513				15112  1
ide_core			 118988 6 sis5513,ide_generic,ide_disk,ide_cd,usb_storage

``` 

I'm quite much running out of ideas, haven't had so much trouble enabling DMA myself. (luckily) 

You could try rearrenging /etc/modules - some people on this forum had to do it to get DMA working. Try:

 ```

sis5513
ide-cd
ide-disk
ide-generic
mousedev
psmouse
lp
nvidia

``` 

I removed sd_mod. I don't have it in my modules file, but it gets loaded automaticly (and is in use). I'm not sure why "enable DMA only for disks" is on by default in Ubuntu's kernel. Maybe for compatibility reasons (for some very old machines which may have problems with that setting). It has cause - and still causes some headaches and probably some people are just unaware that they're not using full potential of their computers hardware - and only thing they notice is that "Ubuntu sucks, playing DVDs is not smooth" -kind of things. :(

BTW, what do you have in BIOS settings? Do you have DMA=auto or something like that? Hmm.. Just realized, it can't be that as the Live CD was ok.

*scratches head*

Maybe you should check /etc/hdparm.conf and undo changes you may have done earlier. If the module loads correctly, you should be able to enable DMA afterwards. I had trouble doing this earlier, but now it seems to work for me even as DMA is not enabled during boot.



***2*  **Now I got it. It's probably neccessary to make a new initrd. You may need to add that sis-module to /etc/mkinitrd/modules and run something like:
 ```

cp /boot/initrd.img-$(uname -r) /boot/initrd.img-$(uname -r)_bak
mkinitrd -o /boot/initrd.img-$(uname -r)
``` 
initrd is a ramdisk, something that kernel uses at very early stage of booting to enable support for devices that are needed for booting (for example if it can't yet access filesystem because module that is needed to access filesystem is on the filesystem...) It may be neccessary that you load the chipset specific module at that time. This is quite potential way to mess your system, so I'd suggest installing another kernel before proceeding (to get easy access around possible hangups).

If you have linux-image-2.6.10-5-386 kernel installed, install:
 ```
apt-get install linux-image-2.6.10-5-686
``` 

It probably does everyhing that's neccessary (adds itself to bootloader).

If I was unclear, go ahead and make questions.

---

### Post by clueless on 2005-05-01
I am very impressed from point 2! Quality! He, he, but unfortunately didn't work. Again same thing is happening. And by the way upgraded to Hoary and got the k7 kernel but with no solution. And then rebooted from live cd guess what... sudo lsmod |grep sis gives me:
sis_ agp           6144    1
agpgart          27596    1  sis_agp
sis900            16772    0
crc32                4352    2 sis900,stir4200

Does that mean that maybe it's that sis900 thingy? Or the sis_agp? I think I will try putting each one of them (trial and error, the least professional and more time consuming scientific process, but it has good results). Who knows if something like that works.

---

### Post by heimo on 2005-05-01
sis900 seems to be ethernet driver. You can always get information on module with modinfo. 

modinfo sis900
 ```
filename:	   /lib/modules/2.6.10-5-386/kernel/drivers/net/sis900.ko
author:		 Jim Huang <cmhuang@sis.com.tw>, Ollie Lho 
description:	SiS 900 PCI Fast Ethernet driver

``` 

Hmm... If you're not afraid of compiling kernel... (it's not too difficult), I'd suggest going through that route. You could take Ubuntus configuration and just disable the "enable DMA only for disks" setting.

I'm quite sure there is instructions on howto compile kernel in Ubuntu somewehere on Ubuntuforums. Howto compile kernel in Debian is probably quite close.
[http://www.falkotimme.com/howtos/debian_kernel2.6_compile/]("http://www.falkotimme.com/howtos/debian_kernel2.6_compile/")

Rough instructions (no details):

Kernel sources are available though Synaptic / apt-get. For example:
apt-get install linux-source-2.6.11

Then you'd need to uncompress the package in /usr/src, make symbolic link from /usr/src/linux to the directory that was created, copy old configuration file from /boot/ directory to /usr/src/linux/.config, run make oldconfig and configure DMA, compile and install new kernel (and modules). 

Not so difficult as it may sound at first. No programming skills needed, graphical / semigraphical configuration tool available (I prefer menuconfig).

What ever way you choose, good luck. :) And I'm still willing to help with any questions that may arise.

EDIT: About the initrd. If you're using grub (default bootloader), check  in /boot/grub/menu.lst that you have line with something like:
 ```
initrd		  /boot/initrd.img-2.6.10-5-386
``` 
in the section with your current kernel and that the initrd.img-file matches the file that was created with mkinitrd.

---

