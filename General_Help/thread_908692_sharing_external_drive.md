---
title: "sharing external drive"
date: 2008-09-02
forum: General Help
---

### Post by lgdadmdc on 2008-09-02
I have a music folder on an external drive that I want to share over our home network, but when I try I get this error: 

'net usershare' returned error 255: net usershare add: cannot share path /media/My Book/music as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only = False" 
to the [global] section of the smb.conf to allow this.

how do I do this? I have no idea how to login as root, and when I try to add this line in the smb.conf it tells me I don't have permission.....

someone please help!!!!

---

### Post by NoWayBill on 2008-09-02
I find it much easier to move around in a GUI than in terminal.

The way I get around root permissions is to enter..
**sudo nautilus** or **kdesu konqueror** (if using KDE desktop) into console.

Now every file you open with Nautilus will be as root, now the power is yours.

Or, **sudo gedit /path/to/smb.conf**

---

