---
title: "USB Booting"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by M@ndingo on 2005-03-27
I really like this distribution of Linux.  Is there a relatively easy method of copying the Live CD contents to my 1GB intellistick so it can boot a newer pc?

Thanks.

---

### Post by TravisNewman on 2005-03-27
Please watch where you post. Wrong forum section. Moving to the appropriate section.

---

### Post by broseman on 2005-03-27
Do you speak german a bit?

There is a HowTo in the german Wiki:
[http://ubuntuusers.de/wiki/installation:usb](http://ubuntuusers.de/wiki/installation:usb) 

Greetings,

 broseman

---

### Post by telmo on 2005-03-27
[QUOTE=broseman]Do you speak german a bit?

There is a HowTo in the german Wiki:
[http://ubuntuusers.de/wiki/installation:usb](http://ubuntuusers.de/wiki/installation:usb) 

Greetings,

 broseman[/QUOTE]


... And why not translate it to [English?](http://babelfish.altavista.com/babelfish/trurl_pagecontent?lp=de_en&url=http%3A%2F%2Fubuntuusers.de%2Fwiki%2Finstallation%3Ausb)
;)

---

### Post by broseman on 2005-03-27
> ... And why not translate it to English? 
Aaargh :-) Don't tell me you would understand *that*... :)
Okay folks, here is a quick 'n' dirty translation...

1. Reboot with Installation-CD in your drive

2. At boot prompt: custom-expert

3. Follow the instructions, but beware: a) Use the first partition to boot your system and b) It shouldn't be bigger than 8 GB

4. Move to a shell before the installation of GRUB

5. #nano /target/etc/mkinitrd/modules
add the following lines:
sd_mod
ehci-hcd
uhci-hcd
ohci-hcd
usb-storage

6.#nano /target/etc/mkinitrd/mkinitrd.conf
Change the value of DELAY to 10.

7. #chroot /target

8. #mkinitrd -o /boot/initrd.img-2.6.10-4-386

9. #exit

10. Install the bootloader into your Ubuntu partition (probably /dev/sda1)

---

### Post by pseudonym on 2005-03-28
This assumes that your motherboard supports booting from a USB device, right? (I read the German page and it didn't spell that out directly). I know my m/b doesn't but I was wondering if there was some way around that to make it work. Does anyone know? Thanks.

---

### Post by tool69 on 2005-04-12
Hi,
I've got a laptop with a 40GB internal drive and XP  [-o<  on it. I can't format it for several job reasons...
Now, I've installed Ubuntu on an external usb drive (80GB, hsa for linux), but can't boot on it (kernel panic).
Grub is on the internal disc.
I don't understand what you mean in :

1.Use the** first** partition to boot your system ( the one containing XP ?)

2.It shouldn't be bigger than 8 GB ( so I do have I to create a new partition on XP <8GB ?) 

3.What exactly is your **target** ? On my external drive, I've only 2 partitions : / (root) and a swap one.

Thanks for your help, sorry for my bad english :

Tool69.

---

### Post by broseman on 2005-04-12
Hi Tool69,
I will try to help you... But remeber that I was just the translator, not the original auther of the little howto.

> 1.Use the first partition to boot your system ( the one containing XP ?)
No, the first partition on your external drive.

> 2.It shouldn't be bigger than 8 GB ( so I do have I to create a new partition on XP <8GB ?)
Not on XP, but - again - on your external drive.

> 3.What exactly is your target ? On my external drive, I've only 2 partitions : / (root) and a swap one.
I would say, the author of the howto meant "target" as an replacement for the first partition. In your case, this would be (I guess...)

```
/dev/hsa1/
```

(By the way, are you sure it's "hsa"? Normally, usb-drives are mounted at "/dev/sda1" in ubuntu)

Greetings,

 broseman

---

### Post by tool69 on 2005-04-12
Thanks for your help broseman,

it's ok for the first two answers (so I have to create a new partition that's it ...a swap one, a root(/) one and another <8gb within the bootloader ?), but in the third point I've got a problem :
"/dev/hsa1/" --> that's what I though but when I come to the console, I've got no /dev/sda1 or /dev/sda2 !(sorry I was wrong with my hsa)
In fact, I've /dev/discs/disc0 and  /dev/discs/disc1 : difficult to know wich is what.

When I try "#nano /target/etc/mkinitrd/modules", then modules is empty !
this is the same for "nano /target/etc/mkinitrd/mkinitrd.conf", I can't change it as it's an empty document too.

For the 10th point, how can I "Install the bootloader into your Ubuntu partition (probably /dev/sda1)" ? ( a command line, but in this case wich one ?)

---

### Post by broseman on 2005-04-12
I would do it like this:

1. partition: /dev/sda1   /      
2. partition: /dev/sda2   /home
3. partition: swap

Put the bootloader onto the first partition (here: / )

Sorry, I have no clue, where your dev/sda1 has gone... :-( Maybe some other users could help us here?

Same with empty modules... :-(

Last issue: You'r looking for "grub-install". Take a look into "man grub-install".

Greetings!

---

### Post by tool69 on 2005-04-12
It works perfectly, thanks.

---

### Post by tomlink on 2005-04-14
Tried all these manuals, still doesn't work for me. I want to install Ubuntu on my external USB Harddrive with four partitions including root / (ext3), swap and /home (and an additional ntfs partition).

Modified the initrd to include the necessary modules, installed Grub to /dev/sda1, it starts to the menu, but any boot doesn't work. The kernel says it cannot access the drive hd(1,0) and ends up with the error 17.

However, I found out if I set root to (0,0) which is my internal harddrive with windows xp, I can load the kernel and initrd, but then it stops after a while with the error pivot_root: No such file or directory /sbin/init: 428: cannot open dev/console: no such file
Kernel panic - not syncing: Attempted to kill init!.

What am I doing wrong? Are the modules maybe not properly loaded so that I still cannot access the USB drive or what? Any help greatly appreciated.

---

### Post by hornblower on 2005-05-09
I'm getting the exact same pivot_root ... kernel panic error as the above poster. My current install has all the grub files on the external drive, so when I boot up with the external drive on, grub shows up instead of windows. I've tried tweaking some of the grub parameters, but to no avail. I think I know what needs to be changed, but I just don't know enough about grub syntax to make much progress. Grub is able to successfully uncompress the kernel, so I know that it's properly configured up to that point. Past that, though, I don't know how to tell grub or the kernel where my root partition is.

And if that isn't the problem, then maybe grub just needs to be installed to the MBR of the primary hard disk (something which i don't wish to do).

---

