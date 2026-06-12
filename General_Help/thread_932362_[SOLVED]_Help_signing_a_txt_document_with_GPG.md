---
title: "[SOLVED] Help signing a txt document with GPG"
date: 2008-09-28
forum: General Help
---

### Post by NewJack on 2008-09-28
I am trying to sign the Ubuntu Code of Conduct to add to my Launchpad account.  I downloaded the "UbuntuCodeofConduct-1.0.1.txt" to my desktop.  When I attempt to sign it using the following command:

$ gpg --clearsign UbuntuCodeofConduct-1.0.1.txt

I get the following output in the Terminal:

gpg: can't open `UbuntuCodeofConduct-1.0.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.0.1.txt: clearsign failed: file open error

Is there a problem with clearsign?  Am I doing something wrong?  Is there a way for me to sign the .txt file another way?  Any help is appreciated.  Thanks

Joe

Oh P.S.- My PGP key shows up as "REGISTERED" on my Launchpad account.

---

### Post by Elfy on 2008-09-28
at a guess I'd say that the file is on the desktop and your terminal isn't. Try ```
cd Desktop
``` then run the gpg --clearsign command again

---

### Post by spiderbatdad on 2008-09-28
add your key to seahorse...and yes to what forestpixie wrote

---

### Post by NewJack on 2008-09-28
Oh, do I feel silly. Forgot to cd to Desktop each time.  Guess that is what happens when you are only on 3 hours sleep. 

Thanks guys, sorry to bother you.  

<<< /at me    :lolflag:

---

