---
title: "Two panels in KDE / small buttons in Gnome"
date: 2008-11-07
forum: General Help
---

### Post by newgalois on 2008-11-07
I have a mix feeling choosing between gnome and kde for my ubuntu. Applications are not a big problem as I don't mind running KDE apps on gnome or gnome apps on KDE. The problem is I like the two panels look of gnome/ubuntu as much as I love the small button size of KDE. Is there a way to get the best of the two worlds? Either make the gnome buttons smaller or get two panels in KDE 3? Yup, I know that I can add a panel, or an external taskbar in KDE. However, I cannot change their size for some reason :(.

Thanks

---

### Post by cdtech on 2008-11-07
I really didn't like having all that KDE on my GNOME desktop. I'm not sure if this is what your asking but maybe this can help you as well.

If you use the Gnome desktop (like I do) try this:
Make a backup:
```
mkdir ~/.desktopbackup
cp -R /usr/share/applications/ ~/.desktopbackup
```
On a command line type:
```
for i in /usr/share/applications/kde/*; do echo "OnlyShowIn=KDE;" | sudo tee -a $i; done
```
You could also do the same with KDE by changing it to:
```
for i in /usr/share/applications/*; do echo "OnlyShowIn=GNOME;" | sudo tee -a $i; done

```
Hope this helps.........

---

### Post by newgalois on 2008-11-08
These are really good tips to ... another problems that I encountered. However, my question was about the look and feel of the two desktop environment. If you have used both environment, you'll see that KDE is more compact. The buttons are smaller (in size). The list items are nearer to each other. I'm using a 2.5 year old laptop with highest solution being 1024x768. In some Gnome applications (such as gnumeric), some dialogs pop out of my windows, which is very annoying. In kde, everything's ok. 

On the other hand, I just love the two panels in gnome and is struggling to get them on kde. 

A related question: I prefer the warm "human" theme in ubuntu to the cold blue-ish theme of kubuntu. Is there a "human" theme for kde?

Thanks

---

### Post by newgalois on 2008-11-24
Problem solved!

I installed the oxygen theme for Gnome
[http://kims-area.com/?q=node/62](http://kims-area.com/?q=node/62)

Thanks for your replies!

---

