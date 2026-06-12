---
title: "problems with wine"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Angry_Mushi on 2009-05-15
I've been trying to install a software through wine, in case anyone knows it, it's called mp3Rocket, and this is what it says when I try to execute it: ```
 [/home/zamoritas/Escritorio/jre-6u1-windows-i586-p-s.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/zamoritas/Escritorio/jre-6u1-windows-i586-p-s.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/zamoritas/Escritorio/jre-6u1-windows-i586-p-s.exe or
          /home/zamoritas/Escritorio/jre-6u1-windows-i586-p-s.exe.zip, and cannot find /home/zamoritas/Escritorio/jre-6u1-windows-i586-p-s.exe.ZIP, period.

```

---

### Post by whoop on 2009-05-15
Is jre-6u1-windows-i586-p-s.exe the file you are trying to execute?
Did you run:
```

wine jre-6u1-windows-i586-p-s.exe

```

---

### Post by Mark Phelps on 2009-05-15
If you're going to use Wine you need to familiarize yourself with the CodeWeavers database page where you can search for test results and ratings using your app.

The link is below:

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true")

If you check, you will see there is no listing for MP3Rocket.

---

