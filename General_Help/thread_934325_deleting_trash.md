---
title: "deleting trash"
date: 2008-09-30
forum: General Help
---

### Post by Hopalong on 2008-09-30
When clearing the wastebasket, it gets stuck on one folder - which has sub-folders (is this the problem?). It gives a message saying 'Error while deleting', which under 'details' gives one file name and says 'Error removing file: Permission denied'. Whose permission? and where can I give mine? Yes, its my machine, and has no other users.
  If I open the folder, right-click on the file, and ask to delete this, I still get the massage.

---

### Post by Ryadt on 2008-09-30
Type in terminal```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by Spaceman9 on 2008-09-30
Press Alt+F2 and a window will pop up. In the line at the top of the window type gksudo nautilus. Then hit Enter. Nautilus will open with root access so you can change permissions.

Go to the folder where the files is that you need to change permissions. Right on the file and click on the tab that says"Permissions". Type in your user name in the 2 lines where it says root or has a number. That will change the permissions so you can have access to the file.

Then go back up to the folder the file is in and delete the file.

Ok, one thing here. When you run Nautilus in root mode, you can delete any file without changing the Permission of the file first, so I just told you how to change Permissions so you'd know.

Hope this helps.

---

### Post by Hopalong on 2008-10-02
Yes Ryadt! It worked.

---

### Post by Hopalong on 2008-10-02
Tried te gksudo Nautilus trick, but it never replied. Should I have put a file name somewhere?

---

### Post by Ryadt on 2008-10-02
Type it in either the terminal or do Alt+f2 and input it in there. ```
gksudo nautilus
```

---

### Post by Hopalong on 2008-10-02
This time I got into nautilus (with a l.c. 'n'!) but when I selected 'Deleted items' it said 'the folder contents could not be displayed'. (Yes, I did put two files in there first!.)

---

