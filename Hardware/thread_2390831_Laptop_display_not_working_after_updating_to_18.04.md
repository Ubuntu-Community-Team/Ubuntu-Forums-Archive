---
title: "Laptop display not working after updating to 18.04"
date: 2018-05-03
forum: Hardware
---

### Post by svarogg on 2018-05-03
I was running Xubuntu 17.10 on a Lenovo Legion Y720, using nvidia display drivers.


  Everything worked great up until today that I updated to Xubuntu 18.04.


  Now the laptop's screen shows a small unblinking cursor, and that's it. External Displays still work perfectly well.

  The laptop's display isn't detected by xrandr or any similar program.


  Grub, Xubuntu's splash screen and when switching to TTY, however, are displayed on the laptop display.

I've tried using both nouveu and nvidia drivers, `prime-select nvidia` and `prime-select intel` - same thing happens.


  What could this be?

  
Thanks.

---

### Post by mörgæs on 2018-05-05
How does it work in a live boot of 18.04?

---

### Post by svarogg on 2018-05-06
> **mörgæs said:**
> How does it work in a live boot of 18.04?

Great suggestion! It actually seems to work.

I'll try to re-install 18.04 and let's see if it helps.

---

### Post by svarogg on 2018-05-09
So I re-installed Xubuntu, and now things work well... I guess solved, but would still be nice to understand the root cause of this issue.

---

### Post by mörgæs on 2018-05-11
Upgrades often wreck a system like you have just experienced. The process is so big that I'm surprised that it sometimes works. Finding out exactly what went wrong can be close to impossible. 

Just stick to fresh installs and you have a good foundation.

---

