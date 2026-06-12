---
title: "Screen brightness controller stops work after sleep mode"
date: 2011-09-20
forum: Hardware
---

### Post by Teraspes on 2011-09-20
Hi!

I have a Toshiba R830 laptop. The problem I have is that the screen brightness controller stops work after I resume the computer from sleep mode. If I do a complete reboot - I can change the screen brightness. It works if I wake it up from hibernate too. But not from Suspend.

I have tried to set the brightness from the terminal too - but it doesn't work either.

```
sudo pkexec gnome-power-backlight-helper --set-brightness 1
``` doesn't do anything. Neither does: ```
sudo acpitool -l 1
```Does anybody here know if this is possible to solve in some way? Is it possible to restart a fitting daemon or something? Or are there any logs that I should look in?

I'm thankful for all answers. :)

---

### Post by faceonline on 2011-09-22
+1 Toshiba R700. Only noticed this the other day. Have you tried restarting X? Not that that's a fix though...

---

### Post by technosysind on 2011-09-22
What are your settings in power management??

---

### Post by filipejps on 2011-09-30
Same problem here with my Toshiba tecra m11

---

### Post by Teraspes on 2011-10-24
I'm sorry, I forgot this thread. I still have the problem. :/

> **faceonline said:**
> +1 Toshiba R700. Only noticed this the other day. Have you tried restarting X? Not that that's a fix though...
No, how do I do that?

> **technosysind said:**
> What are your settings in power management??
Umm.. 
On Battery Power:
Put computer to sleep ..: never
Lid closed: Suspend
Battery critically low: Suspend
Spin down hard disks: checked
Put display to sleep ...: 0:30
Reduce backlight: unchecked
Dim display when idle: unchecked

---

### Post by Sonador on 2012-01-20
Any ideas? Same problem on Acer Extensa with GMA 4500

I have read a lot of posts about this issue but have found no solution. It is annoying and it affects different distros, I read even several posts about the problem on Windows...huh

---

### Post by Sonador on 2012-04-28
Nice, I've installed the new 12.04 xubuntu and it is OK now.

---

