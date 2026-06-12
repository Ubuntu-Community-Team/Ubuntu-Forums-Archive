---
title: "how to password protect a file?"
date: 2008-10-10
forum: General Help
---

### Post by elidoperezmd on 2008-10-10
i think the question is pretty clear, how can i protect a file or folder with a password?


thanks for reading

---

### Post by spiderbatdad on 2008-10-10
I can only think of a couple of ways to do this. You can create an open pgp key for yourself and then use the encrypt option that appears in the menu when you right click the file. Once you have the encrypted file...you would delete the original. Now your pgp key would be needed to decrypt the file...this is very secure, and relatively easy, once you get past the learning curve of using gnu privacy guard for the first time, and adding your key to seahorse.

The other option i can think of is to sudo chown root:root yourFile.ext, then change the permissions: sudo chmod 600 yourFile.ext. Now only someone who know the administrator password can view the file with sudo cat yourFile.ext from a command line interface.

---

### Post by Sam on 2008-10-10
Or you can encrypt a whole directory with a password. There is a lot of tutorials about it (or wait for the next version of Ubuntu (19 days) which has this feature by default).


If it's to share to someone, you can make a password protected zip archive. However this is not the most secure option.

---

### Post by bodhi.zazen on 2008-10-10
There is no easy way to do this, but security is different on Linux.

The first layer of security is Permissions. If a user does not have permissions he or she can not read your file, password or no.

The easiest way to password protect a file or directory is , IMO, encryption. There are several options for encryption and IMO the easiest to use is Truecrypt.

[uhelp]community/FilePermissions[/uhelp]

[http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10](http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10)

8.10 uses encfs

[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)

You can also go with LUKS

[http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks)

---

### Post by kevdog on 2008-10-17
You can use Gnupg (sometimes known as gpg) with the --symmetric option that can encrypt a file protecting it with only a password.

If you need help with the syntax (since this is an old thread), please respond and I can rapidly help you!

---

### Post by Dr Small on 2008-10-17
> **kevdog said:**
> (since this is an old thread)
Aha! This is a first... A self-admitted necromancer. I wonder how the B0rg will handle this one. :p

Anyhow, Kevdog is correct. If you want to password protect a file, GPG is your best bet. I prefer Keybased encryption, but that's just my personal choice. Symmetric encryption with GPG is also very good.

Dr Small

---

### Post by kevdog on 2008-10-18
> A self-admitted necromancer

Hey a week old thread isn't that old.  I mean rigamortis has barely set in at this point.

---

