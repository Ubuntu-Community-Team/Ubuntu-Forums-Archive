---
title: "[SOLVED] transfering firefox book marks"
date: 2008-08-08
forum: General Help
---

### Post by jimi_hendrix on 2008-08-08
how can i transfer my firefox book marks from windows to linux

---

### Post by todak on 2008-08-08
Bookmarks> Organize Bookmarks. In the window that appears select the "Import and Backup" menu item. Then select "Export HTML" and choose a removable drive to store the file. In Ubuntu, go through the same thing in Firefox , except choose "Import HTML" and point to the file you created under windows!:)

---

### Post by DJ_Peng on 2008-08-08
You can also check [Moving from Windows to Linux]("http://kb.mozillazine.org/Moving_from_Windows_to_Linux") on the mozillaZine Knowledge Base

---

### Post by SeanBlader on 2008-08-08
Use the plugin for Firefox called Foxmarks. I use it to sync my Firefox bookmarks between 5 different systems, and it will work on any firefox regardless of OS.

---

### Post by DJ_Peng on 2008-08-10
That will work, but it's a bit of overkill is you simply want to migrate your profile from one OS to another. Hopefully Mozilla will find a way to let Weave/Prism backup your entire profile one day.

---

### Post by hyper_ch on 2008-08-10
you can copy just your whole windows ff profile folder to linux.

---

### Post by ragflan on 2008-08-10
Yup, do that. Transfer your entire FF profile from Windows to Ubuntu instead of just your bookmarks (if you prefer). 

Open up the run command in Windows (Windows Key + R)
Type **%appdata%** and press enter. 
Find the folder named 'Mozilla'. 
Open Mozilla folder.
Open Firefox folder.
Open Profile folder.
Open **your profile (example: 4v0fyxaa.default) ** folder. 
Copy the contents of that folder or package it into a zip file.


Under Ubuntu:
Open your Home folder.
Click on View -> Show Hidden Files. 
Open Mozilla Folder.
Open Firefox Folder.
Open Profile Folder.
Open **your profile** folder and paste your windows Firefox profile contents here or extract the package here.

If you have some Windows-only Addons like PicLens, they won't work on Ubuntu, but everything else should be just fine.

---

### Post by alienexplorers on 2008-08-11
If you have a floppy drive copy the bookmarks to it then reload them in Ubuntu.  You can also do the same with a USB flash drive.

---

