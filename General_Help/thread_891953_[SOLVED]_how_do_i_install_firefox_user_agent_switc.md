---
title: "[SOLVED] how do i install firefox user agent switcher?  keep getting errors"
date: 2008-08-16
forum: General Help
---

### Post by bluepowder7 on 2008-08-16
on xubuntu 8.04, and using firefox 2.whatever, i'm trying to install the user agent switcher because one page i need to use at home ONLY and ONLY works with IE.  and i don't feel like rebooting into winxp just for that.

so i go tothe addons.mozilla.whatever.com page, and find the button, and press it.  but i get errors (see images below).  is there some manual way i can install it?

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/useragent1.jpg[/IMG]

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/errorlog.jpg[/IMG]

---

### Post by dje on 2008-08-16
close firefox and in a terminal try this:
```
mv $HOME/.mozilla $HOME/.mozilla.bak
```
(this backs up your firefox settings by moving them allowing firefox to create a new one in case yours is corrupted preventing installation of the addon)
then restart firefox and try installing the plugin again

you could also try:
```
sudo apt-get install useragentswitcher
```

if that fails try:
```
sudo apt-get install --reinstall firefox-2
```

dje

---

### Post by bluepowder7 on 2008-08-16
ok, um, that's kinda cool.  in a way.  i did the "sudo aptitude install useragentswitcher" and that went smoothly - well, it showed no errors.

but when i launch firefox 2.x, i don't actually see any way of changing the user agent.  am i blind?  i did try to "sudo aptitude reinstall firefox-2" and then redo the useragentswitcher, all to no visible avail.

---

### Post by dje on 2008-08-16
> **bluepowder7 said:**
> ok, um, that's kinda cool.  in a way.  i did the "sudo aptitude install useragentswitcher" and that went smoothly - well, it showed no errors.

but when i launch firefox 2.x, i don't actually see any way of changing the user agent.  am i blind?  i did try to "sudo aptitude reinstall firefox-2" and then redo the useragentswitcher, all to no visible avail.

first have a look in the Tool file menu in firefox for any signs of User Agent Switcher, also did you try the first command?

dje

---

### Post by bluepowder7 on 2008-08-16
ok, i tried the first command ONLY now, and starting firefox again DOES give me the user agent switcher in the Tools menu.  cool!  (i didn't try that the first time since you wrote 'you could also try', which led me to believe that i could do either the first bit OR the second+third bit)

anyhoo - turns out that i now lost my bookmarks.  doh!  i normally don't use firefox for much, but i did have some stuff marked.  hopefully i can find it.....

---

### Post by dje on 2008-08-16
ok no problem do this:
```
mv $HOME/.mozilla $HOME/.mozilla.bak2
mv $HOME/.mozilla.bak $HOME/.mozilla
```
then open firefox and you can export your bookmarks (could be in the bookmarks menu, although i'm using ff3 so im not quite sure). once youve exported them do this:
```
mv $HOME/.mozilla $HOME/.mozilla.bak
mv $HOME/.mozilla.bak2 $HOME/.mozilla
```
then start firefox and import the bookmarks

hope that helps
dje

---

### Post by bluepowder7 on 2008-08-16
cool, got it all back.  nice!
now to get java working so that the site thinks i'm using IE and is able to use java for the content...

---

### Post by dje on 2008-08-16
have you installed java? if not do:
```
sudo apt-get install ubuntu-restricted-extras
```
also please mark the thread as solved if the problem is solved ;)

hope i helped
dje

---

### Post by bluepowder7 on 2008-08-16
had java already, but did that restricted-extras just now anyways.  still issues, but then i've made a new thread for that.

this user switcher - SOLVED!

---

