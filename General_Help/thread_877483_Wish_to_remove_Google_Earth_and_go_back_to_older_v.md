---
title: "Wish to remove Google Earth and go back to older version - HOW?"
date: 2008-08-01
forum: General Help
---

### Post by kystorms on 2008-08-01
I have installed Google earth via the Google Websites download, 
and see that it will not work on my machine, no earth present.

Have no idea why it wont work, since there seems to be many different reasons for this to occur in Hardy.

I wish to delete this install and then install a lower version in hopes of that working, 
can someone please point me to directions on how to delete / uninstall?

I coded in terminal , whereis googleearth and it told me it was in my
/usr/local/bin/googleearth and seeing no uninstall files, tried to delete however I was refused access to it that way.

any help appreciated!
:confused:

---

### Post by drs305 on 2008-08-01
Did you locate a googleearth folder anywhere? You can search for it with:

```
sudo find / -type d -iname *googleearth
```
or
```
sudo find / -type d -iname googleearth
```

If you find a folder with an uninstall file in it and it isn't in your home folder, use "gksu nautilus" or "sudo" along with the path/filename in a terminal to uninstall it.

---

### Post by jacktar on 2008-08-02
I also have this problem. When I start it using the icon it only shows a black screen with stars. It does run properly from terminal as root though.

---

### Post by mikewhatever on 2008-08-02
Just get the older version and reinstall over the current one. The bin file it comes in unpacks to the desired location, so that it would overwrite the directories.

---

