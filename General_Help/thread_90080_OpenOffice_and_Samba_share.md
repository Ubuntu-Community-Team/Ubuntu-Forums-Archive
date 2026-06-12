---
title: "OpenOffice and Samba share"
date: 2005-11-14
forum: General Help
---

### Post by ubuntutinger on 2005-11-14
I just installed Kubuntu 5.10. Sorting out problems on network printing, etc. A few steps close to complete a working machine. 

Now, I try to open a doc file from networked Window 2K box. Kubuntu asked me if I wanted to open with OpenOffice.org2 Writer. I clicked and saw program is loading, jumping icon. Then, the icon dissapeared. Nothing loaded nothing happened. Tried a few times. Just won't work. Opened OpenOffice.org2 Writer. Tried to use open file. It only show local files. Anyone know how to get the remote doc file opened?

---

### Post by Takis on 2005-11-14
I'm not sure whether OO has support for KIO, KDE's system for file I/O (e.g. file:/, ftp:/, fish:/, smb:/, etc). You may like to copy it to your local system, edit it and then copy it back.

---

### Post by ubuntutinger on 2005-11-14
[QUOTE=Takis]I'm not sure whether OO has support for KIO, KDE's system for file I/O (e.g. file:/, ftp:/, fish:/, smb:/, etc). You may like to copy it to your local system, edit it and then copy it back.[/QUOTE]

Hi Takis,

I am pretty green in Linux. Could you explain more on  how to do it?  Which file(s) need to be edited? Thanks,

---

### Post by Takis on 2005-11-17
Sorry I may have complicated matters. Do you know how to access Windows files and folders from your Linux box? There should be no file editing involved. If you do, all I meant was copy the file from Windows to somewhere on your Ubuntu box (in your home directory's probably the best place). Then you'll be able to open it in OpenOffice. When you've done what you wanted to do, save it and copy it back.

If you don't know how to access your Windows shares through KDE, post and I'll guide you through it.

---

### Post by ubuntutinger on 2005-11-17
[QUOTE=Takis]Sorry I may have complicated matters. Do you know how to access Windows files and folders from your Linux box? There should be no file editing involved. If you do, all I meant was copy the file from Windows to somewhere on your Ubuntu box (in your home directory's probably the best place). Then you'll be able to open it in OpenOffice. When you've done what you wanted to do, save it and copy it back.

If you don't know how to access your Windows shares through KDE, post and I'll guide you through it.[/QUOTE]

Ya, I know copy Windows files to Linux box and OO can work on it. But, my intention is to double click remote file from Linux box and hope OO can open it and start edit. Just like the Windows Box normally perform when opened a remote file from another Windows file in the LAN. I guess I did not make my question clear enough. Thank you,

---

### Post by randcoop on 2005-11-18
You can't do what you want from smb: in Konqueror.  However, you can if you mount the Windows share as smbfs.  First, make sure you've got smbfs installed (sudo apt-get install smbfs).  Then, create a mount point in /mnt (sudo mkdir /mnt/[mount point name]).

Once that mount point exists, mount the share with:

sudo mount -t smbfs //[Windows Name]/[Share Name] /mnt/[mount point]

Once a share is mounted, then it can be seen in Konqueror and will automatically open in OpenOffice when clicked.

---

