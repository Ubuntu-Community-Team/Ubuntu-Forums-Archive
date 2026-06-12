---
title: "Archive manager broken?"
date: 2008-08-30
forum: General Help
---

### Post by MaxIBoy on 2008-08-30
For some reason, I think I got a broken archive manager on my desktop. Works fine on my laptop, but on my desktop I have never been able to successfully extract an archive, not once. 

The following command did not work:
```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install --reinstall archive-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package archive-manager
maxtothemax@maxtothemax-desktop:~$ 

```

How do I either reinstall or replace the archive manager?

---

### Post by mb_webguy on 2008-08-30
> **MaxIBoy said:**
> For some reason, I think I got a broken archive manager on my desktop. Works fine on my laptop, but on my desktop I have never been able to successfully extract an archive, not once. 

The following command did not work:
```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install --reinstall archive-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package archive-manager
maxtothemax@maxtothemax-desktop:~$ 

```

How do I either reinstall or replace the archive manager?

The Archive Manager in Ubuntu is actually called File Roller, as you can see if you go to Help->About in Archive Manager.  You can install it with "sudo apt-get install file-roller".  Also, File Roller can use other applications to open and create certain archive types.  Type "sudo apt-get install p7zip-full p7zip-rar" to be able to work with 7z and rar archives.

---

### Post by MaxIBoy on 2008-08-30
Still doesn't seem to work. Any good replacements out there?

---

### Post by kellemes on 2008-08-30
> **MaxIBoy said:**
> Still doesn't seem to work. Any good replacements out there?

What kind of package are you trying to work with? And what's the message you're getting?

---

### Post by MaxIBoy on 2008-09-01
As an example:

```
[/home/maxtothemax/UrbanTerror_41_FULL.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/maxtothemax/UrbanTerror_41_FULL.zip or
          /home/maxtothemax/UrbanTerror_41_FULL.zip.zip, and cannot find /home/maxtothemax/UrbanTerror_41_FULL.zip.ZIP, period.

```

---

