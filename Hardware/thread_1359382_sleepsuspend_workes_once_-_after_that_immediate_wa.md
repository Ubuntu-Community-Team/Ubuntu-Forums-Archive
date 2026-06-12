---
title: "sleep/suspend workes once - after that immediate wakeup"
date: 2009-12-19
forum: Hardware
---

### Post by Bagh33ra on 2009-12-19
I have a new install of 64-bit karmic (Gnome and KDE), dualbooting with XP on a desktop with the ASUS M3N78-EM Mobo.

My problem, is that I can suspend to RAM only once. The first time everything works just fine, the computer suspends, and starts nicely from the power button. But if I try to suspend a second time (without a reboot or hibernate in between), the computer first seems to suspend, but then immediately wakes itself up again. After this I can continue to work normally, but suspend continues to wake itself up, whenever I try it. 

my /proc/acpi/wakeup shows everything as disabled (no poweron in there).

Here is my pm-suspend.log with an immediate awake, in case it's of any help.

---

### Post by staticsage on 2010-01-01
I don't know why it works, but add the following to the end of your kernel line in /boot/grub/menu.lst

```
usbcore.autosuspend=-1
```


Source: [http://xbmc.org/forum/showthread.php?&t=60127&page=6](http://xbmc.org/forum/showthread.php?&t=60127&page=6)

---

### Post by Bagh33ra on 2010-01-02
Thank You!

That seems to solve it. Although your solution was for the old grub. With a fresh Karmic, I have grub 2 and had to do the following

1.
add "usbcore.autosuspend=-1" to the  GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub
2.
run sudo update-grub
3.
reboot

After that I have suspend working as many times i like. Can anyone tell me what kind of averse effects disabling the usb autosuspend will have on my system, if any?

Marking this as solved.

---

### Post by staticsage on 2010-01-02
I do not think there are any adverse effects associated with this setting. I actually spent a good portion of the day searching for why usbcore.autosuspend causes the machine to wake up immediately.

The only thing I could come up with is that autosuspend tries to suspend a USB device only to have the USB device "wake up" after the computer was in standby. This would cause the system to resume because of the USB wakeup. I have no idea if that is the reason, but it is my best guess.

This link talks about usbcore.autosuspend: [http://lwn.net/Articles/253587/](http://lwn.net/Articles/253587/)

Also, adding the line
```
options usbcore.autosuspend=-1
```
to /etc/modprobe.d/options is a method to disable without messing with your bootloader.

---

### Post by Bagh33ra on 2010-01-03
Again, that does not work on my system. 

Without being sure at all, I think this has to do with which kernel you are running. If I have understood what I have read correctly, some older kernels run usbcore as a module (modprobe.d/options is the place), whereas the newer kernels (2.6.30 upwards???) has it in the kernel itself?

---

### Post by DLGandalf on 2010-01-13
thanks so much for this solution.
Is this a motherboard/bios bug?

Could I've debugged this myself, because I spent way too much time into this and feel very stupid.

---

