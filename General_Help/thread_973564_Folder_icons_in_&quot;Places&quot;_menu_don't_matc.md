---
title: "Folder icons in &quot;Places&quot; menu don't match other icons"
date: 2008-11-06
forum: General Help
---

### Post by FSXmann on 2008-11-06
I recently upgraded to Ubuntu 8.10 and the folder icons under the Places menu have changed back to the gnome icon theme.

[IMG]http://i401.photobucket.com/albums/pp95/fsx15/Screenshot.png[/IMG]

How do I fix this so that it matches the rest of the icon set?

---

### Post by Leira on 2008-11-18
me too~ I've changed the icon set, but the places icons are still gnome style

---

### Post by Leira on 2008-11-18
Found a solution here: [here]("http://ubuntuforums.org/showthread.php?t=966436&highlight=places+menu+icon+theme"), I should have searched first, my bad. Don't forget to re-login afterwards.

> **iris-n said:**
> That's a cosmetic bug only, but quite visible.

In the Places menu of the gnome-panel, any icons other than the default theme don't show up. It is actually a gnome-icon-theme bug, but as it affects Intrepid, I think it would by nice to put here. It's [[COLOR="DarkOrange"]_launchpad entry_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033").

The workaround: 

```
sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome
```

It's due to [[COLOR="DarkOrange"]_perfectska04_[/COLOR]]("http://ubuntuforums.org/member.php?u=352049").

---

### Post by joey-elijah on 2009-03-02
I followed the above and now i have NO icons in my places menu. Just be warned.

---

### Post by jastonas on 2009-03-14
Me too! No icons at all now......

---

### Post by jastonas on 2009-03-14
but after alt ctrl bckspc everything is fine :)

---

### Post by Turbo2007ad on 2009-09-06
Hi,

I was able to solve the mismatch of the places folders rather easily.  After doing some digging I was able to determine that the places folders are using the folder.png icon located in the directory:

/usr/share/icons/gnome/24x24/places

By replacing the folder.png icon in the above directory with one of your own and restarting your system it will change the folder icon used in the places menu accordingly.  Hopefully this works for everyone else as it did for me.

---

### Post by Netom on 2009-09-15
The problem is that the theme is incomplete. Just go to the theme folder that should be either in:

  /usr/share/icons/theme_name

or in a hidden folder named .icon inside your Home folder (choose show View->Show Hidden Files)

Every theme is organized a little bit different, but you should look for the folders called "places", (for example I have this folder ~/.icons/black-white_2-Style/scalable/places), depending on the theme could be more than one "places" folder, so you must repeat the following directions for each folder.

Inside these folders it shoud be a file called "inode-directory.png" or "inode-directory.svg", these are the files missing since you cannot see the icons in the "Places" menu. So just duplicate the "folder.png" or "folder.svg" file.

Also its possible to create a link: right click on the "folder.png" file and choose "Make link", rename the resulting file with "inode-directory.png"

Log out and Log in.

That's all.

---

### Post by nairda on 2010-11-26
All that was actually needed was to remove icon-theme.cache, and reload the icons (i usually do this by going to appearance and selecting another icon theme, then going back to the one i wanted)

Some times the icon theme won't match the names required for places though, for example in Hydroxygen I had to change the links from folder-docs.png => folder-documents.png

Little things like that are easily resolved though.

---

