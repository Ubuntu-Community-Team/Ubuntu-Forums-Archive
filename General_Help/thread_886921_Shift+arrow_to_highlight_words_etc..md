---
title: "Shift+arrow to highlight words etc."
date: 2008-08-11
forum: General Help
---

### Post by tsphere on 2008-08-11
Hi,

Ironically, one of the things I found most difficult in ubuntu is that keyboard shortcuts which I used in that other os, don't work.
It's ironic because linux is more computer-geek-hardcore, and the increased dependency on the mouse is annoying...

Most frustrating for me is that shift+arrow to highlight doesn't work. So I always have to use the mouse, which is very annoying.
shift+home, shift+pg up/dn, shift+end work great, but shift+arrows don't work.

I tried enabling it in keyboard shortcuts, but I have a laptop with no numeric keypad (only arrow keys), and it doesn't work.

Thanks,
Eyal

---

### Post by pauper on 2008-08-11
Well, be more specific.

To my knowledge Shift and Arrow keys highlight text in Firefox, gedit, gVim,
oowriter, tomboy, gnome-dictionary, even gcalctool, which are part of Ubuntu
environment, don't you agree?

They don't work the way you expect in bash. echo, cat, cut, grep, awk, sed,
head, tail... will neatly redirect output to a file.
 
"xclip" or "xsel" will save it to its buffers:

```
sudo apt-get install xclip
lsmod | xclip
xclip /proc/modules
```

Middle-click (Shift-Insert or Ctrl-v for clipboard) in gedit and there it is.

Look into "xautomation" utility as well:

[http://hoopajoo.net/projects/xautomation.html](http://hoopajoo.net/projects/xautomation.html)

> **tsphere said:**
> It's ironic because linux is more computer-geek-hardcore, and the
increased dependency on the mouse is annoying...

It's highly unlikely to have GUI and not to be mouse-oriented. Text console is
always there for your needs. Fire up "screen" utility and live happy ever after
without any mouse gestures.

Some interesting reading:
[http://www.jwz.org/doc/x-cut-and-paste.html](http://www.jwz.org/doc/x-cut-and-paste.html)

---

### Post by tsphere on 2008-08-12
Thanks, however the shift+arrow keys don't work for me in firefox, or any other program.
But, not to worry, I found ctrl+shift+arrow, which does basically the same thing only it highlights only full words. If anyone knows how to get that simple shift+arrow functionality, That would be great.

---

