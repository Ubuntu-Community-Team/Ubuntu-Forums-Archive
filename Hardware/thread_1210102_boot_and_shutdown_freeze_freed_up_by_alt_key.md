---
title: "boot and shutdown freeze freed up by alt key?"
date: 2009-07-11
forum: Hardware
---

### Post by mlitty on 2009-07-11
I just installed 9.04 64bit on my HP Pavilion dv6000.
[INDENT]Hardware[/INDENT]
[LIST]
[*]AMD Athlon64/Opteron
[*]nVidia GeForce 7150M
[*]Ricoh Co Ltd xD-Picture Card Controller
[*]Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express
[/LIST]

During the install boot, and now during some post-install boots the screen gets through grub and settles on a black screen.  If I press the alt key, the screen progresses to the progress bar which freezes.  It will start when I press and hold the alt button, but freezes again when I let off of the alt key.

Sometimes it also freezes on the shutdown progress bar, and continues with the  press of the magic alt button.

I'm using the "recommended" nvidia drivers, "NVIDIA accelerated graphics driver (version 180)

I'm not sure what wireless driver is running.  The proprietary "Alternate Atheros "madwifi" driver is grayed to indicate not in use, but the wireless card is working well, right out of the box.

I didn't see anything glaring in "/var/log/messages"
I did see this in dmesg.
> eth0: no link during initialization.
[   55.488571] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.269812] ADDRCONF(NETDEV_UP): wlan0: link is not ready


This one has me perplexed.  What's up with the freezes and that all powerful alt key?  Is there a way to track this down and fix it?

More testing.  It's not a magic alt key.  It's a magic any key.  The space, b, just about any button will keep things going.

Is there a way to disable those boot and shutdown screens so I can get and old fashioned linux screen with all of that wonderful what's going on info?  I tried to pull "quiet splash" out of the grub menu.list, but still see that pretty progress bar on boot and log off.

---

### Post by SteveDee on 2009-07-11
> **mlitty said:**
> I just installed 9.04 64bit on my HP Pavilion dv6000.

...is there a way to disable those boot and shutdown screens so I can get and old fashioned linux screen with all of that wonderful what's going on info?  I tried to pull "quiet splash" out of the grub menu.list, but still see that pretty progress bar on boot and log off.

Removing "splash" from menu.lst should work (I've just tried it). Just be sure you operate on the correct text block. In my case I'm booting from this text block:-

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dc7c3e4c-73c1-4bd9-96ae-aca1405bd761 ro splash vga=771 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

...taking "splash" out of the kernel line works for me.

---

### Post by mlitty on 2009-07-19
Thanks SteveDee.  That did work.

I also have another important bit of info.  I've been trying to find the trigger for these halting starts and shutdowns.  It has something to do with being on battery power.  If I boot or shutdown on while on battery power, the process halts several times during the boot and/or shutdown sequence.  Every time I boot while on battery, it's a halting boot.  Every time I shutdown on battery, it's a halting shutdown.  While plugged in, it's fast and there are no halts.

Thanks to SteveDee, I was able to see what is scrolling by during the boot halts.

The first halt happens when this appears
```
Begin: Running /scripts/init.premount ...
```
then I tap shift, ctrl, or alt and it continues to 
```
 forec death 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3 
```
the another tap and the next halt is on
```
setting preliminary keymap ...
``` 
then there are several more tap and halts, including 
```
On battery power so skipped file check
```
and then a few more tap and halt iterations until finally reaching the log in screen.
As I watched the boot script info scroll by, everything that I noticedhad an "[OK]".  Nothing reported "[FAILED]".

One solution, of course, would be to always boot and shutdown while plugged in, but that sort of defeats the pupose of a laptop.

Does anyone out there have a suggestion?

---

### Post by mlitty on 2009-07-19
With the new information, I was able to use some different search terms and found a thread with a description and solution at
[URL="http://ubuntuforums.org/showpost.php?p=7575302&postcount=9"]
http://ubuntuforums.org/showpost.php?p=7575302&postcount=9[/URL]

Unfortunately, it's an involved fix.  If anyone has some insight into the easier "work around" he mentions, please post in that thread.  I'll be watching there.

This thread can be removed, marked as duplicate, or marked solved.

Thanks.

---

