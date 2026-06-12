---
title: "FTP Program with Built-in Editor (Does it Exist?)"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by kestal on 2009-08-10
So I have been on Ubuntu for a while, and I think I may be overlooking something obvious, but I cannot be quite sure.

For Windows, there is a program called CuteFTP which is a simple ftp editor with a built-in HTML/php editor that can be tabbed with as many tabs/html pages needed, and saved dynamically in the place they were edited from.

Is there a program, like this, on Ubuntu?

I know that might be a lot to ask as there are a lot of decent ftp programs, but all of which require downloading, editing, uploading, downloading, etc. CuteFTP made it so that you could select a document on the live section of a site and edit it, and just save (so it was automatically saved to the live section - rather than downloading, editing, uploading, etc).

Not sure if that makes sense or not... Its not much of a difference, but its an extra step that I tend to feel weird working with. CuteFTP is Wine compatible to an extent, but saved has their local drive set up to the local 'wine' drive, rather than Ubuntu. I'd wish to save my xampp on a local folder off of my desktop (from Ubuntu, rather than the virtual drive in wine), rather than setting a directory in Wine - to avoid messy things)

---

### Post by callan79 on 2009-08-10
> **kestal said:**
> For Windows, there is a program called CuteFTP which is a simple ftp editor with a built-in HTML/php editor that can be tabbed with as many tabs/html pages needed, and saved dynamically in the place they were edited from.


Hi kestal,

I'm not sure how much success you'd have editing multiple files on the fly, but I can tell you that editing one file at a time works fine.

Just install Filezilla or gFTP, configure 'gedit' as the editor, and you'll be right. When you save the file and close gedit, the FTP program will upload the new file to the server.

I do this all the time and it works well. Filezilla works better than gFTP in my experience.

Cheers
Callan

---

### Post by airtonix on 2009-09-16
> **callan79 said:**
> 
Just install Filezilla or gFTP, configure 'gedit' as the editor, 

You don't even need to use another ftp program.

Nautilus/Gnome handles the ftp via GVFS, and gEdit will benefit from it also.

In nautilus : 

[LIST=1]
[*] open nautilus,
[*]press ctrl + L
[*]type in ftp address
[*]enter authorisation details if required
[*]bookmark the location (ctrl + d)
[/LIST]
In gedit, 

[LIST=1]
[*]press f9
[*]select "Bookmarks" from the dropdown list
[*]select your ftp server you bookmarked in previous phase
[*]????
[*]profit.
[/LIST]

---

