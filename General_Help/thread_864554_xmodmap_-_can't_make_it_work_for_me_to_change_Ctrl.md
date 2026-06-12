---
title: "xmodmap - can't make it work for me to change Ctrl+Alt+Backspace to something else"
date: 2008-07-19
forum: General Help
---

### Post by Marinski on 2008-07-19
Hello!
Here is my situation: I use two keyboard layouts, which I switch with Alt+Shift (old Windows habit). The thing is that I very often type something with the wrong layout and after that try to delete it with Ctrl+Backspace, cause it deletes whole words back - faster. And when pressing Alt+shift and Ctrl+Backspace in quick succession I kill my X server because of the Alt+Ctrl+Backspace shortcut.
So what I want is NOT to disable the shortcut, but to remap it to i.e. Ctrl+Alt+End. I did some googling and found about xmodmap, I tried to change the mappings, tried creating an ~/.Xmodmap file with the needed lines, but none would do what I want. 

The standard output when I type xmodmap -pke is:
keycode  22 = Backspace Terminate_Server
keycode 103 = End

I tried to put this in ~/.Xmodmap
keycode  22 = Backspace
keycode 103 = End Terminate_Server

After rebooting I was able to see, that the changes had been applied via xmodpam -pke, but anyway, Ctrl+Alt+Backspace still killed my X, While Ctrl+Alt+End didn't do anything.

What am I doing wrong? Any suggestions?

---

### Post by erginemr on 2008-07-19
I doubt you can do combos with Xmodmap. You will need something else, xmacro or xbindkeys maybe:
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)
Both are available in the repositories for you to try.

However, Ctrl+Alt+BackSpace may have been hardcoded to the X server.

---

