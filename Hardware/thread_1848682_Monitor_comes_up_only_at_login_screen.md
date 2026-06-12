---
title: "Monitor comes up only at login screen"
date: 2011-09-23
forum: Hardware
---

### Post by -Shuji- on 2011-09-23
I have an external monitor connected to my Pavilion dm1z laptop.  I normally use my external monitor and keep the laptop LCD closed.  The monitor only comes up at login screen, it stays black when the laptop is showing POST and Grub menu.  How can I tell Ubuntu to start using my external monitor right after I press the power on button?

Shuji

---

### Post by lightwarrior on 2011-09-23
The monitor is detected after boot.  This is not an Ubuntu issue.
During power up, the BIOS manages video output.
There is no BIOS option to select a different video output on the dm1z.
Still, you need the LCD lid open to access the power button on this machine.

---

### Post by -Shuji- on 2011-09-23
> **lightwarrior said:**
> The monitor is detected after boot.  This is not an Ubuntu issue.
During power up, the BIOS manages video output.
There is no BIOS option to select a different video output on the dm1z.
Still, you need the LCD lid open to access the power button on this machine.

Lightwarrior, I checked the BIOS and like what you said, there is no option to select a different video output.  Thanks a lot for helping me understand this.

Shuji

---

### Post by lightwarrior on 2011-09-23
You're welcome.

Maybe putting Ubuntu in suspend mode instead of shutting down, will allow you to bypass this POST/grub on LCD and login much faster.

---

### Post by -Shuji- on 2011-09-24
> **lightwarrior said:**
> You're welcome.

Maybe putting Ubuntu in suspend mode instead of shutting down, will allow you to bypass this POST/grub on LCD and login much faster.

Thanks, Lightwarrior.  That is a good idea, however, suspend and hibernate does not work on dm1z.  This is something that I have to fix.

Shuji

---

