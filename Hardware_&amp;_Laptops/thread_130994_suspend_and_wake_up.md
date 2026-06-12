---
title: "suspend and wake up"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by TheDarkKnight on 2006-02-15
I was facing a weird problem. The suspend feature worked perfectly, but when I tried to resume (by opening the lid or otherwise), it would wake up sometimes or it would just show me a blank screen (with the only option being a hard reboot). 

However I observed that if I disconnect the power supply before the suspend and then try to resume without AC power, it works! 

Has anybody had a problem like this? Is there a way to fix the suspend/wake up thing?

I was trying to locate a good frontend for the power management functions (like in the kde control center)... any suggestions?

Thx.

---

### Post by chele on 2006-02-16
[Gnome Power Manager]("http://www.gnome.org/projects/gnome-power-manager/packages.html")

Note the comments about changing the permissions of HAL to allow it to work on Ubuntu.

PS: What make and model of computer are you using?

---

### Post by TheDarkKnight on 2006-02-16
I'm using a dell inspiron 6000 with an ATI Radeon mobility 300 card. 

Well it turns out that the AC power off trick before suspending isn't foolproof after all. It failed once today. 
Though it certainly increases the chances of the laptop waking up after the suspend, it's not a permanent solution.

After I open the lid, the laptop attempts to wake up - I can see the numlock, capslock, bluetooth etc lights flashing and the power light goes from a slow blink (in suspend) to on but the screen remains blank.

Another (possibly) relevant piece of information -
After I try to start the computer after hibernating, it sometimes gives me a kernel panic at boot time... saying that I should boot with the acpi debug option. However, if I try again normally, it works.

Any idea what could be going wrong?

Thx.

---

### Post by anandrd on 2006-03-01
I am having a similar problem. My laptop (Inspiron 6000) wakes up successfully most of the time but sometimes it just gives a blank screen (the only way out being the hard reboot.) I haven't figured out anything yet. If you make any progress, let me know and so will I.

---

