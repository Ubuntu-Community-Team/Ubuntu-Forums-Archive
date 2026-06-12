---
title: "How to uninstall ubuntu 7.10"
date: 2008-08-22
forum: General Help
---

### Post by joruss1 on 2008-08-22
I have Ubuntu 7.10 installed and could not connect to the internet to upgrade to 8.04.  So I downloaded 8.04 ISO file from windows, always connects, and checked the hash is OK, and burned the CD.  It would not install under Ubuntu 7.10.  So I went back to windows and installed it with Wubi and it works OK and I can connect to the net.

My problem is I still get the 7.10 multi boot screen with XP and when I select XP, I get another boot screen to choose Xp or Ubuntu.  If I display boot.ini it only shows the Wubi version.  Where is the other file with 7.10?  How do I get rid of version 7.10?  Is it buried some where in ntldr?

---

### Post by Lusse on 2008-08-22
The first menu you see is grub...

My suggestion would be to first unistall ubuntu 8.04 then open up any partion-editor(for example gparted) and then remove every partition exccept the windows one(ntfs). When thats done boot of the ubuntu 8.04 cd and install that to the "largest free space" on the harddrive.

//Linus

---

### Post by Lusse on 2008-08-22
Or...

If you are happy running ubuntu from wubi u can run mbrfix from the windows rescue-cd or *maybe* you can run it from inside windows, just try and see if the command exists...

//Linus

---

