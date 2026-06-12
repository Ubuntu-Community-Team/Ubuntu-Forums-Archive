---
title: "[SOLVED] TortoiseSVN equivilent?"
date: 2008-10-25
forum: General Help
---

### Post by blis102 on 2008-10-25
Hello everyone,

I have been looking around for a TortoiseSVN equivilent, but have not had much luck. 

Currently I am using **kdesvn** on Ubuntu 8.04 which is a nice program but since it is an application, it is somewhat inconvenient for me to use (am a lazy SOB). 

I would *love* to be able to open up a file browser, go to some checked out code, and see which files are current (with a check icon, like TortoiseSVN) and which files are out of date (with an "x" or something...) and to have a right-click menu for committing, reverting, etc...

Does anyone know of a program that does this?

Thanks for any suggestions!

---

### Post by geirha on 2008-10-25
Try the [nautilus-script-collection-svn](apt://nautilus-script-collection-svn) package. Once it is installed, do ```
nautilus-script-manager enable Subversion
``` to enable the scripts for your user. When you right-click files you should now have a new menu entry: Script -> Subversion.

---

### Post by blis102 on 2008-10-25
Sweet! That is awesome! Thanks for that!

Now if only it would show icons... :)

Cheers!

---

### Post by blis102 on 2008-10-30
Sort of a bump...

Does anyone know how to get icons to show up in Nautilus that denote whether or not files are current/outdated/etc? It would be ideal to have similar icons compared to TortoiseSVN (maybe even be able to have my own custom icons too...).

Basically I am looking for a clone of TortoiseSVN for Ubuntu :)

I am using kdesvn which is pretty much perfect except its not integrated with Nautilus...

Anyone know where I could find something like this? Any idea how hard it would be to code myself (a simplified version of course...)? Any links, suggestions, tips would be greatly appreciated!

Cheers,
D

---

### Post by blis102 on 2008-10-31
I have found out about NautilusSVN which is about as close as you can come to TortoiseSVN.

[http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/)

Check the "Issues" tab about installing on 8.04 because you need to move some files over.

Hope that helps someone!

Cheers,
D

---

### Post by jwdonal on 2010-12-15
A clone of the tortoise tools is now available for Linux for many distributions which resolves all of the issues I have seen mentioned here.  It's called RabbitVCS ([http://rabbitvcs.org/](http://rabbitvcs.org/)).  Linux users have been asking for a tool like this for as long as I can remember, so please broadcast news of this excellent tool to the numerous forum threads (not just for ubuntu) where people are all asking the same question.

You're welcome. :)

---

### Post by Lilonius on 2011-03-20
RabbitVCS is good for small repositories, but useless for big ones. It can take minutes just to browse from one folder to another. I would not call this thread as SOLVED.

---

