---
title: "[SOLVED] Help newbie! Too many deleted files in &amp;quot;Open File&amp;quot; dialog."
date: 2008-10-31
forum: General Help
---

### Post by kozlovsk on 2008-10-31
Hi!

Newbie question. Why does Gnomes "Open File" dialog shows all deleted files (with ~ at the end)? I am using desktop a lot, and even though the desktop is now almost empty, it's impossible to use "Open File" dialog, because it shows hundreds of files that don't exist, it just takes too long to find the right ones.

---

### Post by kozlovsk on 2008-10-31
At least it would be great to know, if it is normal, and what was the idea of making such feature?

---

### Post by Thomas Jensen on 2008-10-31
It is normal, the files with **~** at the end are backups. They are made automatically when documents are being edited, I think you will have to disable this feature in the individual applications. All I know is that in gedit (the "Text Editor") this is done in **Edit > Preferences > Editor**.

Oh and to make the backups not show up in the open/save file dialogs: Right click on the file listing and (de)select "Show Hidden Files". This option can also be found in the file browser under the view menu.

NB: When you enable viewing of hidden files you will not only see the files ending with ~, but also files beginning with a period (**.**), particularly (probably only) in your home folder. These hidden files commonly contain settings and preferences pertaining to the user whos home folder they are in. You should not delete them.

---

### Post by kozlovsk on 2008-10-31
Thanks a lot! I think they were all made by Gedit, I like it and use it a lot. I've opened the Places > Desktop in Nautilus, Ctrl-H to show hidden files, and deleted them. 

Thanks again!

---

