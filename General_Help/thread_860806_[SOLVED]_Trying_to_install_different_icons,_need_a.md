---
title: "[SOLVED] Trying to install different icons, need a bit of help"
date: 2008-07-15
forum: General Help
---

### Post by Drizzel on 2008-07-15
Yes I'm a n00b.. I'm on art.gnome.org trying to understand their vague instructions on installing icons. In the wiki I read this.. "And clicking on the "Go to Theme Folder" in the Icon tab of the Theme Details window will take to the correct location for Icon themes." Something about the The GNOME Theme Manager. I see nothing about "Go to Theme Folder" anywhere in ubuntu.

How do I access the The GNOME Theme Manager? So I can find where the icon and theme directories are so I can just manually extract the icons. Needs to be so diffucult... :(

---

### Post by ad_267 on 2008-07-16
Go to System - Preferences - Appearances. Drag the theme onto this window and it will install. Not difficult at all.

---

### Post by Drizzel on 2008-07-16
The difficult part I was speaking of is finding where the icon directory is. That is difficult, I've been searching through all my folders forever. I did manage to get some themes installed, but cant install icons.

---

### Post by ad_267 on 2008-07-16
Did you read my post? You don't need to know where the icon folder is, just drag and drop onto the system - preferences - appearance. It's in ~/.icons and you can create that directory if it doesn't exist.

---

### Post by Drizzel on 2008-07-16
No I totally just blew past it.. Yes I read your post. I drag the icons where you said and it didnt work.

From the wiki i'm reading: "The GNOME Theme Manager does not install Icon themes into the correct location. Theoretically, Icon themes could be installed using the same method as Application and Window Border methods, but your Icon theme won't appear in the list"

All I want to do is find the icon folder so I can manually extract the icons to that folder, so, yeah I need to know where the icon folder is.

---

### Post by Drizzel on 2008-07-16
Ok I found the answer. Just needed to hit ctrl+h to unhide the icon folder in the home directory. I extracted the icons to that folder and now they show up.

---

### Post by ad_267 on 2008-07-16
Ok well that's a bit more helpful. For most themes you should be able to do what I said. If the theme isn't configured properly to allow this you will get an error like invalid theme.

Usually what I find is that if you extract the file there will be either directories inside or archives that are a valid theme that you can then drag onto the Appearance Preferences window. If you want to install them by putting them into a directory you can put them in ~/.icons, if that doesn't exist you can make it. It needs to have the "." before icons.

---

