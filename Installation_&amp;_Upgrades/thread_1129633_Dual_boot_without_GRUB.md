---
title: "Dual boot without GRUB?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by chrini on 2009-04-18
Hello,

I have a fairly complex question about some possible dual boot Windows/Ubuntu options.

_Background:_ I'm currently running Windows XP, but I also would like to run Ubuntu on the same HDD (it's on a laptop). I've recently (successfully) installed Ubuntu on a USB flash drive, however, it was very slow and surfing the internet was literally 1000 times slower than it would be from an internal HDD (as would be expected).

_Overview:_ Also, I really don't want a GRUB loader because 90% of the time I am using XP rather than Ubuntu, so I'd prefer to have my computer boot directly into Windows every time. So my question is: is there any (simple) way to install the GRUB boot loader onto a USB flash drive so whenever I want to use Ubuntu I can simply plug in the USB stick and select "boot from USB"? And will my computer "like" having Ubuntu installed without the GRUB loader installed on the internal HDD? Basically, without GRUB will my computer see Windows as the "main" OS and boot into it rather than Ubuntu?

_Status:_ I have read several web articles on how to install the GRUB loader onto a USB stick, but most of them are quite hard to follow, require the use of Linux to install it (which I don't have yet), or are targeted to people who want to install Linux on a USB stick (which I've done as mentioned above). I was thinking that there might be an option during the Ubuntu install to point the GRUB loader at the USB rather than the internal HDD (is this possible?). Unfortunately, I do not have a "testing machine" to try to run through all my ideas, that is why I chose to ask the experts :D!

Well, I better leave it at that for now. There are quite a few questions in here to be answered and I don't want to make it too overwhelming. Any help is appreciated. Thanks!

---

### Post by lisati on 2009-04-18
You might want to consider using Wubi to install Ubuntu "within" Windows, which uses the Windows bootloader instaed of Grub

---

### Post by meierfra. on 2009-04-18
>  I'd prefer to have my computer boot directly into Windows every time. 
I suggest to use Grub, but configure Grub so that you  automatically  boot into Windows. This will accomplish your goal and is much easier to set up than using the windows boot loader.

---

### Post by Shazaam on 2009-04-18
Also, you might consider running Ubuntu as a virtual machine (on top of Windows). There are a few drawbacks such as slightly slower performance (in the vm depending on your memory amount) and 3d gaming is iffy at best.

---

### Post by theozzlives on 2009-04-18
You could use the USB creator from the live CD.

---

### Post by sailthesea on 2009-04-18
> **lisati said:**
> You might want to consider using Wubi to install Ubuntu "within" Windows, which uses the Windows bootloader instaed of Grub

 I'd agree
 But once you have a feel for Ubuntu go for a proper dual boot it seems to work better in its own space Plus you just won't feel the need to use Windows as much;)

---

### Post by TimDaniels on 2009-04-18
> **chrini said:**
> 
I have a fairly complex question about some possible dual boot Windows/Ubuntu options.

If you would go with Grub as the boot loader/manager, you can still make WinXP the default OS.  Grub would replace your MBR, though, so if you removed Ubuntu, Grub would still be your boot loader/manager.  If that is OK, here is a tutorial on how to do it:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Otherwise, if you want Winxp's boot loader/manager (ntldr) to control booting, and if you like struggling, use this guide,
substituting "Grub" for "Lilo":
[http://www.vsubhash.com/writeups/multiboot_os.asp](http://www.vsubhash.com/writeups/multiboot_os.asp)

*TimDaniels*

---

### Post by chrini on 2009-04-19
Thanks for all the replies! Oddly enough, I subscribed for instant email notification, but I only received one email. Usually I get an email every time a response is made... but that is beside the point.

Everyone's ideas are all very good, however, they did not really answer my question about the possibility of installing GRUB on a USB stick and removing it from the internal HDD (with FreeDOS boot cd and fdisk /mbr). 

> Also, you might consider running Ubuntu as a virtual machine (on top of Windows).

I do actually have a VM set up with Ubuntu and it is great for simple tasks such as using Octave or programming, but as you say the performance is quite slow with anything that uses a lot of memory (even with 2 GB dedicated it was quite slow). I also don't like the internet connection because it is "bridged" so it just uses the host internet... it would be much better if it actually used the wireless card itself (if you know how to do this, please let me know!).

> I suggest to use Grub, but configure Grub so that you automatically boot into Windows

After I had posted this message, I did read a great tutorial on how to edit GRUB and set Windows as the default OS. Go _[here]("http://users.bigpond.net.au/hermanzone/p15.htm") _to check it out, it is very handy and detailed! And if I find no solution to my answer, then I'll likely go this route.

> You might want to consider using Wubi...

From what I have read about Wubi, it sounds like a similar choice to just using dual boot and GRUB. The difference being that you use a windows installer rather than booting from an install disk (?) and the fact that it uses Windows boot loader, which from what I have read is not as good as GRUB.

> You could use the USB creator from the live CD

This is essentially the same thing as installing Ubuntu on a USB stick (except it might be a bit lighter and it seems a little more complicated if you want to have specific programs installed?). And as I mentioned, the performance was horrible because, I am assuming, the read/write is drastically slower when it is reading from the USB port rather than the internal HDD.


At any rate, thanks for all the solutions! I will, however, refine my question because after reading my original post I think I may not be quite as clear as I thought I was. 

**_Question:_ I'd prefer to have *NO* boot loader at all, but instead I'd like to have my machine boot into Windows every time. However, this would eliminate any way to get into Ubuntu, so I was wondering if it is possible to put GRUB on a USB stick so I can simply 'boot from USB' and, thus, still be able to boot into Ubuntu?**

Does this make sense? As I mentioned before, I wish I had a test machine because I have all kinds of ideas that I'd like to try. But I'd like to get some opinions before I try any "testing" on my only machine :D.

---

### Post by meierfra. on 2009-04-19
> so I was wondering if it is possible to put GRUB on a USB stick so I can simply 'boot from USB' and, thus, still be able to boot into Ubuntu?

Sure. Make sure the USB stick is plugged in while you are installing Ubuntu. At the last step of the installation, click on the "advanced" button.  This will let you  choose the location for Grub. Choose the MBR of your USB drive. (something like /dev/sdb or /dev/sdc. You can use "sudo fdisk -lu" in a terminal of the LiveCD to determine the correct location)

---

### Post by nealaustin on 2009-04-19
I would suggest using grub. Now once everything is installed in Ubuntu go to applications add/remove programs. Add KgrubEditor. It is a sweet prgram that will let you edit your grub file. What I liked the most is that you can get rid of all of those old versions and set the default to about 2 seconds. It also lets you set your windows to be the default although I wouldn't know why.

Neal

---

### Post by chrini on 2009-04-19
Awesome, thanks for the reply. I was wondering if I could change the timer to about 1 or 2 seconds... I'll give that a try.

---

