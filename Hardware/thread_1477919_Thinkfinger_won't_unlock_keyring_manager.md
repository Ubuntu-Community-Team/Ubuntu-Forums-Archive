---
title: "Thinkfinger won't unlock keyring manager"
date: 2010-05-09
forum: Hardware
---

### Post by cyrus_the_virus on 2010-05-09
Hi,

I've installed Ubuntu 10.04 and the thinkfinger driver for the fingerprint scanner. This works great but there's one problem. When I login 'swiping' my finger the gnome keyring won't be unlocked. This means I've to enter my password for wlan every time.

In the previous versions of Ubuntu I used a workaround for this. I deleted the keyring files (~/.gnome2/keyring). The next time I would login the keyring manager would prompt for a new password and I would enter an empty password. 
For some reason as of 10.04 I'm not prompted for a new password after deleting the keyring files.

So my question is: Is there another way to reset the keyring password?

Regards,
Martijn

---

### Post by P4man on 2010-05-09
applications > accessoiries > passwords and encryption.
Right click the passwords:login and change passwords.

FYI, its not possible to open the keyring with a fingerscanner. The keyring encrypts your passwords on disk, and the encryption key is your password. When you dont enter a password, but your finger, its simply not possible to encrypt and decrypt your passwords with a fuzzy image. 

The only alternative is storing the encryption key somewhere on disk or not encrypting your passwords (ie setting a blank password) neither of which is very secure. Just so you know, anyone with physical access to your machine will be able to retrieve your passwords if you do this!

---

### Post by cyrus_the_virus on 2010-05-09
> **P4man said:**
> applications > accessoiries > passwords and encryption.
Right click the passwords:login and change passwords.

FYI, its not possible to open the keyring with a fingerscanner. The keyring encrypts your passwords on disk, and the encryption key is your password. When you dont enter a password, but your finger, its simply not possible to encrypt and decrypt your passwords with a fuzzy image. 

The only alternative is storing the encryption key somewhere on disk or not encrypting your passwords (ie setting a blank password) neither of which is very secure. Just so you know, anyone with physical access to your machine will be able to retrieve your passwords if you do this!

Thanks for your reply P4man :)

Unfortunately that doesn't work. In the keyring manager application you mentioned my keyring&passwords are not showed (password listbox is empty) when I've logged in using my fingerprint. However when I log in to gnome using my password the keyring will show up.
I've tried to login with my password, then change the keyring password, logout and login again using my fingerprint. But after the 2nd login the keyring is empty and I'm prompted for a wlan password again.

I think I've found a useful bugreport: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/529338]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/529338")
It seems that the keyring password must be the same as the login password otherwise it won't unlock. Unfortunately there's no fix yet. 

Btw, I'm aware of the fact that not using a keyring password means that password are stored in plain text.

---

### Post by P4man on 2010-05-09
good find. Seems like that is your problem indeed, although logging in with a password and then changing the keyring password ought to work. Im not aware off a different way. You can not change the password without opening the keyring first (unless you dont mind losing your passwords, in which case you can probably just delete your -encrypted- keyring).

---

