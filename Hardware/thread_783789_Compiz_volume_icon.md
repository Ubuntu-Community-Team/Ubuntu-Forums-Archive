---
title: "Compiz volume icon"
date: 2008-05-06
forum: Hardware
---

### Post by Z_o-s-o on 2008-05-06
Is there any way I can get that nice big white volume icon back when using the mac4lin icons with compiz.

The icon that comes with mac4lin is stretched out and off center when compiz is enabled, and I want to change it back to the normal white compiz one, but dont know how.

---

### Post by jocko on 2008-05-06
Compiz doesn't provide any icons.
Do you mean you want the *gnome* icon back?
If you just want to replace one specific icon, you can find the human icons (the standard ubuntu icons) in /usr/share/icons/Human.
I'm not sure what's the best way, but I think it would be possible to just replace the icon in the current theme (probably stored in the folder ~/.icons in your home directory) with one from the human theme.

---

### Post by Z_o-s-o on 2008-05-06
The thing is I cant find that white volume icon in any of the icon folders in /usr/share/icons

---

### Post by jocko on 2008-05-06
Are you sure? Have you checked if you have this:
/usr/share/icons/Human/scalable/devices/gnome-dev-harddisk.svg
???

---

### Post by Z_o-s-o on 2008-05-06
What I'm trying to do is change the big ugly speaker icon in this screenshot back to the nice white one, like when using human icons...problem is, the white speaker icon is nowhere to be found in any of the icon folders anywhere.

[IMG]http://i30.photobucket.com/albums/c337/masterd151/Screenshot.png[/IMG]

---

### Post by jocko on 2008-05-06
Ahh.. I see... I must have been a little bit dazed and confused there...
I didn't think of that as an icon, so I just assumed that by "volume icon" you meant the icon for mounted volumes...
It appears to be connected to the human icon theme, but I can't find the actual file anywhere either...

---

### Post by trigoman05 on 2008-06-30
I also had the same problem and I looked and looked for the icon but it seems that the only way to get this is by having no icon at all!!
Just to make sure we are on the same page this is the icon right?
[URL="http://i284.photobucket.com/albums/ll35/trigoman05/Screenshot.png"]
[IMG]http://i284.photobucket.com/albums/ll35/trigoman05/Screenshot-1.png[/IMG]
[/URL]
To get this icon, I just deleted the volume icons from the current icon theme. So navigate to:

/usr/share/icons/<your_current_theme>/scalable/status/

Now delete/rename/move the icons with the following names

audio-volume-high.svg  audio-volume-medium.svg
audio-volume-low.svg   audio-volume-muted.svg

That's all! Now you will have the normal-looking-volume icon. Enjoy!!!

NOTE:You may need to access the ../status/ directory as root. To do that press ALT+F2 then type gksudo nautilus /<the_directory_above>/

---

