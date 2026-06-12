---
title: "How-to Write To a Floppy Media in ubuntu"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by sarah_b on 2005-12-17
1.from a terminal enter:
sudo gedit /usr/share/applications/nautilus-root.desktop

2.Insert the following lines into the new file:

[Desktop Entry]
Name=file Browser (Root)
comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;

3. save the new file and exit.

4. from a terminal enter:
sudo mount /dev/fd0

5. go to:
Applications > System Tools > File Browser (root) and open.
Then go to and open floppy0 from the root file browser

6. from a terminal enter:
sudo gedit /home/your_user_name/your_file_path

7. drag & drop the file from step 6 into your nautilus root browser floppy directory.

---

### Post by mjkey on 2005-12-17
I got as far as step number 5 - the only folder with the name "floppy0" is located in /media/floppy0, any:???:  suggestions?

---

### Post by sarah_b on 2005-12-17
[QUOTE=mjkey]I got as far as step number 5 - the only folder with the name "floppy0" is located in /media/floppy0, any:???:  suggestions?[/QUOTE]

so you were able to do this part:
Applications > System Tools > File Browser (root) and open

---

### Post by sarah_b on 2005-12-17
mjkey 

If you are able to open your (root) browser that you created, what do you see in the left pane window ?

---

### Post by mjkey on 2005-12-17
Home
Desktop
Filesystem

---

### Post by sarah_b on 2005-12-18
[QUOTE=mjkey]Home
Desktop
Filesystem[/QUOTE]

mjkey, your floppy may not be mounted. When you mounted your floppy, did it show up on your desktop ?

There is something wrong there, it should also show your hard drives, such as hda1 in your browser window and on your desktop.

---

### Post by OBnascar on 2005-12-18
Hi sarah,

Great tip, that worked perfect for me. Although I am sure there will be critics about using a root browser. But hey, it works ! Something that I have not been able to do before.

jerry

---

### Post by mjkey on 2005-12-18
duh, I guess the floppy has to be in drive to mount. Now I can read and write to floppy. Thanks alot.:)

---

### Post by sarah_b on 2005-12-18
[QUOTE=mjkey]duh, I guess the floppy has to be in drive to mount. Now I can read and write to floppy. Thanks alot.:)[/QUOTE]

I'm glad it worked for you..........sarah

---

