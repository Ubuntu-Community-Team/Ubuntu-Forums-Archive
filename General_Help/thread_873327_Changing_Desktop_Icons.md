---
title: "Changing Desktop Icons"
date: 2008-07-28
forum: General Help
---

### Post by dennismoore1 on 2008-07-28
Hello,
  If you're like me and hate the gnome default program launcher icon then this will probably help.  There are two ways to change it read way 1 if you're using a link and way 2 if you're using a launcher.  Wine windows emulator is required to do this.

    Way 1:  If you are using a link
         1.  Delete the link.
         2.  Create a empty text file.
         3.  Write the following code in the file.
cd "(directory of file)"
./(file name)
             With the quotes included and the parentheses not included.
         4.  Name the file something with a . as the first mark (.example)
         5.  Open terminal and navigate to the Desktop and type the following code:
chmod 775 (filename)
         6.  Make a launcher, name it and/or comment it.
         7.  Make the command the following:
bash "/home/(username)/Desktop/(file name)/"
         8.  Go to Applications -> Wine -> Programs -> Accessories -> Notepad
         9.  Go to File -> Open
         10.  Navigate to the Desktop and select the launcher (filename.desktop)
         11.  If one of the lines starts with "Icon=" backspace the current icon and write in the directory of the desired image.
         12.  If no line starts with "Icon=" make one.
         13.  File -> Save
         14.  Exit all programs and restart your computer.
         15.  The changes will have been made.
    Way 2:  If you are using a launcher.
         1.   Open Notepad with wine.
         2.   Open the launcher as text in notepad.
         3.  If one of the lines starts with "Icon=" backspace the current icon and write in the directory of the desired image.
         4.  If no line starts with "Icon=" make one and follow instruction 3 of Way 2.

---

### Post by rune0077 on 2008-07-28
Indeed, you can just right click the icon, select "Properties", click the image of the icon in the window that opens, and point it to the icon you want instead. :)

---

### Post by ad_267 on 2008-07-29
Haha yeah that's a lot of effort you don't need to go through.

Also, notepad in wine? You can just use gedit or any other text editor for this.

And you can go to [http://www.gnome-look.org](http://www.gnome-look.org) and download a whole new icon set if you want.

---

### Post by dennismoore1 on 2008-07-29
Oops, kinda over analyzed it. Rune you're right, but ad is wrong gedit does not work, and who wants their images limited to gnome's?

---

### Post by Gourgi on 2008-07-29
> **dennismoore1 said:**
> Oops, kinda over analyzed it. Rune you're right, but ad is wrong gedit does not work, and who wants their images limited to gnome's?

i believe you can use your own images, not just gnome's ;)

---

### Post by ad_267 on 2008-07-30
> **dennismoore1 said:**
> Oops, kinda over analyzed it. Rune you're right, but ad is wrong gedit does not work, and who wants their images limited to gnome's?

Gedit doesn't work?

Go to applications - accessories - text editor. Click on file - open. Browse to the .desktop file and open it. Not very hard.

Or in a terminal. "gedit name.desktop"

---

