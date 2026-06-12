---
title: "[SOLVED] Unable to empty all items in trash."
date: 2008-11-29
forum: General Help
---

### Post by AceRimmer on 2008-11-29
There are two folders in my trash that I cannot delete, it gives me errors every time I try.  How do I force these to delete?

---

### Post by Xiong Chiamiov on 2008-11-29
You can delete these items manually through the terminal.
```

sudo rm -rf ~/.local/share/Trash/files/*

```
or
```

sudo rm -rf ~/.local/share/Trash/*

```
[linky]("http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html")

I'm not sure where the Trash folder is in 8.10.

---

### Post by beno1990 on 2008-11-29
What error does it give you when you try to delete them? If it's permission denied, restore them, open nautilus as root using alt+f2 and typing "sudo nautilus", and then delete them as root. But you'll also have to empty the trash from within Nautilus, because you're deleting it to Root's deleted items folder, not your own user's.

---

### Post by drs305 on 2008-11-29
Trash in 8.10 Intrepid is at /home/*username*/.local/share/Trash

Here is a link to all sorts of info and techniques on finding and deleting trash from your system:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by AceRimmer on 2008-12-02
> **beno1990 said:**
> What error does it give you when you try to delete them? If it's permission denied, restore them, open nautilus as root using alt+f2 and typing "sudo nautilus", and then delete them as root. But you'll also have to empty the trash from within Nautilus, because you're deleting it to Root's deleted items folder, not your own user's.

When I hit "empy trash" they just don't get removed.  When I open trash and try to delete them I get permission denied.

when I run sudo rm -rf /home/aaron/.local/share/Trash/* nothing happens.  When I go to that directory it shows being empty. However files are still in the trash can, a few hundred megabytes worth. I did a sudo nautilus and got an error when i tried to empty the trash.

---

### Post by Bott on 2008-12-02
> **Xiong Chiamiov said:**
> You can delete these items manually through the terminal.
```

sudo rm -rf ~/.local/share/Trash/files/*

```
or
```

sudo rm -rf ~/.local/share/Trash/*

```
[linky]("http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html")

I'm not sure where the Trash folder is in 8.10.

Thanks for the fix.  The second code line got rid of a pesky folder that wouldn't delete from Trash!

---

### Post by AceRimmer on 2008-12-04
I figured it out.  There is a trash folder on my backup hard drive.  So I went in there, adjusted the permissions on the folders and the trash emptied.  Thanks everyone.

---

