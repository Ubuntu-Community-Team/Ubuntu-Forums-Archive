---
title: "[SOLVED] laptop_mode is not running"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by azelter on 2007-11-08
I'm running a fresh gutsy install on my HP dv6120us. It has laptop_mode installed, however, when I do:
/etc/init.d/laptop-mode start
it does not seem to start
when I do:
/etc/init.d/laptop-mode status
I get nothing.
And when I unplug the AC power, the settings listed in /etc/laptop-mode/laptop-mode.conf do not take effect.
I have also tried making /proc/sys/vm/laptop_mode > 0
laptop_mode still appears not to be running.
I had thought that laptop_mode should just happen automatically for laptops. Am I missing something?
Thanks!
Alex

---

### Post by Perpetual on 2007-11-08
```
sudo gedit /etc/default/acpi-support
```

Scroll to bottom and change laptop-mode to 'true'.

---

### Post by azelter on 2007-11-08
Great. Now it works. Man I never would have guessed that. There is nothing in /usr/share/doc/laptop-mode-tools/README to say that, nor, so far as I can see, is there that info anywhere else that I would have found.
Thanks alot. Any advice for how I would come to know these little (but rather significant) obscurities in the future. Other than bugging the likes of you of course ;)

---

### Post by Perpetual on 2007-11-08
> **azelter said:**
> Great. Now it works. Man I never would have guessed that. There is nothing in /usr/share/doc/laptop-mode-tools/README to say that, nor, so far as I can see, is there that info anywhere else that I would have found.
Thanks alot. Any advice for how I would come to know these little (but rather significant) obscurities in the future. Other than bugging the likes of you of course ;)

Not bugging me.  And I only knew that because I'd already been on that mission myself :)

---

### Post by lapchumi on 2008-01-16
I have 5.04 Hoary Hedgehog and randomly when i open the lid or unplug it and then click somewhere the computer will go into laptop mode (this is assuming that laptop mode is a black screen with white type that continues where the startup log left off and asks you to re-login). I am wondering how i can shut this off or exit it back to the normal view with the desktop?

---

### Post by azelter on 2008-01-16
This is not laptop mode. This is your non-graphical terminal. You either reached it because your X server stopped for some reason, or because you pressed ctrl+alt+f1 or some other f key. Or, perhaps, because your power management is set to do something your system can't handle when you close the lid or unplug the power.
Graphical mode lives in tty7. Boot up output is normally in tty1. You normally reach these displays by pressing ctrl + alt + the appropriate f key. Try ctrl + alt + f1 and then ctrl + alt +f7 to get back to where you are now. If you are just 'randomly' entering this mode after closing the lid or unplugging power then I guess something strange is being tripped by your power management configuration.
What laptop do you have. If you look in /var/log/messages after this error occurs what do you see?
Cheers,
Alex

---

### Post by lapchumi on 2008-01-16
Thanks I will try this out next time the problem occurs.

---

