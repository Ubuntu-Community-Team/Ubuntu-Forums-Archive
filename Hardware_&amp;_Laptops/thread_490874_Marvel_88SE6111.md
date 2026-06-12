---
title: "Marvel 88SE6111"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by uputer on 2007-07-03
Some motherboards have PATA/SATA RAID controllers with the Marvel 88SE6111.   Does this pose a problem in Linux?   I haven't found much info on it other than some Gentoo users posting in the related forum about it and having problems.   If I'm building a system and shopping for a mother board, should I just stick to a board with the Micron (RAID) controller or will the Marvel ones work eventually?

Anyone know?  Any recommendations or advice?   I'm looking mostly at P35 chipset boards.

---

### Post by timk on 2007-07-24
Hi Uputer,
I see no reaction in this thread. Did you make any progress on the 88se6111, I am considering an MSI Motherboard with this chip and I am wondering too if I should buy it or not.

Timk

---

### Post by scramatte on 2007-07-25
Hello,

I've got an MSI P35 Platinum with 88SE6111 chipset.
I've rebuilded a 2.6.20 with a patch from  
[URL="http://marc.info/?w=2&r=1&s=88se6121&q=t"]
http://marc.info/?w=2&r=1&s=88se6121&q=t[/URL]

but unfortunately doesn't works yet ...

Regards

---

### Post by rezafab on 2007-07-25
I have the MSI G33M-FI with the same Marvell 88SE6111 and it is not recognized by Feisty or Gutsy so far. I've only been able to try with the CD because lack of IDE support prevents me from installing into my hard drive.

Does anyone know if there is a solution to this problem or if somebody is working on it?

I would offer my computer for testing if they need it and try to relay as much info on errors and such.

Thanks

---

### Post by BobCFC on 2007-07-28
I have an MSI P35 Platinum working perfectly with IDE/PATA drives in Feisty Fawn 64bit _after some work_.

To get it to boot up you need to add a magic kernel option:  :idea:
```

**generic.all_generic_ide=1**
```


If you are installing from a livecd press F6 to edit the boot options.. you may also want to change splash to **nosplash** because it takes longer.  This will remove the logo so that you can see what is happening.

Once the system is installed and you reboot you will have to pass the **generic.all_generic_ide=1** option through the grub menu.  To do this press **e** to edit then go down to kernel and press **e** again.  When done press ESC to go back and then **b** to boot with this option.

To make this persistent you can edit the grub config file as root such as **gksudo gedit /boot/grub/menu.lst**


Now you will have a working system but it is very slow to copy files and uses 100% CPU because DMA is not enabled.  The trouble is you cannot just enable DMA using **hdparm** because PATA drives are treated as /dev/sda not /dev/hda anymore.

There has been a lot of work on the new PATA drives in the kernel recently by Alan Cox et al so I decided to download the new 2.6.22.1 kernel from kernel.org and compile one myself manually using the guide on the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")

It seems scary but it's really not hard, just copy and paste the commands then tick boxes for your options.  (make sure you have a few gig free space for temporary files)

Here are the effects of using the latest kernel on IDE/PATA HD speed measure using the command  **sudo hdparm -iTt /dev/sda**


> Speed before using normal 2.6.20.16-generic Ubuntu kernel:

Timing buffered disk reads:    6 MB in  3.75 seconds =   **1.60 MB**/sec

1.6MB/s!!! You can download faster than that OMFG  ](*,)

> 
Speed after using latest 2.6.22.1 kernel:

Timing buffered disk reads:  214 MB in  3.02 seconds =  **70.82 MB**/sec


WOOT!  It's like going from dial-up to adsl.  Also the CPU use is normal too :)


I choose to enable a few kernel options when compiling such as Marvell and generic ATA.. I don't know if it was these or just the new kernel by itself.

NOTE: you still need to pass **generic.all_generic_ide=1** to the kernel from the grub menu to get it to boot! Also if you are using proprietary nVidia drivers from the nVidia web site you will have to reinstall them so have them to hand.
[COLOR="Red"]
PS:  if you are terrified of compiling your own kernel or something breaks you can try the new Gutsy Gibbon Tribe 3 iso.... it contains the new kernel prebuilt and works fine on P35 as long as you pass the magic boot option through the grub menu. Although please remember Gutsy is still in alpha and not released until October 2007[/COLOR]

Pheeeew. After all that everything is perfect I have compiz fusion working and dual monitors and life is sweet in linux.  Hope this helps feel free to ask questions.

---

### Post by uputer on 2007-07-29
> **timk said:**
> Hi Uputer,
I see no reaction in this thread. Did you make any progress on the 88se6111, I am considering an MSI Motherboard with this chip and I am wondering too if I should buy it or not.

Timk
Hi, Tim.   I'm considering a Gigabyte DS3R board now.   But, I hope this thread will help people who use Ubuntu (or any Linux Debian distros) with MSI motherboards with the Marvel chip.

---

### Post by BobCFC on 2007-07-31
> **uputer said:**
> Hi, Tim.   I'm considering a Gigabyte DS3R board now.   But, I hope this thread will help people who use Ubuntu (or any Linux Debian distros) with MSI motherboards with the Marvel chip.



I think you will find similar issues using IDE/PATA drives with any Core2Duo motherboard.  It is Intel's fault not MSI's.  Intel has dropped support for IDE drives completely from the chipsets on Core2duo motherboards and it is up to motherboard manufacturers to bolt-on support.

Just google for problems with the JMicron controller used on most other motherboards.


Hell when I use XP or windows 2003 I can't have DVD and HD both on IDE without loosing UDMA and going back to slow PIO.

Be thankful for the latest linux kernel and Alan Cox!  With **generic.all_generic_ide=1** on gutsy gibbon it works perfectly.

---

### Post by tricky99 on 2007-08-07
Thanks to BobCFC for this info... :KS

It seems to work fine for Ubuntu on my MSI P35 Platinum. Fortunately I have SATA HDD's (on the Intel ICH9R) so the Marvel 88SE6111 is only required for the DVD Writer at present.


Unfortunately for me I also need a Fedora Core7 install and the install CD seems to ignore "generic.all_generic_ide=1".

Since I'm not really a Linux expert whats the best way for me to go ? (apologies if it's inappropriate to ask about another distro here)
[LIST]
[*]Build a custom boot disk with newer kernel hoping that it supports the generic ide option (never done that, sounds like plenty of research)
[*]Just go buy a SATA DVD-Writer (been considering it anyway)
[/LIST]

Rgds
Tricky.

---

### Post by BobCFC on 2007-08-07
I ran a few tests for you with the ISOs that I had lying around.  Fedora 6 32bit, Fedora 7 64bit, PCLinuxOS 2007 32bit, Mepis 6.5.02 64bit.

Mepis wouldn't boot.  Although I could swear it booted a few months ago.  The good thing about Mepis is it has a boot menu option **all-generic-ide** which is meant for people with similar JMicron problems on the P965 Core2Duo motherboards.  This got me on the track of searching for ide boot options in the first place. So bonus points to Mepis for effort.

I could get FC6 to boot but not F7 :(   (Maybe you could install 6 and do upgrade?)  No such help from the menus.  It was a while since I downloaded the ISOs but it seems FC6 was just an installer but F7 was a live CD.  Maybe thats why 7 didn't boot.  Anyway if you press F4 to edit the boot options on the Fedora Core 6 i386 DVD and type **linux all-generic-ide** it will boot and start the install process asking for language and keyboard etc.  I went as far as it recognising my HD and asking for partitions when I exited.  Not going to install Fedora on my machine lol.

PCLinuxOS 2007 booted from the live cd !  using the boot option from mepis **all-generic-ide** I played with the livecd for a bit and was quite impressed It was using DMA right out of the box my HD tested at 71.14mb/s  using sudo hdparm -iTt   although I noticed it was using a much older kernel 2.6.18.8

It is a shame it is KDE based, but they have taken the cool spinning hourglass from fedora which I always wanted!

BTW Debian 4.0 boots the same way as Ubuntu with the **generic.all_generic_ide=1** option.  It is even tucked away in the menus and is how I actually tracked down this magic kernel option.  Yay Debian! We still love you even if you hate Ubuntu.

Well SATA DVD burners are dirt cheap these days but it seems ludicrous when it works perfectly in some distributions.

Incidentally while I was swapping a hard drive with the DVD the on board gigabit stopped lighting up... I found that unplugging the power and switching off for 30s while the motherboard led went out fixed it. It maybe just the bios I am using (1.1)

UPDATE: to get onboard sound ALC888 HD audio working in PCLinuxOS 2007 use:  apt-get install dkms-alsa-driver

---

### Post by BobCFC on 2007-08-07
BTW I found an tutorial that tells you how to download the latest kernel on Feisty Fawn without having to compile it.  Basically you temporarily set the sources list to Gutsy Gibbon.  Upgrade the kernel package.  Then set the sources list back to Feisty Fawn. 

[http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html](http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html)


This means Feisty users can use DMA without compiling their own kernel just by using the boot option **generic.all_generic_ide=1**

---

### Post by bruno321 on 2007-11-06
Hi, I will be updating to a system which will have a mother that has this Marvell IDE controller thing.

I will be installing Kubuntu Gutsy, so no problem with the kernel. But I'll install it to a SATA drive: the PATA drives I have will not be the ones I'll install the system into. So, should I still pass that generic-ide option when I install the system? More exactly, what would I have to do? GRUB wouldn't be an issue here since I would not be booting from those drives, wouldn't it?

Thanks.

PS: The PATA drives are one HDD and a DVD-RW. Would I be able to records DVDs without problem?

PPS: I'm seeing this motherboard also uses this Marvell thing for its SATA devices... Would it also be troublesome?

---

### Post by BobCFC on 2007-11-08
You will have to experiment on your own system, but for me it also affected the IDE DVD drive as well as the hard disks.

This meant that part way through booting the liveCD it couldn't find itself!  It would start booting fine then say please insert boot media or similar, cannot find CD drive in your system.  Crazy.

So, try it normally first.. if you have a similar problem read on...


> should I still pass that generic-ide option when I install the system? More exactly, what would I have to do?

When you boot the liveCD you hopefully get to a menu which says 'Start or install Ubuntu, Memtest86, Check CD for defects'  etc.  Along the bottom you see it says press F1-F6 for other things.

While the menu is over the first item Start or Install Ubuntu press the F6 button to edit the boot options...  This will reveal a long line of text  which ends similar to   '........ quiet splash --'    This is the line you need to edit to pass options to linux.   Delete the word splash.. that will hide the boot logo and let you read any error messages... Then add this to the end of the line:

```
generic.all_generic_ide=1
```

Then press enter to try and boot the LiveCD again.   It will say 'Ignoring unknown boot option generic.all_genric_ide=1'    but despite this, for me it would not boot without it.



> GRUB wouldn't be an issue here since I would not be booting from those drives, wouldn't it?

It is not a GRUB problem, but as grub starts first and boots linux we can pass options to the linux kernel to make it boot differently.  This is basically the same thing as above for the live CD but instead of pressing F6 to edit the boot options you press the letter E.  

Here's a quote from my previous post about that 

> Once the system is installed and you reboot you will have to pass the generic.all_generic_ide=1 option through the grub menu. To do this press e to edit then go down to kernel and press e again. When done press ESC to go back and then b to boot with this option.

To make this persistent you can edit the grub config file as root such as gksudo gedit /boot/grub/menu.lst


If you edit the menu.lst file as root you will find the kernel line which is the same as if you had pressed e at the grub menu.  The only difference is that pressing e is not permenant... it only affects that boot, so instead of having to type it every time you can edit the file once and it will remember.

Here is an example of the relevant section from my /boot/grub/menu.lst file.  Note yours will have different values for (hdx,x) partition as well as a different UUID.  just an example


```
title		Ubuntu 7.10
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8d48e6c9-4a76-4ce2-88f6-15e1be4ce97e ro quiet nosplash generic.all_generic_ide=1
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8d48e6c9-4a76-4ce2-88f6-15e1be4ce97e ro single generic.all_generic_ide=1
initrd		/boot/initrd.img-2.6.22-14-generic

```


You can see I just change splash to nosplash (same as deleting it) and added the magic option to the end of the line.  Also add it to the end of the kernel line for recovery mode otherwise you cannot access the drives when fixing your system!


Good luck I hope this helps. It's ok to message me if I am away and miss replies.  (edit: I've just figured out that I can subscribe to threads!)
Bob

---

