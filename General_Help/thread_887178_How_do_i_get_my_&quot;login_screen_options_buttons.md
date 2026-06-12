---
title: "How do i get my &quot;login screen options buttons&quot; back?"
date: 2008-08-11
forum: General Help
---

### Post by NZJon on 2008-08-11
Hi there,

I have Hardy installed on my AMD64 box, and recently tried out the KDE4.1 release, to have a look at it. I decided that KDE wasn't for me (right now, maybe some other time...) and switched back to GNOME.

However, on my "login screen", where I used to have the "options" button, and server name and date/time, these are now missing. This is what I used to have on my login screen:

[http://commons.wikimedia.org/wiki/Image:Ubuntu_8.04_login_screen.png](http://commons.wikimedia.org/wiki/Image:Ubuntu_8.04_login_screen.png)

Does anyone know how I get these back? I'm hoping there's a simple configuration option that I have missed.

Many thanks,

  Jon

---

### Post by tuxxy on 2008-08-11
system > admin > login window?

---

### Post by jerome1232 on 2008-08-11
what are you getting currently? Is it the KDE manager?
F10 usually brings up a menu that has all the options (some greeter just don't have a button to push to get it)

If you just have KDM loading up by default you should be able to run this command to get GDM back

```
sudo dpkg-reconfigure gdm
```

---

### Post by NZJon on 2008-08-13
Many thanks to tuxxy and jerome1232 for your suggestions.

Jerome1232 -- I should indeed have mentioned what I am seeing! I am seeing the GNOME Human Ubuntu Default Welcome Theme, just without the "options" panel at the bottom.

Tuxxy -- I have looked through the System > Admin > Login Window options, and the closest I've found that might have something to do with my problem on the "Local" tab. There I see the "Menu Bar" options:

```

[ ] Show Actions menu
    [ ] Include Hostname Choose (XDMCP) menu item
```

Even if I have these enabled or disabled, I do not get the "options" panel (probably really called the "menu bar"). So I'm still stumped.

Thanks for your suggestions though.

   Jon

---

