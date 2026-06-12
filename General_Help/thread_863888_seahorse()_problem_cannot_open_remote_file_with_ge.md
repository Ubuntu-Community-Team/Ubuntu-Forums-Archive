---
title: "seahorse(?) problem: cannot open remote file with geany"
date: 2008-07-18
forum: General Help
---

### Post by bs0d on 2008-07-18
Hi

I connect from my desktop to notebook over sftp (click on bookmark in nautilus) and edit scripts with geany remotely. Sometimes I cannot open files on remote machine with geany: if I right click on the file which I am trying to open I see "open with text editor" instead of "open with geany" despite in "open with.." dialog geany set as default handler for these scripts. If I open Seahorse , tab password, I see my saved password for remote machine, click properties, go to application tab and there are only seahorse, gedit and sftp filesystem service listed , but not geany?

So my supposition is that geany cannot access password to open the file. I can be wrong. From other side, gvfs should open the remote connection over sftp and geany do the opening with help of gvfs. 

If I open geany and then file->recent file and try to open the remote file I get error message in geany's status bar: Could not open file /home/user/.gvfs/sftp on192.168.1.100/home/user/folder/file.pl (No such file or directory)

I don't know, where to look for the cause of this problem.

I can open with gedit but if I try open with other application and choose geany - geany popups but without to open the file.

I don't know if it is a bug or misconfiguration.

Where are the settings for seahorse stored? Can I edit them to add geany manually?

other ideas?

thanks

---

### Post by Vadi on 2009-01-18
Try the latest version from here: [http://www.getdeb.net/search.php?keywords=geany](http://www.getdeb.net/search.php?keywords=geany)

---

