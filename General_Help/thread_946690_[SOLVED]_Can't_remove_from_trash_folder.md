---
title: "[SOLVED] Can't remove from trash folder"
date: 2008-10-13
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2008-10-13
I copied some files from a backup cd to a folder on the desktop. The copy operation didn't work correctly for some reason, so I deleted all the empty folders that were created. Now I am not allowed to empty the trash folder. It seems that I don't have permission to read the empty folders in the trash.

---

### Post by brianfreytag on 2008-10-13
move them back to your desktop.

Go to terminal
```
sudo rm -rf /path/to/folder
```

You'll have to type in your password when it asks for a sudo password.

This will remove the folder and anything inside of it.
Do this for each folder.

---

### Post by fooman on 2008-10-13
i have had that happen to me before....try this in a terminal:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by newman on 2008-10-13
Beautiful. Thanks, I was having the same issue.

---

### Post by drs305 on 2008-10-13
It does happen to a lot of people. Just be careful with the combination of sudo and rm. An inadvertent space here or there can really mess up a system. 

The other option to remove trash, with perhaps a bit more work and definitely a bit more safely, is to open a file browser such as nautilus with the "gksudo" command. This will allow you to go to the directory and individually delete trash folders. The chances of deleting an entire partition are less with this method.

I'm not saying not to use the command line, just be careful. Cut & paste commands that you know are safe instead of retyping them, and make sure you know what you are doing if you use sudo combined with rf -f. Another option is to 'chown' a folder that has files you want to delete but can't (sudo chown -R username /path/to/folder) so that you own the contents.

For an explanation of how to find and delete trash using various methods visit the 'Disk Full' link in my signature.

---

### Post by ihatetryingtopickaloginna on 2008-10-13
Thanks everyone. Some good advice here.

---

