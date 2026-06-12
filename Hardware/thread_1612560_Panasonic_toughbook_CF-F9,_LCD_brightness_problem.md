---
title: "Panasonic toughbook CF-F9, LCD brightness problem"
date: 2010-11-03
forum: Hardware
---

### Post by quercus54 on 2010-11-03
ubuntu 10.10 desktop, 32 or 64 bit. Adjusting the LCD backlight brightness seems to be impossible. The mechanism of the function keys Fn-F1,-F2, the onscreen "brightness" slider, the value in /sys/devices/virtual/backlight/panasonic/brightness, everything works fine. But there is never ever any influence on the real backlight brightness of the laptop display. Normally it always remains on its maximum brightness, in rare cases it boots with its minimum brightness instead. The laptop is hardly usable this way:
Can anybody please provide some hints on how to solve the issue.

---

### Post by P4man on 2010-11-03
Thats usually an ACPI problem. Any chance you can update the bios?

As a workaround, try booting with 
```
acpi_osi=
```

as kernel option (indeed nothing behind the = sign). 

To test that solution, enter grub menu, edit the default line (press E) and at the line that ends with ```
quiet nosplash 
```just add the above option. 

```
 blahblah quiet nosplash acpi_osi=
```
Press control+x to boot.

If it doesnt help, you can experiment by adding 

  acpi_osi="Linux"

This only works for one boot, but if it helps we can make it permanent.

---

### Post by quercus54 on 2010-11-04
Problem solved! P4man, your advice was a 100% hit.
After adding the boot option
  acpi_osi=
the LCD brightness function keys work perfectly, and there are no more dmesg complaints: "ACPI: Failed to switch the brightness".
(Instead acpi_osi="Linux" does not help)
I made the modification permanent by adding the boot option into /boot/grub/grub.cfg

Thank you very much !

Of course now, I wonder, what is the mechanics of this option.

---

### Post by P4man on 2010-11-04
glad it worked.

Beware though, if you are using grub2 (which you are with ubuntu 9.10 or later) do not edit grub.cfg. It will be overwritten with the next update. Instead, follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

As for what it does; the details are beyond my comprehension, but as I understand it, its a workaround to disable some bios/acpi functionality where the bios queries the OS and sets settings depending on what OS is reported. Unfortunately many bioses dont work properly if they dont get the expected "windows" result and therefore fail to initialize some hardware.  As I understand the above setting lets the kernel figure it out, rather than rely on the bios.

---

### Post by quercus54 on 2010-11-04
Thanks for the link to the grub2 how-to. I am aware of the fact, that I'll have to re-new the entry in grub.cfg once I update the kernel That's something, I could live with. But of course, if there's an easy way around, I'll follow it.
As to your explanation about the "acpi_iso=" entry. That's very interesting, but alarming as well. Is this BIOS <--- Windows "collaboration" a new way of locking out other OSs than dammed windoze?
BTW, I wonder, what happens, if I boot with acpi_iso="Windows".

Thanks again for your help, good night (Europe)

---

### Post by P4man on 2010-11-04
> **quercus54 said:**
> Thanks for the link to the grub2 how-to. I am aware of the fact, that I'll have to re-new the entry in grub.cfg once I update the kernel That's something, I could live with. But of course, if there's an easy way around, I'll follow it.

There is. See my link and follow the instructions to make it permanent.

> As to your explanation about the "acpi_iso=" entry. That's very interesting, but alarming as well. Is this BIOS <--- Windows "collaboration" a new way of locking out other OSs than dammed windoze?


Its not new. Its been a problem since, forever. The fact bioses arent written to work well with non windows OS's isnt a conspiracy though, its just a result of linux marketshare. What is food for thought is the fact many bioses are compiled with a microsoft acpi compiler that has age old and known bugs that dont get fixed (but that do not affect windows). Some people decompile the acpi code and recompile it with an intel acpi compiler so the code works on linux. Draw your own conclusions from that.

---

### Post by listerdl on 2011-04-06
Really nice machine by the way - I have the Toughbook CF F8 - the generation below yours, seriously thinking of getting yours this year - its got the 64 bit processor which is sweet.

I had the same problem with the screen but my work around was actually fixed when I installed the Ubuntu Tweak Center - might be unrelated to your problem though.

For those reading this try to see if the settings were low in the Ubuntu Tweak program if you have it installed.

THanks!

---

