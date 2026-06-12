---
title: "[SOLVED] All my files became text files."
date: 2008-07-23
forum: General Help
---

### Post by lvlo on 2008-07-23
Hi.

After playing with new Beagle 0.3.8 (witch I installed with "make install") and Brasero 0.8.0 (with I installed with checkinstall and then uninstaled it) all my files became a text files. Just don't know where begin to solve a problem.

Thank you for your time.

---

### Post by Habbit on 2008-07-23
What do you mean with "all your files become text files"? Could you be a bit more specific and/or put some example?

---

### Post by lvlo on 2008-07-23
> **Habbit said:**
> What do you mean with "all your files become text files"? Could you be a bit more specific and/or put some example?

I mean that all my files became associated to Gedit and Open Office.

Here is a screenshot:
[IMG]http://ubuntuforums.org/picture.php?albumid=378&pictureid=1240[/IMG]

---

### Post by Habbit on 2008-07-23
File associations seem to be stored in .xml files within the following routes:

/usr/share/mime (system-wide standard location)
/usr/local/share/mime (place where programs install "override" files to add themselves)

Check whether any of those locations, particularly the last one (which should be empty) has any strange file, redirecting everything to text.

Another possibility is that the file type _recognition_ has been messed up, so GNOME is recognizing everything as MIME type text/plain. In that case, I don't really know what to do: try reinstalling the "file", "libmagic" and "libmagic1" packages.

---

### Post by lvlo on 2008-07-23
Oof!.. :KS Problem was solved by simple command:
```
sudo update-mime-database /usr/share/mime
```

Thanks for your attention.

---

