---
title: "Zipping Multiple Files"
date: 2008-09-18
forum: General Help
---

### Post by Starclopsofish on 2008-09-18
So I recently aquired a large collection of files (of which type will remain nameless for legal/forum rules reasons) which can be accessed even when zipped. Since there are 500+ of these files, I'm very interested in zipping them up, as this could save up to a Gigabyte of space. 

Anyway, due to the sheer number of these files, it is obviously impractical to compress them individually. What's the best way to go about this, is this type of functionality built in to the compression utilities, or is it time for me to buckle down and learn some BASH scripting?

Thanks!

---

### Post by ryanhaigh on 2008-09-18
I don't know if there is a GUI utility that will do what you want but this is all you need for the command line:

```

cd /where/your/files/are
for file in ./*
do
  zip "$file.zip" "$file"
done

```
That will create an individual zip file for each file in the directory.

If you want higher compression add -9 to the zip line.

---

### Post by mb_webguy on 2008-09-18
All archive formats allow multiple files to be included in an archive.  That's sort of the point of an archive.  There are some, such as tar, which don't compress the included files, and so are used in conjunction with some form of compression -- which is why we have tar.gz and tar.bz files.

The Archive Manager (File Roller) included in Ubuntu makes it simple to create a multi-file archive.  Simply open Archive Manager (if you don't see it in the menu, open the terminal and type "file-roller") and click the New button.  Give the archive a name and specify the location where you want the archive created, and select the type of archive you want to create.  File Roller can handle a wide variety of archive formats, depending on what helper applications you have installed on your system.  There are differences between the different formats, but that's not within the scope of this post.  Needless to say, the only one you shouldn't pick is an uncompressed tar, since it obviously uses no compression.

Now, simply open Nautilus and drag the folder containing the files you want to archive to the Archive Manager window.  The folder (and the files it contains) will be added to the archive.  Once you're done, close the Archive Manager window.

EDIT:  I guess I misread your post.  I thought you were saying you *didn't* want to zip them individually....

---

### Post by Starclopsofish on 2008-09-18
Worked like a charm! Thanks!

I'm very interested in becoming more competent in the command line, do you know of a good tutorial to get me started down this path?

---

### Post by ryanhaigh on 2008-09-18
Advanced bash scripting : [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I used that when I needed some bash scripts for a uni project, always a good reference to have around. Other than that I suggest just using the command line for the little things like this and of course you can always try and help people on the forums ;P

---

