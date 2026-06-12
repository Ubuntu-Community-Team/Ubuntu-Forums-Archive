---
title: "Effects"
date: 2008-07-27
forum: General Help
---

### Post by shane786 on 2008-07-27
Hi,

I can't change any of my effects. I want the cube and everything and i just don't know how to access this stuff. I know how to change visual effects but i don't know if they have a compiz thing for gnome.

I don't know anything about this stuff. can someone make it simple for me?

thanks

---

### Post by Troll_the_Great on 2008-07-27
First, did you installed compiz?If not, install it via Synaptic.
Then open a terminal and type:
```
sudo apt-get install compizconfig-settings-manager
```
Then go to System-Preferences-Advance Desktop Effects Settings and configure it from there.
Have a look at this link for more help.
[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)
Hope this helps.
Cheers!

---

### Post by northern lights on 2008-07-27
> **Troll_the_Great said:**
> First, did you installed compiz?If not, install it via Synaptic
compiz fusion is installed by default on ubuntu (from gutsy and up). only ccsm needs to be added...

---

### Post by UbuntuNerd on 2008-07-27
I used this guide a while back and I found it very useful 



[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/]("http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/")

---

### Post by billgoldberg on 2008-07-27
I suggest my customization guide.

It's in my signature.

---

### Post by Sef on 2008-07-27
Applications > Add/Remove > Show: 'All Available Applications' > Search: CCSM > click on box next to ccsm > apply changes > apply > close

Read [Forlong's Blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") for how to set it up.

---

### Post by overdrank on 2008-07-27
Moved to Desktop Effects & Customization :)
You may look at the FAQ's link in my signature also.

---

### Post by Tex786 on 2008-07-27
> **Sef said:**
> Applications > Add/Remove > Show: 'All Available Applications' > Search: CCSM > click on box next to ccsm > apply changes > apply > close

Read [Forlong's Blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") for how to set it up.

THAT HELPED ALOT. 

Where do i get the ting at the buttom of my screen that will roll throgh all the different programs on my computer? I know they got the idea from apple. I would love to have it on my desktop.

thanks

---

### Post by northern lights on 2008-07-27
> **Tex786 said:**
> Where do i get the ting at the buttom of my screen that will roll throgh all the different programs on my computer? I know they got the idea from apple.That'd be a dock.

In Ubuntu there are two in the repositories, one of which is installable the same way you've just installed 'ccsm'.

That one is called "Avant Window Navigator", short AWN. You can find it under

"Applications > Add/Remove > Show: 'All Available Applications' > Search: Avant > click on box next to Avant Window Navigator > apply changes > apply > close"

Alternatively, cairo-dock is also worth mentioning. Run```
sudo apt-get update && sudo apt-get install cairo-dock cairo-dock-plug-ins
```from a terminal window.

I'd say google for screenshots to choose your dock of preference (both customizable, check several).

---

