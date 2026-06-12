---
title: "new to ubuntu"
date: 2008-08-01
forum: General Help
---

### Post by drakoumel on 2008-08-01
hello i am fairly new to ubuntu working on it for some weeks or so .. can anyone tell me how to change the skins ?
also how to put the bar on the bottom of the screen in this pick :
[http://thegrayson.deviantart.com/art/My-Ubuntu-Linux-Desktop-89135654](http://thegrayson.deviantart.com/art/My-Ubuntu-Linux-Desktop-89135654)
thnx

---

### Post by chris4585 on 2008-08-01
> **drakoumel said:**
> hello i am fairly new to ubuntu working on it for some weeks or so .. can anyone tell me how to change the skins ?
also how to put the bar on the bottom of the screen in this pick :
[http://thegrayson.deviantart.com/art/My-Ubuntu-Linux-Desktop-89135654](http://thegrayson.deviantart.com/art/My-Ubuntu-Linux-Desktop-89135654)
thnx

welcome to ubuntu to start off.  changing 'skins' more commonly known as changing themes are pretty easy, head on over to [http://gnome-look.org]("http://gnome-look.org") and on the side look for gtk2+, find one you like, save it, and then right click on  your desktop click on change background, go to the theme tab, and drop the .taz.gz or other archived file into the dialog box, or you can install it by hitting the install button, and selecting the archived file, for more customization features hit customize

metacity = the windows manager theme
GDM = login theme
icons = self explanitory

The metacity, icons and gtk themes can be installed by the same way as i explained above.  GDM can be installed by going to system > admin > login window then go to the local tab.


The bar in the pic is called a dock and that dock is probably awn, you can install awn by opening applications > accessories > terminal and type in

```
sudo apt-get install avant-window-navigator awn-manager
```

I dont thinik it comes a lot of applets though, you can look up how to install awn with all the applets on google probably, good luck

edit: I almost forgot you need compositing turned on for awn to work, if you have compiz on it should work, to turn compositing on I'm actually not sure, never done it besides just used compiz

---

### Post by em4g.3ht on 2008-08-01
don't forget emerald theme manager ;)

i believe you can get it by searching for emerald in the synaptic package manager.

also if you want to get really into it you can change your splash screens and usplash themes!! (it's a little more complicated that dragging and dropping into the apperance preferances)

gnome-look.org is a good place to start looking for themes, if you didn't know already. And most of the downloads have simple guides that make installing the new eye candy a breeze! :)

---

