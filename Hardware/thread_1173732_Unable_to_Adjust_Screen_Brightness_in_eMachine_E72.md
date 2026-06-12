---
title: "Unable to Adjust Screen Brightness in eMachine E725"
date: 2009-05-30
forum: Hardware
---

### Post by rojakcoder on 2009-05-30
Hi,

I'm using a eMachine from Acer. The model is  E725 (seems to be quite new).

I have a problem with adjusting the screen brightness. It is always at 100%. I can't dim it. Here's what I've tried.

1. The function keys. The function keys respond - when I press the key for dimming or making it brighter, the screen shows that it understands the keys but the screen brightness doesn't change.
2. The Brightness applet on the menu bar. I've added it to the menu bar and tried to adjust it. But the brightness doesn't change as well.
3. I've resorted to using the command line:
```

#cat /proc/acpi/video/OVGA/DD03/brightness
levels: 10 20 30 40 50 60 70 80 90 100
current: 20
```I then attempted to change it using:
```
#echo 50 > /proc/acpi/video/OVGA/DD03/brightness
```I've googled for help but to no avail. It seems that there is a problem with the hardware understanding the command to change the screen brightness. I like to point out there there are other directories in /proc/acpi/video/OVGA:

```
/proc/acpi/video/OVGA:
DD01  DD02  DD03  DD04  DD05  DOS  info  POST  POST_info  ROM

/proc/acpi/video/OVGA/DD01:
brightness  EDID  info  state

/proc/acpi/video/OVGA/DD02:
brightness  EDID  info  state

/proc/acpi/video/OVGA/DD03:
brightness  EDID  info  state

/proc/acpi/video/OVGA/DD04:
brightness  EDID  info  state

/proc/acpi/video/OVGA/DD05:
brightness  EDID  info  state

```

Only the brightness file under DD03 responds to any command.

Any pointer is appreciated.

---

### Post by rojakcoder on 2009-05-31
Any one? Bump

---

### Post by rojakcoder on 2009-06-04
I'm willing to go down to the kernel level, even attempting to recompile it. If anyone has a pointer or can point me to the right source, it's greatly appreciated.

---

### Post by mares.home on 2009-09-02
Hi
I have got the same laptop and have the same problem.
I have found that if you boot Ubuntu 9.04 with acpi=off kernel parameter, then Brightness adjustment works fine, but all other things that relative to acpi don't work, even wifi, but if boot with acpi switched on - everything works except brightness adjustment.
Any other kernel boot parameters don't work.
I believe that problem is with wrong (or new, unknown) ACPI table.
Any suggestion?

---

### Post by rojakcoder on 2009-09-09
This is an update to help those with the same issue on the same machine.

Thanks to Mares, he has managed to find a semi-solution to the issue. It isn't a complete fix in the sense that the keys will work perfectly or the screen resolution is maintained.

Basically, all you need to do is to add a kernel parameter **acpi_osi=Linux** to the file /boot/grub/menu.lst

Again, this is Mares' credit.

Hope this helps someone out there.

---

### Post by rojakcoder on 2009-10-23
Just want to post an update that with the new kernel 2.6.28-16 (Jaunty Jackalope), the same kernel parameter works. The only issue is that when updating the kernel, there is a message saying that the file menu.lst has been modified. You can choose to use the one from the update and then add in the kernel parameter later.

Cheers.

---

### Post by bradmayne04 on 2010-04-06
there is no text in my menu.lst file I'm using 64 bit 9.10 karmic ubuntu.  Should there be text am I missing something?

---

### Post by ahallubuntu on 2010-07-18
I have 9.10 (32 bit) on my E725.  Since 9.10 and onward use Grub2 not Grub, there is no more menu.lst file to edit.  Instead, you add the magic above to the file /etc/default/grub .  

```
sudo gedit /etc/default/grub
```

Find the line "GRUB_CMDLINE_LINUX" and change it to this:

GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Then update grub:

```
sudo update-grub
```

And reboot.

It worked for me - except that the brightness controls are REVERSED!  (Fn-up reduces brightness, Fn-down increases it.)  And hitting Fn-up actually types a character.  Hmm...

---

### Post by petr.simacek on 2011-10-14
Works in Debian Squeeze aswell! Thanks ahallubuntu! P.

---

