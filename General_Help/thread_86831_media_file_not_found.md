---
title: "media file not found"
date: 2005-11-06
forum: General Help
---

### Post by styven on 2005-11-06
Hi all,

When i insert my sd memory card, i get the following error message in Konqueror...

An error occurred while loading media:/sdc1:
The file or folder media:/sdc1 does not exist.

I did a search and a file exists called /dev/sdc1, this file is owned by "root" and i can do nothing with it.

Is it the case that if i owned this folder it would load when i put my card in, and would i then be able to see the contents?

Currently, i have to go via, storage, hda1, media, usbdisk to veiw the contents, which is not ideal.

Should i not be able to sign in at the log in screen as root and change the permissions of this file, cause as it stands i can't.

I have tried going via disk & filesystems to "enable" this particular drive, but no go.
I do now have extra drives appear in storage media, but they are shown as hard disk sdc, not removable media. I have tried to mount these, but get a message saying only root can do this.
How do change this permission also? 

steve

---

### Post by daller on 2005-11-14
Does opening "/media/sdc1" work?

...I had a lot of my problems solved by upgrading to KDE3.5

See [www.kubuntu.org](www.kubuntu.org), on how to do so...

---

