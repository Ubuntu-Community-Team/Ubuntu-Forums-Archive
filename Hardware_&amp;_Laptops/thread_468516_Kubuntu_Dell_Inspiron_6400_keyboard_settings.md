---
title: "Kubuntu: Dell Inspiron 6400 keyboard settings"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by Neuralgia on 2007-06-08
I just realized, that when I use Kubuntu, my laptop (Dell Inspiron 6400) doesn't recognize my SHIFT keys (left or Right).

I tried to use the Keyboard Settings inside the System Settings, setting the kbrd as "Laptop/Notebook Dell Inspiron 6xxx/8xxx" inside the Regional & Language Settings.

any ideas?

---

### Post by Merritt.kr on 2007-06-09
That's odd... I have a 6400 as well. My keyboard works just dandy... and I didn't do anything special to get it working. 'fraid I don't know why yours is not. :(

---

### Post by neptho on 2007-06-09
I use Gnome, so I can't help about device specific button functionality, but you can always install and use xbindkeys to bind your buttons to do various things.  Here's what I used when I was running Debian with XCFE:

Remember to add xbindkeys to your startup session if you go this route, or you'll have to run it manually when KDE loads.

```
%cat ~/.xbindkeysrc 
"audacious --play-pause"
  m:0x0 + c:162 
  XF86AudioPlay 
"audacious --stop" 
  m:0x0 + c:164 
  XF86AudioStop 
"audacious --rew" 
  m:0x0 + c:144 
  XF86AudioPrev 
"audacious --fwd" 
  m:0x0 + c:153 
  XF86AudioNext 
```

---

### Post by Neuralgia on 2007-06-09
it's something related to KDE, cause GNOME has no problems... not even WOS

---

### Post by neptho on 2007-06-09
Then I'd suggest using xbindkeys, as noted above.; it'll make things work and you won't have to worry about it.  ;)

---

