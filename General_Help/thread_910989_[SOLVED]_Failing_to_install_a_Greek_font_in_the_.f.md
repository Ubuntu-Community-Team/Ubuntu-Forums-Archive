---
title: "[SOLVED] Failing to install a Greek font in the .fonts folder"
date: 2008-09-05
forum: General Help
---

### Post by Berean on 2008-09-05
Hi,

Previously, I installed a Greek font in the hidden folder .fonts in my home directory, after installing mscorefonts, using Terminal, and this thread:
[http://ubuntuforums.org/showthread.php?t=817067](http://ubuntuforums.org/showthread.php?t=817067) .  However, I've reinstalled Ubuntu and now can't find the folder .fonts, even after showing hidden files!  Any ideas?  Your help is appreciated, thanks.

---

### Post by Elfy on 2008-09-05
If you didn't have a seperate /home partition then when you reinstalled it was overwritten.

---

### Post by Berean on 2008-09-05
Yes, I understand that: Everything was overwritten as it was a fresh install.  But my original question was where do I find the .fonts folder, after showing hidden files in my home folder?  Once I find the .fonts folder I can simply paste the font into it and it will work.  Any ideas?  Thanks.

---

### Post by FrankVdb on 2008-09-05
Create it and copy your fonts there.

---

### Post by KStorm on 2008-09-05
A more reliable way to install fonts manually is to (as root) insert the fonts into /usr/share/fonts, then do

# mkfontdir
# fc-cache

That outta do it.:KS

---

### Post by Elfy on 2008-09-05
I myself prefer to keep added fonts together in home - I'm more likely to remember they are there when it's time to reinstall :)

---

### Post by Berean on 2008-09-05
Thanks, to you all.  I didn't realise it would be quite that simple!  Everything is working tickety-boo, so I can start writing in my chosen font.  Once again, many thanks.

---

