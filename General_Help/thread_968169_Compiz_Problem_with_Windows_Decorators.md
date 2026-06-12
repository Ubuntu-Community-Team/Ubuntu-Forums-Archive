---
title: "Compiz Problem with Windows Decorators"
date: 2008-11-02
forum: General Help
---

### Post by ninboy on 2008-11-02
Hello everyone!

I have some problem with Compiz... I just installed ubuntu 8.10 in a fresh install. Well, the first thing I did was uninstall all the compiz crap that comes by default, because my graphic card is not so good.

Anyway, I installed the ATI drivers, and everything is great now. I tried to install compiz again, and everything whent smoothly. I installed the packages:
```
sudo apt-get install compiz compizconfig-settings-manager simple-ccsm
```All the Compiz packages are in my system now. I activate compiz and everything is fine, but one thing. The windows borders! It seems that compiz is overwriting my windows borders and put some ugly thing... I use the nice new DarkRoom, but with compiz, the window decorations aren't the ones with the theme. No matter what theme I select, I always have the same orange-window decorator... The only way to get my the theme's default was disabling compiz...

Can someone tell me how I make that compiz use my theme windows borders?
Here's my programs...

---

### Post by tuxxy on 2008-11-02
It seems like your using Emerald for the borders maybe? you could try disabling it or run this command should return them to normal

```
metacity --replace
```

---

### Post by ninboy on 2008-11-02
> **tuxxy said:**
> It seems like your using Emerald for the borders maybe? you could try disabling it or run this command should return them to normal

```
metacity --replace
```

Actually, I've installed emerld when i installed Compiz, but then I uninstalled it. I've also remove .emerald folder in my home. When I use that, actually it makes Compiz disable...

---

### Post by GrandpaLeaman on 2008-11-02
Did you install the Compiz Fusion Icon?

```
sudo apt-get install fusion-icon
```Then find Compiz Fusion Icon in your menus. I believe it will be in the "System Tools" menu. When you start the icon, it will show up in the notification area. All you need to do is right click on the icon, chose "Select Window Decorator" and change the setting to GTK Window Decorator.

If you want the icon to show up in the notification area at startup, place it in your "Sessions". I believe fusion-icon is in the /usr/bin folder.

Hope this proves helpful.

---

