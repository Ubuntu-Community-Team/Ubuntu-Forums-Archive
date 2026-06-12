---
title: "Question about beryl 3d cube"
date: 2008-10-16
forum: General Help
---

### Post by George7a on 2008-10-16
Hi,

Thanks to you guys I have enabled the cube and it is running and moving just great!

I have some questions:

1) I have seen some videos in youtube and in them the windows on the desktop appeared also in 3d when the cube was rolling. the seemed to be a bit far from the desktop, like poping out of the screen. How do i do that? 

2) In my cube all the 4 desktops have the same background and the same shortcuts. I would like to have a unique desktop in each side of the cube, with a different BG and shortcuts. How can I do that?

Thanks in advance.

- George

P.S. I have upgraded to 8.04 yesterday (I had 7.10)

---

### Post by isparkes on 2008-10-16
Make sure that you have the "Advanced Desktop Effects Settings" available under System -> Preferences.

You can get this by doing (in a terminal)

sudo apt-get install compizconfig-settings-manager

or through Synaptic.

---

### Post by Elfy on 2008-10-16
Not sure about the different windows but to get 3d desktop in Effects enable 3d desktop, you can change the space in the misc options of that effect.

You need the compiz config installed

```
sudo apt-get install compizconfig-settings-manager
```

Run it with ```
ccsm
```

---

### Post by philinux on 2008-10-16
Under the advanced desktop effects menu.

Enable 3D windows, top left tick box. So many choices. LOL

---

### Post by George7a on 2008-10-16
Thanks guys,

The 3d desktop effect is already enabled and compizconfig-settings-manager is already installed.

Philinux, thanks, That is what I meant for the 3d windows, I will try it.

The other question is how to make the 4 desktops, that I already have in my cube, unique? I would like to set a different background & shortcuts for each desktop. Now when I add a shortcut to a desktop it is added to allt the 4. I want to have different shortcuts on each side of the cube.

- George

---

### Post by philinux on 2008-10-16
You can have a different wallpaper on each cube face but the downside is you can't have any icons on the desktop. And you have to hack gnome.
One discussion of many.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=482505](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=482505)

---

### Post by overdrank on 2008-10-16
Moved to Desktop Effects & Customization :)

---

### Post by George7a on 2008-10-16
> **overdrank said:**
> Moved to Desktop Effects & Customization :)
I thought I am still a beginner, and now I need to hack into GNOME!

---

### Post by lametike on 2008-10-16
about this , iwant to ask where can i get the desktop cube plugin??

---

### Post by Kevbert on 2008-10-16
You need to install CCSM which you can get via Applications-Add/Remove.  What version of Ubuntu are you using ?
What's the graphics card ?  You can get this by going to Applications-Accessories-Terminal and entering
```
lspci
```
If the graphics card is Intel, ATI or Nvidia chances are you can use Compiz to get a 3d cube. If not, then the card is not supported and you're out of luck.

---

### Post by unoodles on 2008-10-16
I don't think you have to hack GNOME. AFAIK the next version of ubuntu (8.10) will have a compiz plugin that will manage desktop wallpapers. I have the 8.10 Intrepid beta running in a virtual machine, and there *is* a wallpaper plugin, but I have not tried using it.

---

### Post by George7a on 2008-10-16
> **unoodles said:**
> I don't think you have to hack GNOME. AFAIK the next version of ubuntu (8.10) will have a compiz plugin that will manage desktop wallpapers. I have the 8.10 Intrepid beta running in a virtual machine, and there *is* a wallpaper plugin, but I have not tried using it.
So in 8.10 I can have 4 different desktops with 4 different wallpapers and 4 different groups of shortcuts?

As I understood it won't be available in 8.04, right?

---

### Post by Kevbert on 2008-10-16
Just tried the wallpaper plugin on Intrepid Beta. With the desktop sphere I don't see multiple wallpapers or multiple wallpapers on the screen (for each desktop).  Maybe it's not fully implemented yet, or I'm doing something wrong. I've addedf 6 new wallpapers but not sure about what to do with the colour settings.

---

### Post by Kevbert on 2008-10-17
> **George7a said:**
> So in 8.10 I can have 4 different desktops with 4 different wallpapers and 4 different groups of shortcuts?

As I understood it won't be available in 8.04, right?

Have a look at [[COLOR="Red"]wallpapoz[/COLOR]]("http://wallpapoz.akbarhome.com/download.html")

---

