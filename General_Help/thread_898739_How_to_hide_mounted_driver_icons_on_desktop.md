---
title: "How to hide mounted driver icons on desktop?"
date: 2008-08-23
forum: General Help
---

### Post by Yunus Emre on 2008-08-23
Hi.
I've permanently mounted my NTFS drives, following the guide on forums, but now the icons always appear on my desktop. How to make them disappear?

---

### Post by Bionic Apple on 2008-08-23
Go to Applications -> Accessories -> Terminal.  Type in "gconf-editor".  Go to Apps -> nautilus -> desktop.  On the right hand side of the window, there should be an option that says "volumes_visible".  Uncheck it and have a great day!

---

### Post by Scunge on 2008-08-23
Alternatively, AFAIK only volumes mounted in /media will be shown. If you mount them elsewhere they won't show up, but you can always make a link on your desktop to the mount folders you might want.

This is useful for a multi-user system where by default you don't want to have things like drives shown, but can't necessarily get into each user's account to change the settings to not display them.

Also, it's easy in a backup program to "exclude /media" and those NTFS drives still be backed up, rather than having to fiddle about with "exclude /media except for ...".
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by Yunus Emre on 2008-08-24
Thanks, it's better now :)

---

### Post by disconnect5 on 2008-08-24
i use the app 'ubuntu tweak'. i believe you can adjust this within it as well

---

### Post by HuckBerry on 2010-03-07
Has anyone gotten this procedure (gconf-editor) to work on Ubuntu 9.10 Desktop? I've used this since 8.04 however after a fresh install to 9.10 it no longer seems to work. Just wondering if my experience is unique.

---

### Post by krige on 2010-06-25
> **Scunge said:**
> Alternatively, AFAIK only volumes mounted in /media will be shown. If you mount them elsewhere they won't show up, but you can always make a link on your desktop to the mount folders you might want.

This is useful for a multi-user system where by default you don't want to have things like drives shown, but can't necessarily get into each user's account to change the settings to not display them.

Also, it's easy in a backup program to "exclude /media" and those NTFS drives still be backed up, rather than having to fiddle about with "exclude /media except for ...".
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

Thank you Scunge, that was the clearer explanation on how to solve this problem.

I guess now I need to find out where my volumes are auto-mounted to /media/ and change that to /mnt/

---

### Post by krige on 2010-06-25
I have found a great tool in Ubuntu Software to easily manage storage devices, it's called "Storage Device Manager".

---

