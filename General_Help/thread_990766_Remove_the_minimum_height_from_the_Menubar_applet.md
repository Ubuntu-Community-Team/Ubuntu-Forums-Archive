---
title: "Remove the minimum height from the Menubar applet"
date: 2008-11-23
forum: General Help
---

### Post by ChrisBookwood on 2008-11-23
Hi,

I have been doing some changes on my laptops desktop, to make more space - smaller font size.
Now I have come to the conclusion, that I want a gnome panel with the height of 21. The things is, though, I use the applet Menubar, which I'm heavily fond of, but it seems to have a minimum height of 24, so even though I change the panels height to 21, when the Menubar is applied, the height becomes 24, even though it says it is 21 in height.

Can you give me a hint to how I remove that minimum height parametre?

I have been looking around for myself, but I haven't been able to find anything, i'm afraid.
... I hope you guys can.


Regards,
Chris Bookwood

---

### Post by loomsen on 2008-11-23
```
sudo apt-get install gnome-color-chooser
```

[[img]http://www.ubuntu-pics.de/thumb/6244/screenshot_02_8gGvEJ.png[/img]](http://www.ubuntu-pics.de/bild/6244/screenshot_02_8gGvEJ.png)

:)

---

### Post by ChrisBookwood on 2008-11-23
> **loomsen said:**
> ```
sudo apt-get install gnome-color-chooser
```[[IMG]http://www.ubuntu-pics.de/thumb/6244/screenshot_02_8gGvEJ.png[/IMG]]("http://www.ubuntu-pics.de/bild/6244/screenshot_02_8gGvEJ.png")

:)

It doesn't seem to be changing the size of the actual ubuntu logo, left for the Applications, Places and System text.
Great app, though!

---

### Post by loomsen on 2008-11-23
Did you log out and back in? You might have noticed, due to the gnome-panel being a required component, it is run with --sm-disable, so no session management options for gnome-panel. You gotta workaround that, it should resize your icons then actually.

For instance, drop to a shell, Alt+Ctrl+F1, and make a gz out of the binary, 
```

sudo /etc/init.d/gdm stop
sudo gzip /usr/bin/gnome-panel

```

Log back in (or edit the respective file), commit your changes, 
```
sudo /etc/init.d/gdm start

```

When you're done setting up the panel, extract it again with:
```

sudo gunzip /usr/bin/gnome-panel.gz

```

and you should be fine :)

---

### Post by ChrisBookwood on 2008-11-23
I'm not sure I understand that method and why it would work ... Can you explain it to me, please?

---

### Post by loomsen on 2008-11-23
Sure.

There's this key in gconf, you might have noticed (assuming you're running Intrepid), called required components.

This causes the gnome-panel to be run with --sm-disable (sm=Session Management)

This actually means that gnome won't get/store settings through the settings-daemon, like any other apps would, but stores them by itself. Further you'll prlly not be able to end gnome-panel anyhow, cause it will get restarted instantly.That's what that key does, it takes care you don't delete the panel by mistake or so.

If you pack it tho, you can just leave it where it is, but you actually made it inexecutable, for this moment. Otherwise you won't be able to get this done, cause gnome will always have it's gnome-panel running and restarting. I guess if you just remove it from where it is you'll pretty likely get some error at login time, cause of that. If you make a gzip out of it, it just get's noticed, but not executed :) And you'll still be able to log in. Got me? Quite l8 in germany :)

---

### Post by ChrisBookwood on 2008-11-23
Yeah okay... So you want me to go to shell, do a gzip /usr/bin/gnome-panel, so I now have gnome-panel.gzip in /usr/bin/, but no gnome-panel.
Now what to do? I don't get how I apply the changes (what changes?) before i gunzip the file again?

---

### Post by loomsen on 2008-11-23
Yes, open gnome-color-chooser, set icons to your desired size, logout/drop to shell again, gunzip gnome-panel.

That way is, at least I assume it is, the only way gnome-panel won't be able to fight back. :)

But, actually, 
> So you want me to go to shell
I don't want you to, you wan't you to :)

You don't like the shell? My app no 1, would be totally lost without.

---

### Post by ChrisBookwood on 2008-11-23
It didn't work, I'm afraid...
As before, it was only the icons in the dropdown-list that changed size.

---

### Post by ChrisBookwood on 2008-11-23
Any ideas?

---

### Post by ChrisBookwood on 2008-11-24
No ideas at all?

---

### Post by loomsen on 2008-11-24
So, I got you right, you just wanna have a somewhat bigger MainMenu icon, right? 

Create a Desktoplauncher, Alt+F1 triggers the Main Menu, right where your cursor actually is. Or, get cairo dock, 1.6.3.1 has a quite nice Main Menu applet implemented.

I think I'll even find an old script for cairo to create a generic menu, structured in subdocks.

Other than that... Humm. lxpanel? give it a try, didn't use it yet.

---

### Post by ChrisBookwood on 2008-11-24
No, that the wrong way ... I wan't to make Mainmenu appletten possible to be on a panel with height of 21... As of now, it doesn't seem to be possible, since Mainmenu appletten has an min-height of 24...
I don't know if the easiest thing would be to change the min-height of Mainmenu appletten, or switch to a whole other menu-applet.

...You also mention the icon height... I don't care about that, really. I just want my panel to have a height of 21.

---

### Post by loomsen on 2008-11-24
You can hack it if it's that.

```
sudo nano /usr/share/idl/gnome-panel-2.0/GNOME_Panel.idl
```

[[img]http://www.ubuntu-pics.de/thumb/6296/screenshot_04_7686cF.png[/img]](http://www.ubuntu-pics.de/bild/6296/screenshot_04_7686cF.png)

---

### Post by ChrisBookwood on 2008-11-25
Such a file doesn't exist on my system, I'm afraid...

---

