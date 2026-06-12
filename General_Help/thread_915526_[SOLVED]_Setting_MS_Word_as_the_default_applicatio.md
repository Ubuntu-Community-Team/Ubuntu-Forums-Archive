---
title: "[SOLVED] Setting MS Word as the default application"
date: 2008-09-09
forum: General Help
---

### Post by Victormd on 2008-09-09
I know this thread has appeared before, I've seen it a long time ago but can't find it...

I'm trying to set MS Word as the default application for documents in Ubuntu (I already have it working under wine with no problem). Has anyone been able to do this?

This is on my wife's laptop and she didn't like or didn't want to use OpenOffice Word Processor so in an attempt to keep her from going back to windows, here I am... :)

---

### Post by wenuswilson on 2008-09-09
Right click on a .doc file and do properties and open with.
I don't have MS Word so I don't what (if anything) further to do.

---

### Post by ad_267 on 2008-09-09
Edit: Sorry that doesn't work.

Found a thread here though: [http://ubuntuforums.org/showthread.php?t=586846](http://ubuntuforums.org/showthread.php?t=586846)

---

### Post by Victormd on 2008-09-10
> **wenuswilson said:**
> Right click on a .doc file and do properties and open with.
I don't have MS Word so I don't what (if anything) further to do.

That doesn't work because word is running through wine. Ultimately, double clicking on the document will open word but not the file. There is a wildcard that you need to add and that's what I don't remember... :)

---

### Post by Victormd on 2008-09-10
> **ad_267 said:**
> Edit: Sorry that doesn't work.

Found a thread here though: [http://ubuntuforums.org/showthread.php?t=586846](http://ubuntuforums.org/showthread.php?t=586846)

Thanks, there was was a script in this thread that did the trick. If anyone else needs it, here it is:
```
#!/bin/sh
wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE" `winepath -w "$@"`
```

Just create this script and then set the script as the default application! :)

---

