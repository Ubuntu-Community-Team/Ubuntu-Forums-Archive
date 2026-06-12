---
title: "using special laptop buttons &quot;back&quot; and &quot;ok&quot; to switch workspaces"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Crypty on 2007-10-24
Hi, my laptop has 2 small buttons, one is "back" and one is "ok" I want to use these to switch workspaces wither by just pressing 1 to go back and forth or having 1 button go to the left workspace and one to the right. The problem i'm having is that ubuntu seems to recognize the "back" button the same key as backspace, and the "ok" button as another return key. 

Is there any way I can get it to recognize these keys independently so I can map them to actions in compiz?

---

### Post by kebes on 2007-10-24
First thing to do is run a little program called "xev"... this program opens a small window, which will show the keycode for any key you press. Then you can press those keys and take note of what the number was.

If the "back" button generates the exact same keycode as the "backspace" key, then there's nothing you can do: the two keys are identical at a hardware level,  and there's no way for Ubuntu to know the difference between which one you pressed.

But normally the "special keys" will generate keycodes that are unique. You can then use those keycodes to activate whatever functionality you want. To do this, you write a little script (that gets run on startup) which maps those keycodes somehow. The easiest way to do this is to map the special keys to the "higher function keys" (your keyboard probably has F1 to F12 ... but there are also function keys that go higher, but just are not on the keyboard...).


For example, if the special key had keycode "234" you could have a script like:
```
#!/bin/bash
xmodmap -e 'keycode 234=F20'
```

So that now that special key is basically the 'F20' key. The reason to do this is that now you can create a menu item that runs whatever command you want, and assign it the shortcut key 'F20', so when you press that key, the command gets run automatically.


This may seem like a roundabout way to get it all to work... and in fact maybe there is a simpler way that I'm not aware of. But I used the above tricks to map all of my special keyboard keys to allow me to launch various programs, activate shortcuts, etc.

Hope that helps.

---

### Post by Crypty on 2007-10-24
Thanks I got the OK button working to switch workspaces. The "back" button seems to have the same keycode as backspace though, so I guess that one truly is the same as my backspace key. Oh well.

---

