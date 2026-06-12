---
title: "Samba automatically creating backup files?"
date: 2008-09-22
forum: General Help
---

### Post by Znupi on 2008-09-22
I used the how-to here: [http://ubuntuforums.org/showthread.php?t=255872](http://ubuntuforums.org/showthread.php?t=255872) to permanently mount a samba share and provide read/write access to it. My problem is that whenever I open up a file on the server, modify it and save it with gedit (no, it's not set to create backup files before saving), the file does change, but another file named "cifsxxxx" (where xxxx are digits) appears in the same folder and holds the contents of the file before being saved. Because of the naming of the files, I believe this has something to do either with the samba server (which is Xubuntu 7.10, I think) or the samba client on my machine (Ubuntu 8.04).

Anyone else came across this? Is there some way to prevent the backup files from being created?

---

### Post by Znupi on 2008-09-24
Anyone? Please? :-(

---

### Post by Znupi on 2008-09-28
Bump.. :(

---

### Post by andy.stallwood on 2008-11-11
Hi Znupi,
I have exactly the same problem. It only seems to have started on Intrepid (8.10) for me, but I did update my Debian CIFS server at exactly the same time (I know, bad move. I'd never do 2 upgrades at the same time at work, so I've no idea why I did it at home), so it could be because of that upgrade as well.

Did you find a fix for this?

Andy

---

### Post by Znupi on 2008-11-12
Well, not really. The only fix I found was use ssh for file sharing since it's an open. safer standard and it was also already installed on the server. Another plus is that I don't need to mount the ssh share in order to write to it, so I just keep a bookmark tagged "Server" and connect to it whenever I need to.

---

