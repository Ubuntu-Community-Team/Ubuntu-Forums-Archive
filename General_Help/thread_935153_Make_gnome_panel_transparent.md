---
title: "Make gnome panel transparent"
date: 2008-10-01
forum: General Help
---

### Post by k3kiaze on 2008-10-01
Hi,

I'm trying to get the gnome panel to be completely transparent with no lock. This dude seems to have do it. *[Check it out]("http://www.imgx.org/view/full/3874_8cprp")*

This is what happens if I right-click panel and set transparency to 100%, you can see parts of the panel. [IMG]http://img356.imageshack.us/img356/3785/panelrf6.jpg[/IMG]

---

### Post by Therion on 2008-10-01
Try a different theme and see if the problem persists.

---

### Post by steveneddy on 2008-10-01
## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent

---

### Post by damis648 on 2008-10-01
> **steveneddy said:**
> ## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent

+1, but I would use name=gnome-panel instead of type=dock just because if you ever decide to use some sort of Dock like awn, it will also make that transparent.

---

### Post by steveneddy on 2008-10-01
True, but i don't use awn and I put those directions in a file before awn was as commonplace as it is today. Awn may not have even existed at this time.

Actually, these particular directions come from the Beryl days.

---

### Post by k3kiaze on 2008-10-01
awesome, it worked (but only after restart).

However the icons also become transparent. If you click the link in the first post you'll see that the icons on the panel are not affected.

Update: 
When I used **type=dock** and **name=gnome-panel**, it also affected my main menu (i.e the menu like startmenu in Windows). So everything was transparent in the dock. I then used **type=dock & name=gnome-panel** now the main menu is not affected anymore only the panel and the icons on it.

---

### Post by marko_4454 on 2009-01-25
> **k3kiaze said:**
> awesome, it worked (but only after restart).

However the icons also become transparent. If you click the link in the first post you'll see that the icons on the panel are not affected.

Update: 
When I used **type=dock** and **name=gnome-panel**, it also affected my main menu (i.e the menu like startmenu in Windows). So everything was transparent in the dock. I then used **type=dock & name=gnome-panel** now the main menu is not affected anymore only the panel and the icons on it.

Did you ever get the icons to be unaffected while the bar is completely transparent? I am also having this problem. Please let me know if you were able to do so. 
Thanks!

---

### Post by Arabso on 2009-01-25
Thanks a lot
its very great 
thanks for all

---

### Post by Magical Tiger on 2009-09-23
Sorry for the late post, but this is the only thing that has worked so far. But how do you make it so that the icons and text are not transparent?

---

### Post by Alvarodt on 2009-11-29
Do anyone know the answer? thank you.

---

### Post by Magical Tiger on 2009-11-29
In order to make the bar transparent you just right click on it and select "Properties". Under the background tab, select solid color and adjust the transparency with the slider. To get the panels transparent though, I dont know.

---

### Post by Alvarodt on 2009-11-29
We want all the taskbark transparent, like this:
[http://img155.imageshack.us/img155/3958/screenshoton9.png](http://img155.imageshack.us/img155/3958/screenshoton9.png)

I found it on google so forget the arrow.

Problem is that if we use compiz fusion we have also the icons transparent, we want only the taskbar (all of it).

---

### Post by Magical Tiger on 2009-11-29
Do you want the applications transparent like the picture is pointing at or just the bar?

---

### Post by Alvarodt on 2009-11-29
Just the bar, not the icons, not anything

---

### Post by Magical Tiger on 2009-11-29
Have you tried what I said? It should work.

---

### Post by Alvarodt on 2009-11-30
Yes, but I only have half the bar transparent. For example where you can read "Applications   Places   System" ... is not transparent and there is no way with your solution.

---

### Post by Magical Tiger on 2009-11-30
Ok, I know what the problem is. Im geussing you are not using one of the default themes that come with the installer and that you added one from the internet somewhere. Your current theme doesn't supply some needed graphics or something so it doesn't support becoming transparent. The only way to fix it that I can think of is to either email the maker of the theme to fix it or fix it yourself. I have no experience with theme making so I cant help you there.

---

### Post by Alvarodt on 2009-11-30
You were right, It was because of the theme... Thank you!

---

### Post by Magical Tiger on 2009-11-30
No problem.

---

