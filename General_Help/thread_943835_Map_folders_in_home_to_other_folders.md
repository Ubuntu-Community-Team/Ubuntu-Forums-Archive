---
title: "Map folders in home to other folders"
date: 2008-10-10
forum: General Help
---

### Post by ericesque on 2008-10-10
I'm trying to 'map' my music collection to my /home/user/Music folder.  

I would like to double click the /home/user/Music and see the contents
of /media/media/Music

I managed to use symlinks so that in my /home/user/Music folder, I see a symlink for every artist folder in my /media/media/Music folder, but I swear in the past I was able to make it so that clicking /home/user/Music actually opened /media/media/Music...

If anyone can make sense of what I just said, any ideas on how to achieve this?

---

### Post by Sam on 2008-10-10
Try this in a terminal:
```
mv /home/user/Music /home/user/Music_OLD
ln -s /media/media/Music /home/user/Music
```

---

### Post by Ms_Angel_D on 2008-10-10
An easy GUI way to do this is with [Ubuntu Tweak]("http://ubuntu-tweak.com/") if you look under personal there is a section called folders and it allows you to change the paths.

---

### Post by ericesque on 2008-10-10
that puts a folder in /home/user/Music  named Music that links to /media/media/Music  (though the address bar says it's /home/user/Music/Music)

I'm looking to eliminate the step of that 'go to' link in the /home/user/Music folder.

---

### Post by Sam on 2008-10-10
Ok I see the point.

I think the only way to achieve this is to put a launcher in your home folder.

Create a new file /home/user/music.desktop and paste this in:
```
[Desktop Entry]
Name=Music
Comment=Display music folder
Type=Application
Exec=nautilus /media/media/Music
Icon=folder
Terminal=false
```

---

### Post by geirha on 2008-10-10
That happens if /home/user/Music allready exists when you run the ln command that Sam gave you. That's why he also put an mv command before that, to rename the existing Music folder to Music_OLD.

So make sure you include the mv command. Here's more or less the same as Sam posted, but with the special tilde (~) which is a "shortcut" for your home directory (/home/your-username)
```

mv ~/Music ~/Music_OLD
ln -s /media/media/Music ~/

```

EDIT: Also, if you have a Music bookmark in the left frame of nautilus, you can right click it and remove it, then browse to /media/media and drag the Music folder to the left frame to create a new bookmark.

---

### Post by ericesque on 2008-10-10
> **geirha said:**
> 
EDIT: Also, if you have a Music bookmark in the left frame of nautilus, you can right click it and remove it, then browse to /media/media and drag the Music folder to the left frame to create a new bookmark.

That's what I was looking for! Thanks!  I didn't realize that updating the bookmarks in the 'places' sidebar in nautilus would do the same in the places menu on the panel.  :KS

---

