---
title: "[SOLVED] Wine (last version) Office 2003 Installation Bug"
date: 2008-08-13
forum: General Help
---

### Post by null byte on 2008-08-13
Well, I tried to install Office 2003 in Wine. But seems that I encounter the following bug:

[http://bugs.winehq.org/show_bug.cgi?id=13139](http://bugs.winehq.org/show_bug.cgi?id=13139)

even if the guys at wine say on their main page it is fixed.

**            [EMAIL="truiken@gmail.com"]James Hawkins[/EMAIL]** posted a patch, but I don't know what to do with it...

Any help about this issue?

Thanks in advance :)

**PS**: Don't tell me to virtualize, use OpenOffice or other software, I need Office 2003.

---

### Post by null byte on 2008-08-13
Okay, fixed. Everybody that has this problem, backup your .wine directory and:
```

rm -rf ~/.wine
winecfg

```

Worked for me :)
[SIZE=3][COLOR=#909090] [/COLOR][/SIZE]

---

