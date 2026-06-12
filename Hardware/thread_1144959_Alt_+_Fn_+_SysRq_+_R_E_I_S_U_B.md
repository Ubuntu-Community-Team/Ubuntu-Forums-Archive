---
title: "Alt + Fn + SysRq + R E I S U B"
date: 2009-05-01
forum: Hardware
---

### Post by arkashkin on 2009-05-01
Hello.
I have run already 4 versions of Ubuntu until now, and now i'm using Junty.
My laptop is - Dell latitude D600 old laptop.
My "SysRq" key is combined with "Prnt Scrn", and i have a "Fn" key to switch between them.
The key combination - _Alt + Fn + SysRq + R E I S U B_ never works for me.

I folowed this post:
[http://ubuntuforums.org/showthread.php?t=726783](http://ubuntuforums.org/showthread.php?t=726783)
and i have the same results:

I have tried :
```

$ cat /proc/sys/kernel/sysrq
1
```

and :

```

$ grep MAGIC_SYSRQ /boot/config-$(uname -r)
CONFIG_MAGIC_SYSRQ=y
```

Instead of a system reboot i get whole lot of 'Save screenshot' dialogs...

Please help...

---

### Post by Patsoe on 2010-05-30
I realise this is a very old post, but thought I might help others ending up here from their search engine (this was the top result for "ubuntu sysrq laptop fn" in duckduckgo):

I got the same screenshot dialogues as yours when using the left Alt key, but using the right Alt key gave me the expected SysRq action. I am using an "AltGr dead-keys" locale setting, not sure if that's relevant.

edit: One more thing... after doing what I needed to do in the console, and getting back to X, I found that the keyboard remained in the mode that Alt+Fn+SysRq+r results in. This is annoying because that means many Alt-key combinations (like Alt-left in Firefox) throw you back to a console. The [solution]("http://www.blino.org/notes/tech/linux/keyboard-raw.html") for me was to set "sudo kbd_mode -s".

---

