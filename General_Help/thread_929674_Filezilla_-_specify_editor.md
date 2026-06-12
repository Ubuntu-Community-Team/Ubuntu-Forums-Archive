---
title: "Filezilla - specify editor"
date: 2008-09-25
forum: General Help
---

### Post by Guardian2008 on 2008-09-25
I have searched here for hours but so far have come up empty handed so I'm hoping someone will help me out with this small problem.
Please bear in mind I have been using Ubnutu for less than two days :)

I have installed Filzilla as I used to use it under Windows and under the Filezilla preferences I can specify which 'editor' I would like to have open files for editing.
As I have Jedit installed, that is what I would like to use but I don't seem to be able to find a 'correct' path to insert to get it to work.

Would anyone know what the correct file/path would be and/or if I need to add any additional arguments like '-open' to the path?

---

### Post by zajc on 2008-09-25
Go to menu

```
Edit
Settings
File editing
Default editor --> /usr/bin/gedit
```

---

### Post by Guardian2008 on 2008-09-25
Thanks for taking the time to reply.

I tried that and then also navigated to the file in case I had made a typo or something and if I either double click a file in Filezilla's 'local file' window or right click->edit all I get is a bleep and nothing else happens.

I tried both the options;
Use filetype associations if available
Use default editor

I closed and restarted Filezilla between each attempt but no joy - how frustrating.

---

### Post by Badjaccur on 2010-01-07
Seems like this problem is still there.
I'm using Nautilus now, Ubuntu's standard filebrowser. Just type the path in the adressbar like this: [ftp://username@hostname](ftp://username@hostname)
Gnome's keychain can remember the password if you like. At the moment Nautilus can only do passive FTP though... :(

---

### Post by Guardian2008 on 2010-01-07
The problem seemed to have resolved itself so maybe my initial issue was due to file access permissions of something but
/usr/bin/jedit
works for me without problems

---

### Post by danielelias22 on 2011-05-15
> **zajc said:**
> Go to menu

```
Edit
Settings
File editing
Default editor --> /usr/bin/gedit
```

Thanks for your time&help.

Daniel

---

