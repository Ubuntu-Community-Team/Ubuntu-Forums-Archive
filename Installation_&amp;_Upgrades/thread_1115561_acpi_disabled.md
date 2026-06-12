---
title: "acpi disabled"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by 123456789123456789123456 on 2009-04-03
Hi guys, I have this error on a machine I am just installing xubuntu 8.10 on, so that I can sell it.

grub comes up

error BIOS age 1998, turnoff failed, cutoff 2000 acpi disabled, acpi-force required to enable acpi.

I know from reading some of other fourms, from a guy that had 7.04 and had a simular error, his was age 1999.

I have to edit grub, I think /boot/grub/menu.lst.
I just need to know exactly where in the file I need to edit, before I spend time messing with vi editor, to get it to save, If someone knows of a way I can edit the file within GNU, I would appreaciate it.

---

### Post by Partyboi2 on 2009-04-04
You can follow [[COLOR=Blue]this [/COLOR]]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation")to add the boot option to your grub menu.lst

---

### Post by 123456789123456789123456 on 2009-04-04
I know what command to add, but I can't tell from the documentation exactly were in the list to add the acpi=force command.  Can someone tell me at the end of what line I should add this?

---

### Post by Partyboi2 on 2009-04-04
Look for this section of your menu.lst
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro splash
then add it at the end of the  '# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro splash' line, so it will look something like this

```
# kopt=root=UUID=ff13903a-c958-47a0-8292-f482063226ee ro splash [COLOR=Red]acpi=force[/COLOR]
```

---

### Post by 123456789123456789123456 on 2009-04-04
Thanks, I will try that as soon as possible.  I seem to have another lovely error with the machine, though I don't think it has anything to do with acpi.  I can terminate power by using the BIOS/cpu function of holding down power button.  However for some reason several minutes after it shuts down, the computer restarts.  I could not find anything in BIOS to assist, thought it may be a timer set for auto resume.  I reset the BIOS to defaults, and it seems to be working correctly now.  I know this probably has nothing to do with this forum, unless, there is some function in xubuntu I don't know about that could be causing this in some way.

---

### Post by 123456789123456789123456 on 2009-04-07
I managed to enable acpi using the command, and the computer shuts down, and powers off normally, however every time the computer starts up, just after the text to go to the edit screen, it pops up with that same error.  I added the code to part of the menu.lst that was listed in a file I saw, after the kernal start up, for the newest kernal on the machine, it works, but I would like to know if there is a way to either remove that error text from appearing, or to at least hide the text, so that new users that may use the machine want get confused.

---

