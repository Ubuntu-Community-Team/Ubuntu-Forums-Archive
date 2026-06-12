---
title: "Assign Ubuntu and a cloud OS to different power buttons?"
date: 2010-05-27
forum: Hardware
---

### Post by Tobine on 2010-05-27
I have a HP Mini 5102 with Windows XP and naturally I want to replace it with Ubuntu. Normally this wouldn't be a problem except I really like the QuickWeb feature on this netbook and if I delete Windows I will lose it. QuickWeb is a fast-booting cloud OS that goes from powered-off to online in seconds. I really have no other use for Windows so I do not want to triple-boot. 

One of my favorite things about QuickWeb is that it uses one of the netbook's quick launch buttons to boot up rather than using the regular power button. This eliminates the inconvenience of selecting the OS from the grub menu. I can press 'power' for the desktop OS and 'internet' for the cloud OS.

What I would like to know is if anyone believes it is possible for me to dual-boot Ubuntu with a cloud OS (Chromium OS, Jolicloud, etc) and have each one assigned to a different power button like it is now? If so, do you have any ideas of how to do it or where to find more info?

If this can't be done I will have to install Ubuntu alone but it would be really cool if this was possible.

---

### Post by Defrector on 2010-05-27
[http://blogs.computerworld.com/14749/shh_hp_sneaks_linux_in_on_new_laptops]("http://blogs.computerworld.com/14749/shh_hp_sneaks_linux_in_on_new_laptops")

My instincts say that it is possible. According to this article, QuickWeb is actually linux-based to begin with. This means that its partition probably is recognizable on the hard drive by the ubuntu installer, which means if you tread carefully you can probably install ubuntu without bulldozing QuickWeb-but it's still possible to bulldoze QuickWeb if you're not careful.:P

How do you mean when you say that it needs windows?

---

### Post by Tobine on 2010-05-27
> **Defrector said:**
> How do you mean when you say that it needs windows?

It appears that quickweb is actually installed on Windows. There is a discussion [here ]("http://h30434.www3.hp.com/t5/Operating-systems-and-software/HP-mini-210-quickweb-install/td-p/212868")about reinstalling quickweb and about replacing windows with Ubuntu. Unfortunately it will not work without windows :(

What I'd like to know is if anyone knows if I can make these quick-launch buttons boot separate partitions. If HP can make each button boot separate OSes why can't I? Apparently the third button launches QuickLook, an email client, but I haven't tried this out yet.

---

