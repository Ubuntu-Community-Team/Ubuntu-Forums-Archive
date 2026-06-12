---
title: "Help me / network folders?"
date: 2008-09-11
forum: General Help
---

### Post by Danon132 on 2008-09-11
Is there a folder where i can see the ohter computers on the same internet, and then share files etc?

Greets:)

---

### Post by ilovelinux33467 on 2008-09-11
Yes you can. Look here:
[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")

Or Here:
[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/")

---

### Post by mb_webguy on 2008-09-11
Places->Network should show you the computers on your local network.  However, if you're talking about Windows computers, you must have samba installed.  Samba allows Linux computers to connect to Windows networks.  I'm not sure whether it's installed by default.  If you don't have a menu item called "Samba" in you System->Administration menu, open the terminal and type "sudo apt-get install system-config-samba".  This will install a GUI interface to configure samba -- and samba itself if it's not already installed.

You might have to log out of your session or restart to get samba running.  Afterward, you should be able to open Places->Network, and see an icon for Windows Network if there are any Windows computers on your local network.  You can use System->Administration->Samba to change your Windows workgroup, as well as to manage any shared folders.

Edit:  Following the instructions in ILoveLinux33467's post will also install Samba, but I don't think it will give you the GUI configuration tool in System->Administration.  It's arguably an easier way to go, though.

---

### Post by Danon132 on 2008-09-11
I havent istalled Samba but i can see the ohter computers;)
Thanks for the help:)

---

### Post by gvartser on 2008-09-11
> **Danon132 said:**
> I havent istalled Samba but i can see the ohter computers;)
Thanks for the help:)

The client part is installed by default, its only the server part that you have to manually install. That is if you want to share stuff on your comp with other windblows machines.

/g

---

