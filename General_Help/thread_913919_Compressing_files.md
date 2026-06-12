---
title: "Compressing files"
date: 2008-09-08
forum: General Help
---

### Post by Mclinux on 2008-09-08
Does anyone know a GUI file compresser?  Everytime I try to install one it doesn't appear to be anywhere in my applications list, which leads me to believe it needs to be used on the CLI.  The issues I have with using the CLI is that when I name my file/folders through the GUI I have a bad habit of using spaces, so I can't navigate using the terminal because it doesn't recognise the file names/folders.

---

### Post by Pelham123 on 2008-09-08
Think its 'Archive-Manager'.  Cant remember if its installed by default. Its located in Applications -> Accessories. If it is not there you can use Applications -> Add/Remove to install it.

---

### Post by aloshbennett on 2008-09-08
Select files, right click them and select 'Create Archive' :)

---

### Post by Denestria on 2008-09-08
When you have trouble with spaced file names on the command line all you have do is use [tab] to complete the name or encase it in quotes.

If the file name is         spaced file name          then type spac[tab]
it will fill in the the rest to say spaced file name

or

gzip "spaced file name"

**
You can also escape spaces with

spaced\ file\ name

---

### Post by mb_webguy on 2008-09-08
> **Pelham123 said:**
> Think its 'Archive-Manager'.  Cant remember if its installed by default. Its located in Applications -> Accessories. If it is not there you can use Applications -> Add/Remove to install it.

The actual application is called File Roller, and is listed in the repositories as file-roller.  It is, however, listed in the Gnome menu as Archive Manager.  File Roller can use various command line archive managers such as p7zip to extend its capabilities.  However, it's somewhat limited in using these to create archives.  For example, if you want to create a 7z archive using the highest compression level, you have to use the command "7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on files_to_be_added".

As far as file names with spaces in the terminal, as the others have said, you can either use tab to auto-complete the filename, escape the spaces with a backslash (e.g. *filename\ with\ spaces.txt*), or enclose the filename in double-quotes.

---

