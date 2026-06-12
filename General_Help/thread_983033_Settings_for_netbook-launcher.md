---
title: "Settings for netbook-launcher?"
date: 2008-11-15
forum: General Help
---

### Post by oedipuss on 2008-11-15
I'm finding netbook-launcher very useful, even for a desktop system, but I can't configure it from anywhere.
 Are there any settings or config options available, or is the way it looks just hard-coded ? 

I'm looking for small appearance tweaks that might be useful, like how much it dims the desktop, what size it will be, things like that.

Edit:Oh, I'm using the default intrepid version from universe, package 'netbook-launcher' v. 1.2-0ubuntu1

---

### Post by Aphoxema on 2008-12-17
I'm interested as well, it's a really cool application but it's annoying how it expects a certain layout of the gnome-panel.

---

### Post by DaveM753 on 2009-02-28
Yes, the netbook-launcher is easy to get addicted to, but there's 2 things I'd like to be able to do:

1) Configure it - for instance, I'd like to be able to make the icons just a tad smaller (so more will fit on screen)

2) Add my own shortcuts.  I'd like to add a shortcut (sorry...we call them Symbolic Links, don't we?) into the netbook-launcher's Favorites.

Even without those, the netbook-launcher is really nice!  Thanks to the developers!

--Dave...

---

### Post by zman0900 on 2009-03-02
I am also trying to find the settings.  I am trying to find out how I can change what the various bookmarked folders are launched with (Documents, Music, Pictures, etc).  I was able to edit the appropriate desktop files so that they launch with pcmanfm from the regular gnome menus, but netbook-launcher still uses nautilus.

---

### Post by sunrise-7 on 2010-04-01
No one seems to be answering here and I came across the queries while finding my own answers, so here is a few leads.
1. I actually did not know what the "UNR" was, wanted to get rid of it after upgrading to Ubuntu 9.10 on a desktop, and didn't get any replies to that. I eventually succeeded by finding an entry on the System Menu for something called the Netbook Launcher, and deleted it experimentally, to my Joy.

2. For those of you who really like this application, which could be great on a Netbook, I suggest that you consider doing what I have learned to do ... do a search on google.com I find that doing a search on the Forums often gets me no where. Doing a Search on Google often gives me multiple relevant links IN the Ubuntu Forums!

3. Here are some starter links:
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)
[http://packages.ubuntu.com/intrepid/netbook-launcher](http://packages.ubuntu.com/intrepid/netbook-launcher)

There is a good chance that you will find the detail on these, or, a link from them.
Enjoy

---

### Post by mk67 on 2010-05-10
The only thing I found it's to munipulate /usr/(local)/share/applications/ directory to match my willing.
Other is maybe arround gconf and xml files, or start in Gnome session and rewrite menu config in the matching wills.
I do not try this last ones. the first work (don't forget to make a backup of your desktop files first).
i personaly use a /usr/local/share/applications/*.deskop and make a complete backup of /usr/local/share/applications/, then erased it and made a simlink to /usr/local/... becuse of further software installations.

There probably a secure way, but I didn't find it yet.

---

### Post by kalos on 2010-05-16
To change what menu options are shown in the netbook interface (the menus on the left in [this image]("https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png")), open Main Menu: Go to System and then in the Preferences section, select Main Menu. You can then add, remove, hide, and reorder your applications. 

I don't understand other configuration. There's not much in gconf-editor.

There's also a config file that I don't know what to do with here: ~/.netbook-launcher-efl/conf


FYI, there are two netbook-launchers. The efl variant is supposed to be themeable, but I think you have to understand how Enlightenment theming works. See here: [http://www.linuxuk.org/2010/02/the-new-ui-for-arm-based-ubuntu-devices/](http://www.linuxuk.org/2010/02/the-new-ui-for-arm-based-ubuntu-devices/)


You can check that you have efl variant by running ```
ps aux | grep [n]etbook
```
It will output netbook-launcher or netbook-launcher-efl.

---

### Post by kalos on 2010-05-16
> **zman0900 said:**
> I am trying to find out how I can change what the various bookmarked folders are launched with (Documents, Music, Pictures, etc).

I think the items in netbook launcher's File menu are the bookmarked folders in Nautilus. To change, open a folder and drag new folders into the panel on the left. Or right click on folders in the left panel and say Remove.

---

### Post by dsfitzpat on 2010-09-09
The efl version is what you get if you choose the 2D netbook edition at login.  I'm not sure about previous versions but in Lucid you can change things like the favourites (and the order in which they appear) using gconf-editor.  Go to Apps -> Netbook Launcher -> Favorites.
Then change the order of things in favorites_list.  (You can see what App0, etc are by expanding the Favorites tab.)

---

### Post by mk67 on 2010-09-10
Wow, old thread, I've totaly forget it!!

Don't bother with gconf etc...
The very simple way is to use the menu editor in system tab.

You can manage any thing you want there:
hide, unhide, erase, create menutab/launcher, etc ...

I've made, with the lazy help of my neurones, a multiboot usbkey. One part of the filesystem is dedicate to ubuntu-netbook-launcher manage for tools and etc ...
here is how it looks like:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169041&stc=1&d=1284109475[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169042&stc=1&d=1284109475[/IMG]
I know it's in french, you know now where i'm from ...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169043&stc=1&d=1284109868[/IMG]

You can proceed as you wish, it just take a little time to do:):P

---

### Post by vmemmanuel on 2010-11-29
In Netbook for maverick 10.10, this is how I edited the launcher:
Remove an item: Right click on it and choose " Remove from launcher"
Add an item: First start the application that you want to add. An icon shows up in the launcher. 
While the application is still running, right click the icon, choose "keep in launcher"
Hope this helps.

---

### Post by vmemmanuel on 2010-11-29
In Netbook for maverick 10.10, this is how I edited the launcher:
Remove an item: Right click on it and choose " Remove from launcher"
Add an item: First start the application that you want to add. An icon shows up in the launcher. While the application is still running, right click the icon, choose "keep in launcher"
Hope this helps.

---

### Post by freedom on 2010-12-01
Is it possible to add some shortcuts, like to Desktop folder or Documents folder?

---

