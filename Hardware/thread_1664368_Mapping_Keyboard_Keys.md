---
title: "Mapping Keyboard Keys"
date: 2011-01-10
forum: Hardware
---

### Post by decrow06 on 2011-01-10
Hello,

I recently got a new Dell XPS 15.  It is working well with Ubuntu 64-bit.  However, the keyboard has a variety of default XF86 settings.  I like many of them, such as those that control my media player.  However, the F2 button is set to toggle my wireless device on and off.  This is highly irritating since Alt+F2 no longer launches 'Run' and F2 no longer allows me to rename files.  

Running 'xev' and pressing F2 i obtain the following:


```

KeyRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x15d, subw 0x0, time 20589018, (171,-18), root:(179,542),
    state 0x0, keycode 246 (keysym 0x1008ff95, XF86WLAN), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```

I tried running the command:

```

xmodmap -e "keycode 246 = F2"

```

but nothing happened.  Help, please.

Thanks in advance.

---

### Post by pi/roman on 2011-01-10
See what this gives you.
```
xmodmap -pke | grep -i f2
```

---

### Post by decrow06 on 2011-01-10
```

xmodmap -pke | grep -i f2
keycode  68 = F2 XF86_Switch_VT_2 F2 XF86_Switch_VT_2

```

---

### Post by decrow06 on 2011-01-11
bump...

anything?

---

### Post by decrow06 on 2011-01-11
Update: I tried the following:

```

xmodmap -pke > .xmodmap.rc

```

and I changed the relevant line about keycode 246.  When I restarted X, it asked me to load the file, and I did.  This still did not work.

---

### Post by pi/roman on 2011-01-12
If F2 is registered to a keycode of 68 and pressing F2 gives you a keycode of 246 then something strange is happening. Maybe you have a modifier key stuck.

---

### Post by decrow06 on 2011-01-12
I don't think I have a modifier key stuck.  The logo on the F2 key is a wireless antenna, and Ubuntu auto-detected my keyboard and assigned the F2 key to XF86WLAN.  I don't know how it automatically assigned keycode 68 to F2, but I am pretty sure it's not a stuck modifier.

---

### Post by decrow06 on 2011-01-13
See this thread.

[http://ubuntuforums.org/showthread.php?p=10353537#post10353537](http://ubuntuforums.org/showthread.php?p=10353537#post10353537)

It solved my problem.

---

