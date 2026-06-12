---
title: "Samba in Ubuntu 8.04 is a Pain"
date: 2008-10-12
forum: General Help
---

### Post by RealG187 on 2008-10-12
Samba is a real pain. I had to make a new account on my machine to replace my old one, and have to set it up.

I kept on getting net user share errors, until I gave full permissions for some samba shares folder (under /var/lib/somewhere, I think)

Now I am using a default samba file I found online [here]("http://bestwikiever.wikidot.com/Samba") and still have issues. I have kubuntu-desktop package installed and and add or edit shares using "kcmshell fileshare" or from KDE (last I checked I could use Konqueror or Thunar) but not from Gnome (Nautilus)

---

### Post by RealG187 on 2008-10-13
UPDATE:

Okay I get this at first:

> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

I can easily give permissions for /var/lib/samba/usershares (I give to "everyone" and "sambashare")

But the shares dont show up unless I use a KDE app...

---

### Post by darksoul7 on 2008-10-13
I hear you there, RealG187.

I've had some issues with Samba on my laptop which I didn't have on my PC.

I set up the user, I set up the permissions, but every time I try to connect to the laptop from the Windows machine, it says permission denied. 

The user name and passwords are correctly spelled and entered. 

The machine is seen by all Windows machines on the network. 

Any help would be appreciated.

---

### Post by Dirty Ole on 2008-10-13
Install a package called system-config-samba. It eases out the pain a bit.

---

