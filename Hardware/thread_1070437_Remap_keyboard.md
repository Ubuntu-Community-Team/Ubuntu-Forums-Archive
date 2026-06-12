---
title: "Remap keyboard"
date: 2009-02-15
forum: Hardware
---

### Post by phoskito on 2009-02-15
Hi all,
The space key in my laptop is broken and I would like to remap the "windows logo key" to act as the space key. How can I do that?

Thanks a lot for your help!

---

### Post by utnubuuser on 2009-02-15
Nothing in System>>Preferences>>Keyboard?

---

### Post by phoskito on 2009-02-16
Thanks for your reply but there's nothing helpful in that menu. Any idea that I could try?

---

### Post by crazyfuturamanoob on 2009-02-16
Hello, today I feel very helpful.

[B]
Edit:
Here's a faster way, ignore all below and do this instead:

> xmodmap -e "keycode 133 = space"[/B]
[B]
Edit2:

You probably don't want to type that every time you log in, so type the command here:
> System->Preferences->Sessions->Add[/B]

Open up a terminal, type the following:
```

sudo cp /usr/share/xmodmap/xmodmap.xx /usr/share/xmodmap/xmodmap.xx-space
sudo gedit /usr/share/xmodmap/xmodmap.xx-space

```
Replace xmodmap.xx with the keyboard layout you use. (in my case, xmodmap.fi)

Then, add the following line in text editor:
```

keycode 133 = space

```
If there already is a line with number 133 (keycode for left windows key), then replace it.

And finally, close text editor and enable the new layout:
```

xmodmap /usr/share/xmodmap/xmodmap.xx-space

```

I even bothered testing it. Works for me.

---

### Post by phoskito on 2009-02-17
Thank you very much, it worked ok

---

