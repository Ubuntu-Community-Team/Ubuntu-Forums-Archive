---
title: "Make Hardy Look Like Jaunty"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by JohnWesleyMethodist on 2009-10-21
Hey all,

 The menus/boot screens and so forth have changed from Hardy to Intrepid to Jaunty and will change again for Karmic.

 Is there a way to upgrade just the appearance of Hardy to make it appear like Jaunty/Karmic?

 Would you just add the Karmic repositories and upgrade Ubuntu-Destop? What other packages would need to be installed?

 Thanks

---

### Post by stlsaint on 2009-10-21
if its desktop environments that you want than you can just install the environent ie

kde environment = sudo apt-get install kubuntu-desktop
jaunty uses gnome so it would be
```
 sudo apt-get install gnome-desktop 
```

---

### Post by Mark Phelps on 2009-10-22
> **JohnWesleyMethodist said:**
> ...  Is there a way to upgrade just the appearance of Hardy to make it appear like Jaunty/Karmic?

 Would you just add the Karmic repositories and upgrade Ubuntu-Destop? What other packages would need to be installed?

 Thanks
If you're talking strictly about appearences, you can add and modify themes on your desktop to change the "look" of Ubuntu.  Themes are available from Gnome-look.org.

But if you're talking about making Hardy behave like Jaunty or Karmic (i.e., same menus, same features, etc.), the answer is no. Even if you were to change your Hardy desktop to look like a Karmic desktop, you would have menu items and features that would not work because they weren't available in Hardy.

Also, adding the karmic repos to a Hardy install is going to present all kinds of problems when you start getting package updates, and and has been said in other threads, doing partial upgrades with Karmic is a bad idea.

---

