---
title: "Panel Icon Customization"
date: 2008-09-08
forum: General Help
---

### Post by C0L7 on 2008-09-08
I recently installed Ubuntu 8.04 for the first time. I quit windows vista ultimate cold turkey. I am not using a VM or anything, just straight up quit. haha. anyhow heres my issue....

I am customizing my desktop and making it all pretty, and so far so good. I am stuck with one thing, the Menu Bar (Applications, Places, System). I really want to get rid of the orange/brown ugly color on the left of this menu bar which is the Ubuntu symbol. I have 2 questions. 

1. How big is this icon, so i can create my own icon to replace it with.
2. How can i replace this ugly icon with the one i am going to create?

Help is appreciated. Thanks (screenshot is available to help u understand if you dont get wat i mean)

C0L7

---

### Post by C0L7 on 2008-09-08
*bump

Cant anyone help? or am i in the wrong forum?

---

### Post by rainwalker on 2008-09-08
I'm not sure how to do what you want, though I know it can be done because different icon sets use different icons there...maybe try searching for "change menu bar icon" or something like that.

*Great* looking desktop, by the way!

---

### Post by robz0rz on 2008-09-09
That icon is determined by the icon-theme you use.


System > Preference > Appearance > Customize > Icons

If you want to keep your current icon-theme, but just change that icon, you should find the theme you are using (either in /usr/share/icons or in ~/.icons), create a copy of it and rename it something you like, and then look for the icon called

/[your-icon-theme]/[size]/places/start-here.png

It's quite possible that this icon is a link to maybe gnome-main-menu.png or distributor-logo.png. If that's the case, just change the logo that is linked to, and all the links should change with it.

The icon that is in your screenshot is the 24x24 version I believe. I decided to add a nice icon that keeps the ubuntu-spirit to your desktop, but removes the orange. I hope you like it :) I took the liberty to rip this icon from the awesome [Discovery icon-theme]("http://hbons.deviantart.com/art/Discovery-Icon-Theme-77399781").



I hope I was of any help.

---

### Post by eotakos on 2008-09-12
i don't know about C0L7, but this info was helpfull to me so... thanks!

it would be nice to mark this thread as solved by the way

---

