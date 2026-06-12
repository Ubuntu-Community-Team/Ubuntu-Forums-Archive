---
title: "Jaunty upgrade language / locale mess"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by bhrgunatha on 2009-04-27
I was previously on Kubuntu Hardy with English British/English US and Chinese Locales and English and Chinese languages installed. I CANNOT read Chinese but I am learning and so I use Skim to help.

After upgrading to Jaunty today ALL menus and applications menus were in Chinese. I eventually managed to find the regional settings to try to change System Language to British English but no change was apparent. After struggling for several hours trying to find regional and language settings settings I eventually uninstalled the Chinese Language in frustration.

Now half the menu items are English and despite uninstalling Chinese many/most are still displayed in Chinese. 

Here is a screenshot that shows the current state : [http://imgur.com/F16P.png](http://imgur.com/F16P.png)

How can I get back to my original KDE 3.5 configuration with everything displayed in English?

---

### Post by AlanPo on 2009-04-30
> **bhrgunatha said:**
> I was previously on Kubuntu Hardy with English... 
After upgrading to Jaunty today ALL menus and applications menus were in...

Now half the menu items are English and despite uninstalling Chinese many/most are still displayed in Chinese. 

How can I get back to my original KDE 3.5 configuration with everything displayed in English?

So do I.  I have had gnome and english, latvian and russian language support installed.  Now if I install some other language support (I need keyboard layout) it makes all the ubuntu in that language!!!!!!! removing that language causes interrupted boot process saying that this locale do not exist. Sure it does not.

So language support is a total mess in Jaunty. It's not up to KDE or Gnome. It's about Jaunty. And - please fix it someone.

---

### Post by nicholas22 on 2009-05-18
The solution to this was simple for me:

- Re-install the offending locales (as the problem lies with messy un-installation)
- Reboot
- Run System Settings and ENSURE no other apps are running (e.g. for me running Firefox, terminal, another system panel etc. were the sources of problems)
- Uninstall the languages 
- Reboot

Now everything should be clean again. ;)

---

