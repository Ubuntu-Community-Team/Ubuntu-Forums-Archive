---
title: "How to password protect a folder on Linux?"
date: 2008-08-17
forum: General Help
---

### Post by kagashe on 2008-08-17
This question is being asked by many Linux users on various forums. Today I searched on Google and found [this solution on Linuxforums.org]("http://www.linuxforums.org/forum/linux-security/18535-how-can-i-protect-folder-password.html#post557502").

You can password protect a zip file. Proceed as follows:

Create a directory for this experiment, and name it test.
Copy a few files and paste them into this directory so it isn't empty.
Now open a terminal and enter:
$ zip -e -r test test
Enter password:
Verify password:
Delete the directory test.

Now you have a file test.zip which is password protected.

zip with -e option encrypts the contents of the zip archive using a password. This encrypts with standard pkzip encryption which is considered weak.

However, the job of protecting the file is done, because even the root user needs the password or should be a hacker to decrypt.

---

### Post by ioluas on 2008-08-17
Thanks for the effort, but this is not protecting a folder with a password. It's merely compressing a folder into a passworded zip file..
deceptive title dude

---

### Post by Garratt on 2008-08-17
Very nice, shame you cant just pp a folder. i know years ago in windows i was using a program to pp folders, i have no idea what it's called now, but i bet if someone looks hard enuf there should be a linux program to encypt or pp folders.
and ioluas the title is a question not a statement so it's not misleading at all.

---

### Post by ramjet_1953 on 2008-08-17
I've never tried it, but I believe Crypt Manager will allow you to do this.

Here's a link: 

[http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html](http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html)

It looks like they have re-named the package.

Here's another link:

[http://code.google.com/p/crypt-manager/](http://code.google.com/p/crypt-manager/)

Yep!

Works well.
You need to install three packages in the order listed here:

1. conceal_0.0.5-0ubuntu1-all.deb
2. conceal_gtk-0.0.5-0ubuntu1-all.deb
3. nautilus-conceal_0.0.5-0ubuntu1-all.deb

Regards,
Roger :cool:

---

