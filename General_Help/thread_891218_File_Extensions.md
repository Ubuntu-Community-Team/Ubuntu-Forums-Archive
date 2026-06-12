---
title: "File Extensions"
date: 2008-08-15
forum: General Help
---

### Post by Enigmatus on 2008-08-15
Not so much a problem, but is it possible for Ubuntu (and Xubuntu for that matter) to display filenames WITHOUT to the file extension?

i.e. 'Image001' as opposed to 'Image001.jpg'

---

### Post by iaculallad on 2008-08-15
> **Enigmatus said:**
> Not so much a problem, but is it possible for Ubuntu (and Xubuntu for that matter) to display filenames WITHOUT to the file extension?

i.e. 'Image001' as opposed to 'Image001.jpg'

It's one cool feature of Ubuntu, and why would you want to hide the file extensions? Ala-micro$oft? I think if that feature of hiding file extension is available in nautilus, it must have been disabled by default.

---

### Post by Awareness on 2008-08-15
It makes no sense to hide extensions for me either... I always turn it off in windows...

No idea how to hide em, sorry

---

### Post by unutbu on 2008-08-15
Unlike in Windows, there really are no "extensions" in Linux. If a file is named index.html in Linux, that is the file's full name. People speak as though .html is the file extension, but the filesystem itself has no concept of file extension. 

If you really really want, there is a way to remove the extensions from all the files in a directory:
```

cd path/to/directory
rename 's/(.+)\..*/$1/' *
```

This will rename all files in the directory without the extension. 

Nautilus will still recognize file types without the extension, but there are other programs out there  that rely on the extensions to clue them into what type of contents the file contains. So unless you are really sure you want to get rid of them, using the above commands is not recommended.

---

