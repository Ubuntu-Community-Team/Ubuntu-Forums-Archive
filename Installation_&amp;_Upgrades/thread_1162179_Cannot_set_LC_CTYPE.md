---
title: "Cannot set LC_CTYPE"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by AlanPo on 2009-05-17
Hello.
I should ask for help as I did find explanation only here in Italian
[http://forum.ubuntu-it.org/index.php?topic=24463.0](http://forum.ubuntu-it.org/index.php?topic=24463.0)
so I do not understand.

I have problem with language support.  I need to enable writing in latvian and russian so I installed those languages with system/administration/Language support. But it changed all menus, all programs to russian, after to latvian!!!
believe me, I do not know russian that well to see all programs here in russian. Change back to english is not possible without uninstall.

so I did uninstall those languages the same way. ended up with that in locale:
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=lv_LV.UTF-8
LANGUAGE=lv_LV:lv:en_GB:en
LC_CTYPE="lv_LV.UTF-8"
LC_NUMERIC="lv_LV.UTF-8"
LC_TIME="lv_LV.UTF-8"
LC_COLLATE="lv_LV.UTF-8"
LC_MONETARY="lv_LV.UTF-8"
LC_MESSAGES="lv_LV.UTF-8"
LC_PAPER="lv_LV.UTF-8"
LC_NAME="lv_LV.UTF-8"
LC_ADDRESS="lv_LV.UTF-8"
LC_TELEPHONE="lv_LV.UTF-8"
LC_MEASUREMENT="lv_LV.UTF-8"
LC_IDENTIFICATION="lv_LV.UTF-8"
LC_ALL=

so question is - how to correct locale to be able to write in at least latvian and understand all menus?

9.04 jaunty
Gnome 2.26.1
kernel 2.6.28-12

---

### Post by BattousaiX on 2009-05-30
Try this.

[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

