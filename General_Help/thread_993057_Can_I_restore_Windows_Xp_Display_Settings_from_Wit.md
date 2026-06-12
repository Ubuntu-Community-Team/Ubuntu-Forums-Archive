---
title: "Can I restore Windows Xp Display Settings from Within Ubuntu?"
date: 2008-11-25
forum: General Help
---

### Post by MarkM941 on 2008-11-25
Well I screwed up my Windows display settings so now I can't boot into Windows. And when I boot into safe mode neither my mouse nor my keyboard work. So can I boot into my Ubuntu installation and restore the display from there?

---

### Post by eder.apt-get on 2008-11-25
I´m afraid not, because XP doesn´t have "conf" files, like xorg or something.
I would remove the video card adapter (Control Panel/Device Manager) and reinstall it. Of course, you gonna have to reboot sometime...:)

---

### Post by Achetar on 2008-11-25
no. not unless you feel like sifting through MBs of hex to find the registry entry and change it.

or you might be able to make a .bat file that will do it (I don't know how) and put it in C:\Documents and Settings\All Users\Startup

---

### Post by prshah on 2008-11-25
> **MarkM941 said:**
> Well I screwed up my Windows display settings so now I can't boot into Windows. And when I boot into safe mode neither my mouse nor my keyboard work. So can I boot into my Ubuntu installation and restore the display from there?

You can do this in two ways: One from within Ubuntu, and the other directly after XP selection in GRUB (Recommended):

*Recommended* 1) Immediately after selecting the Windows option in GRUB, keep tapping F8 to get the startup options menu.

== OR ==

2) From Ubuntu (installed or liveCD), edit the MSDOS.SYS file in your Windows partition, and add the below line to the [Options] section:
```

BootMenu=1

```

(if there is no [options] section or if the msdos.sys file is blank, then use
```

[Options]
BootMenu=1

```

Now, when you boot Windows, the startup options menu will appear automatically, without the need to tap F8.

==

Then, from the boot menu, choose the "Enable VGA mode" option. Then let windows boot normally; Once it's booted up, it will prompt you to change the video settings.

---

