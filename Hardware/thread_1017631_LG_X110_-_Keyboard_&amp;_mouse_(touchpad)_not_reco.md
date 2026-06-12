---
title: "LG X110 - Keyboard &amp; mouse (touchpad) not recognized on boot (grub)"
date: 2008-12-21
forum: Hardware
---

### Post by IceDrake on 2008-12-21
Greetings.

I have recently bought an LG X110 netbook ([http://ae.lge.com/products/model/detail/x110.jhtml](http://ae.lge.com/products/model/detail/x110.jhtml)) and as I "liberated" it from XP Home, I've noticed something strange about it:

When I turn on the device and boot into one of the *buntus (I haven't tried other distros really), the first two or three boots go with the keyboard and mouse (touchpad) not being recognized - even the CapsLock/NumLock lights don't light up as if the keyboard was physically disconnected. CTRL+ALT+DEL doesn't work - only the power button does, once X has loaded. When I plug in a USB keyboard and/or mouse, those detect and work alright, but not the on-board ones. After two or three reboots, everything starts to work again.

The keyboard lockdown doesn't start at X startup, by the way - it starts just as grub starts to boot one of the kernels - after the menu where you select what to start. The selection menu works alright and after that, the keyboard is no longer operational.

This seemed to be the case with all the *buntus I've tried - Ubuntu, Kubuntu, Xubuntu.. I converted the CD images to be used on my USB flashdisk with UNetbootin and those booted just fine - no keyboard problems whatsoever - it's when I install the distro, this starts to happen.

While I haven't seen nearly anything on this specific matter on Google, I did notice a forum post on remote-exploit.org that seems to be very similar to mine and it involves the same exact netbook that I use: [http://forums.remote-exploit.org/showthread.php?p=109383](http://forums.remote-exploit.org/showthread.php?p=109383)
Their specific problem is with BackTrack.

I will try installing lilo now and eventually see if the problem returns, otherwise I'm rather at loss. This seems to be something with grub or the way kernel detects devices, but my knowledge there is rather limited as to what could I do to "suggest" it where to find my keyboard. I am otherwise an experienced Linux user.

Thanks in advance.

---

### Post by IceDrake on 2009-02-21
Booting with the kernel parameter **irqfixup** appears to help me here, so in case and anybody else stumbles upon this problem with their X110, give this a try!

---

### Post by xvilar on 2009-11-16
> **IceDrake said:**
> Booting with the kernel parameter **irqfixup** appears to help me here, so in case and anybody else stumbles upon this problem with their X110, give this a try!

ICeDrake, please, could you let know a newbie as me how to boot the Ubuntu kernel with parameter irqfixup ?¿ I'm usign 9.10 and Grub as bootloader... I know that i can change boot parameters editing the boot lines, but i dont know which to change.

I've done it on Backtrack and it works one time, other not...

Thnx in advance! Cheers!

---

### Post by IceDrake on 2009-11-19
I'm running Kubuntu, but the files should be the same in theory.

Before doing a permanent change, I suggest you to try the temporary one. It's safer, gives you a hang of editing this stuff and can actually show you if this method works or not.

With more observation, I've noticed that **irqfixup** option might not be the one doing the magic here. I had the keyboard failing even with it! What actually did the trick is me doing the Temporary Change bit, but without going through steps 4 and 5 - without editing anything! I just stayed in that area for a few seconds and told it to boot with the B key, and it worked - the keyboard wasn't failing on me when I did that!

I suggest you try this before you go with irqfixup. It might be a bit less convenient, but chances are - that's what makes the keyboard work, not irqfixup - just letting it wait for a bit until something inside activates the keyboard...

Good luck.


**_Temporary Change_**
Normally, before Linux starts to boot, you are given a few seconds to press the ESC key to change what are you booting - either this, or you'll get the actual GRUB menu. Either way, here's what you do:
[LIST=1]
[*]Get to this menu
[*]Select the option you would like to boot (usually the first one)
[*]Press the E key to edit it.
[*]Select the line that starts with **kernel** and press E again.
[*]Use the arrow key to position the cursor between **ro** and **quiet** and add **irqfixup** to it.
[*]Press the B key in order to boot this option with your changes applied.
[/LIST]
In theory, your keyboard and touchpad should be functioning now.


**_Semi-permanent Change_**
The file you need to edit as root is **/boot/grub/menu.lst** (make a backup copy of it in case and something messes up). Down below, you will see the kernel options looking like this:

> title           Ubuntu 9.10, kernel 2.6.31-14-386
uuid            b33729ea-ba15-4fb3-b7df-c2dd92d323ef
kernel          /boot/vmlinuz-2.6.31-14-386 root=UUID=b33729ea-ba15-4fb3-b7df-c2dd92d323ef ro quiet splash
initrd          /boot/initrd.img-2.6.31-14-386
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-386 (recovery mode)
uuid            b33729ea-ba15-4fb3-b7df-c2dd92d323ef
kernel          /boot/vmlinuz-2.6.31-14-386 root=UUID=b33729ea-ba15-4fb3-b7df-c2dd92d323ef ro  single
initrd          /boot/initrd.img-2.6.31-14-386

In the line starting with **kernel**, add **irqfixup** in between **ro** and **splash** so it looks like this:
> kernel          /boot/vmlinuz-2.6.31-14-386 root=UUID=b33729ea-ba15-4fb3-b7df-c2dd92d323ef ro irqfixup quiet splash
(don't copy this line into your menu.lst file - edit your own! It's also not advised tinkering with the "recovery mode" option because it's there if you have problems with the main one)

When you're done, you need to actually re-install the boot loader from these settings in order to apply them. Open a terminal and type:
```
sudo grub-install /dev/sda
```
(if /dev/sda doesn't exist, try /dev/hda instead)

If there were no error messages, you can try rebooting and see if it works.

Keep in mind that when your automatic updates decide to update your kernel, you might need to repeat these steps again. Since I don't know how to force it have the irqfixup option, I had to re-add it manually. This tends to get annoying, so that's why I suggested to not bother with irqfixup all together if it's not what makes your keyboard work in the end.

---

### Post by xvilar on 2009-11-26
I've booted as you explain with Irqfixup and USB connectors doesn't works yet ... :-(

Regards.

---

### Post by IceDrake on 2009-11-26
I wasn't talking about the USB connectors, though. It was a problem with the actual keyboard and touch-pad on my netbook, not the ones externally connected via USB (which did work despite the failure with the on-board devices, mind you).

---

