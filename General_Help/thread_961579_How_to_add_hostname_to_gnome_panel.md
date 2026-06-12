---
title: "How to add hostname to gnome panel?"
date: 2008-10-28
forum: General Help
---

### Post by mikehutn324 on 2008-10-28
How do I get the hostname to display in the gnome panel? is there an applet that will do this?

I switch through multiple windows using a kvm switch and i need to know what's a prod vs test server. this question was asked before but never answered. posters suggested adding the info to the kvm switch config but that's not the same.

thanks!

---

### Post by hictio on 2008-10-28
If you want it right besides the clock, do this:
Open the gconf-editor, type the keys:
```

Alt + F2

```

Then type inside the box:
```

gconf-editor (ENTER)

```

Goto, or expand the key:
'/apps/panel/applets/clock_screen0/prefs/custom_format'


Set it like this, or what ever you like it:
'tango - %a %d %b %H:%M' (without quotes)

On my case, 'tango' is the hostname of my box.

And then, set the format key to 'custom', it is below the 'custom_format' one.
There might be a why of doing this via the hostname command? Not sure, will try later.

Presto.

Used this as a base: [Cambiar aspecto del reloj en Ubuntu](http://120linux.com/aspecto-reloj-ubuntu/), it is in Spanish, tho.

---

### Post by hictio on 2008-10-28
A screenshot:

[url=http://xs.to/xs.php?h=xs232&d=08442&f=clock-name217.png]
[img]http://xs232.xs.to/xs232/08442/clock-name217.png.xs.jpg[/img]
[/url]

---

### Post by mikehutn324 on 2008-10-29
that's perfect! thanks so much

---

