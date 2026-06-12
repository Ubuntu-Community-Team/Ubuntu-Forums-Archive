---
title: "autoplay dvd with xine - need help"
date: 2005-11-27
forum: General Help
---

### Post by elempoimen on 2005-11-27
actually...autoplay with anything.  nothing seems to work.

so I set up the autoplay command as "xine -pdfh" but every time i insert a dvd, i get a kio error saying "/media/cdrom0 is a folder but a file was expected", and no play.  yet if i open a konsole and enter the command, all is well.

any insight?  running kde 3.5 rc2 on breezy

---

### Post by Sp@z on 2006-01-28
I started using a new search too today. I see my problem if somewhat common but this is the 4th thread I have seen about it and it is lso the 4th UNANSWERED thread about it..............:(

---

### Post by Perfect Storm on 2006-01-28
What if you add the path line to the command? I don't know much about KDE but if I want to have VLC to play right away when I insert a DVD in gnome I add: **wxvlc dvd:///dev/dvd** in removable drives and media Preferences.

---

### Post by pins on 2008-01-10
if you appened '# %u' to the command line in the KDE autoplay setup then it will drop the url rather then pass it. Picked this up on another forum.

(EDIT)
eg; wxvlc dvd:// # %u
assuming that you have a default dvd drive set up in VLC, this works for other autoplay handlers that throw the same error message.

(edit 2)
oops, thought this was about VLC (thats what I was having this problem with)

xine -pdfh # %u

should do it.

---

