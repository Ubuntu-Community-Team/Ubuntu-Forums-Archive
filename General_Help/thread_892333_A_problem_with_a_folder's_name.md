---
title: "A problem with a folder's name"
date: 2008-08-17
forum: General Help
---

### Post by sumwonyuno on 2008-08-17
Background info:
I bought a new laptop, and I have Vista and 64-bit Hardy on it.  I have a desktop w/ 32-bit Hardy and an (NTFS) external w/ my storage on it.  Today, I copied the files on my external to an NTFS partition on the laptop.

I'm having problems with a character in a folder name. This occurs in terminal (dir), Nautilus (normal view and properties) and any other program that tries to read a string with the character.  Curiously, the songs in the folder can play in mpd (folder name's characters were invisible when invoking mpd --create-db).  In Guimup, the text is blank for album name and all text after it.

[pictures removed]

Other folder names proceeding the suspect folder were "fixed" after reselecting with the mouse.

The folder name is the title of a song album.  I can see the title in its Wikipedia page, but Firefox freezes when I try to paste the text...

[IMG]http://img179.imageshack.us/img179/1756/ss4ki8.png[/IMG]
[screen shot of page]

I believe the second Japanese character is the culprit.  I don't think I have any other folders or files with that character.  There doesn't seem to be any other folder or file that have this issue.

Both folder copies on the internal and external have this problem in 64-bit.  I tried the external back on the desktop and the folder is fine.  In Vista, the folder on the internal is fine as well.

[EDIT] Problem fixed; possibly due to install of Japanese language pack, or upgrading/reinstalling packages

---

