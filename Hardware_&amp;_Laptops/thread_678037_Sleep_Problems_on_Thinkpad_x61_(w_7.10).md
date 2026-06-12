---
title: "Sleep Problems on Thinkpad x61 (w/ 7.10)"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by daphreak on 2008-01-25
So I'm running Gutsy on my x61 and really enjoy it (compiz works great, tablet is nice)

I will be posting my list of fixes soon so others can hopefully benefit.

But unfortunately I am still having problems with putting my laptop to sleep. Initially (for the first week or so) the only problem I had was that when it woke up from sleep it would not turn on the backlight for my screen. This was easily fixed by going to tty1 and then back to tty7 where the unlock screen greeted me. No big deal.

Now (sometimes, not always) when I wake it up the sleep light turns off and then the computer is unresponsive. Sometimes if I wait and press Enter or move the mouse it will come back to life. Sometimes it will not. Recently it has also fallen into a state where I have not been able to wake it. The sleep and caps lock lights just flash on and off.

On the other hand, sometimes it has trouble going to sleep. When I try to put it to sleep the  sleep light flashes but it never really goes to sleep (when it is asleep the sleep indicator light is just constantly on). I can open the lid and my screen is locked. I log back in and the light continues to flash but the system is completely functional (awake).

I have a feeling that all these problems are stemming from the same source, but im not sure where to look for logs and the fixes I have found elsewhere in the forum have been relatively specific for a certain machine. Any ideas?

---

### Post by wwbkmd on 2008-02-02
daphreak,

I"m having the same initial issue as you. My X61 (non tablet) is also not turning on the backlight upon wake-up. It is my first week  with Ubuntu. Could you please better explain how you fixed the backlight issue? Thanks.

---

### Post by Yellow Pasque on 2008-02-02
> **wwbkmd said:**
> daphreak,

I"m having the same initial issue as you. My X61 (non tablet) is also not turning on the backlight upon wake-up. It is my first week  with Ubuntu. Could you please better explain how you fixed the backlight issue? Thanks.
After you resume, press Ctrl+Alt+F1 and then Ctrl+Alt+F7. You could probably automate this as well.

---

### Post by wwbkmd on 2008-02-02
Thank you, this works!

---

### Post by mbsullivan on 2008-02-07
Hi everybody,

Suspend is notoriously finicky on a number of laptops, so it may not be possible to get it working 100% at this point.  A fix for the backlight issue, in many cases, is to add acpi_sleep=s3_bios to the boot options for your kernel. Assuming you're using GRUB as your bootloader, this entails editing /boot/grub/menu.lst.

If you're as lazy as me, the whole process should be accomplished through the following commands:

```
sudo sed -i.bak -e 's/\(^# kopt=.*$\)/\1 acpi_sleep=s3_bios/g' /boot/grub/menu.lst && sudo update-grub
```

Also, if the default ACPI sleep script works for you (other than the backlight issue), great! I have an x61, and I've found uswsusp's s2ram program ("s2ram --force") more reliable. Unfortunately, somebody made the (very) poor decision to remove s2ram from the Gutsy package for uswsusp, so I've resorted to pegging my version to the Feisty release in order to retain my suspend functionality.

Let me know if you want any more info on this... Cheers!
Mike

---

### Post by daphreak on 2008-04-21
Thanks! I actually found this solution recently on my own but it works well. I had been switching to the virtual terminals and back, but that was more of a hack than a solution.

I still have some freezes after resuming, but the backlight always comes on. One down one to go : ) (maybe moving to hardy will fix this)

---

