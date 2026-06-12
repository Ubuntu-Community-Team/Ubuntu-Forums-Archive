---
title: "1002:4378 modem problems on hp zv6000 with amd64 arch."
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by dsierpin on 2005-12-22
Hello!

I've been using these forums to answer all the many questions I have about installation, and they've helped me a lot.  However, I'm trying to install drivers to get my dialup modem working (ATI softmodem with Conexant chipset) and I'm pretty much stuck.  I went to linmodems like everyone says, did the scan modem thing, then went to Conexant to download the drivers (hsfmodem).  I installed everything ok, compiled the modules and rebooted.  The system freezes when it gets to installing hotplug subsystems.  The linmodems mailing list folks say this is a common problem, and that I need to change to a kernel version 2.6.10 or earlier to solve it, as I currently have 2.6.12-9.  

This whole changing the kernel version thing sounds like a complicated mess, especially considering I have no internet connection.  I've seen kernel compilation HOWTO's, but they all download stuff using apt-get to resolve dependencies.  I've tried downloading and installing myself, but I get into serious dependency ruts where I need file a to install file b and file b to install file a.  

In short, my question is this: Is there any possible way to change my kernel version without an internet connection?  I can download files from another computer if necessary.  

Thanks so much in advance!

---

### Post by towsonu2003 on 2005-12-23
no idea about kernel compilation (did you check out debian howtos?) but you could pass a nohotplug option to your boot... So if your /boot/grub/menu.list have this default entry:
```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
``` try changing it to ```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash **nohotplug**
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```
and reboot
 
Hopefully this will fix the hang (although will stop hotplug)

If you can get your modem to work, then you can follow th howtos better I guess?

---

### Post by dsierpin on 2006-01-02
Thanks for the reply towsonu!

I tried passing the nohotplug boot parameter, but I get a freeze there anyway.  I reinstalled everything, and was able to download a 2.6.10 kernel image.  I had to download a few more files to resolve some dependency issues, but I got the kernel installed.  It won't boot, however.  At first I just got a blank screen on boot, but I fixed that by getting rid of the vga=771 boot parameter.  Now I get the following error:

```
kernel panic - not syncing : VFS: unable to mount root fs on unknown-block (0, 0)
```

Everything is fine in menu.lst, so I was told that there is some faulty partition bit that I need to fix with the rdev tool.  This tool is part of util-linux, but is only for i386 architectures.

Is there some command for the AMD64 arch. that I can use to change where the kernel thinks the root filesystem is?

Thanks!

---

### Post by towsonu2003 on 2006-01-07
a kernel panic is absolutely over my head. hopefully someone else will come by and help... You might want to open a new thread for this one if there is no answer in a week or so...

---

### Post by dsierpin on 2006-01-07
I've been in contact with a guy from linmodems who says that the problem can only be fixed by rolling back the kernel, because the driver simply doesn't work with the 2.6.12 kernel.  But he said that a new driver would be out soon.  I'll keep working at this in the meantime, and anybody who has this problem, keep an eye on the [Linuxant hsfmodem page]("http://www.linuxant.com/drivers/hsf/full/downloads.php").

As of this post, the current version is 7.18.00.07.

---

### Post by dsierpin on 2006-01-19
I installed the i386 version of Ubuntu, and the hsfmodem package installed swimmingly.  I can finally connect to the internet!  I only have a 14.4k connection which I'll have to make due with until I decide to cough up the 20 bucks for the 56k version or until I get my DSL fiasco straightened out (stay away from Wanadoo by the way, they are the devil).

---

### Post by danielta on 2006-02-12
i have exactly this problem with this driver on an acer aspire 5020 amd64 turion; how can i resolve this problem? 
i have installed hsf driver and my kubuntu 5.10 doesn't start any more!

thanks!

Danielta

---

### Post by dsierpin on 2006-02-13
Hmmm... I had to trash my previous installation.  Or rather, I decided to trash it instead of coming up with a more graceful solution.  There's probably a boot parameter you can pass that'll keep the hsfmodem module from loading, try "nohsfmodem" perhaps?  That is a total guess.

If you could do that you could boot up and uninstall that package.  Anybody else have any input on this?  Thanks.

---

### Post by towsonu2003 on 2006-02-13
[QUOTE=dsierpin]Hmmm... I had to trash my previous installation.  Or rather, I decided to trash it instead of coming up with a more graceful solution.  There's probably a boot parameter you can pass that'll keep the hsfmodem module from loading, try "nohsfmodem" perhaps?  That is a total guess.

If you could do that you could boot up and uninstall that package.  Anybody else have any input on this?  Thanks.[/QUOTE]
I am not entirely sure about what I'm talking about but here I go: 
You could boot from the live cd, open up the terminal, check for your / partition (is it mounted?), mount your / partition under /media/something, chroot into it (i'm not sure how to), and sudo apt-get uninstall "package name" to remove the hsf package. would this work??

also, did anyone reported this as a bug? it seems to be a critical bug.

---

