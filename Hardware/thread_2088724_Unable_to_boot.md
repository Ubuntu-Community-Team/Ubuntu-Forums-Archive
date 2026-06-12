---
title: "Unable to boot"
date: 2012-11-27
forum: Hardware
---

### Post by avermaa on 2012-11-27
This is the error that I got while booting edubuntu today:-

After selecting normal boot from grub, i got a screen saying - 'Your screen, graphic card and input device settings could not be detected correctly. You will have to configure them yourself.' At this time only keyboard was working. On pressing enter, I got the next screen with following message.

'What would you like to do:-
- run low graphic mode for now.
- reconfigure graphic setting.
- troubleshoot.'

But the worst part that not even keyboard was working at this time. I dont know how to select any option at this time. But on pressing the escape key, the screen goes but there is no prompt to enter any command.

Help, need urgent help.

Thanks

Ashutosh

---

### Post by dandnsmith on 2012-11-27
Just a thought - any chance your CMOS battery has died, and you've lost the settings? Classic indication is that the date and time are no longer correct on boot.

---

### Post by avermaa on 2012-11-27
> **dandnsmith said:**
> Just a thought - any chance your CMOS battery has died, and you've lost the settings? Classic indication is that the date and time are no longer correct on boot.

But the windows partition is just fine. So it cant be cmos.

---

### Post by Bashing-om on 2012-11-27
avermaa; Hi !
Try this and see:
Boot into the ubuntu install, at the grub menu hit an arrow key to halt the boot countdown; arrow back up to the latest ubuntu non-recovery kernel (now highlighted)
"e" key for edit -> boot sequence -> arrow down to the line similar to this:
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash -> arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-:
ctl + x to continue to boot.
This procedure disables Kernel Mode Setting in the operating system. 

Can you now boot to the desktop (degraded graphics -> might be fixable later) ?

[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

