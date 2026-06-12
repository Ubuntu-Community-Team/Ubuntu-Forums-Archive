---
title: "[SOLVED] problem with package manager"
date: 2008-09-13
forum: General Help
---

### Post by Ariuk on 2008-09-13
Hi all,i'm a linux's beginner and i 'll explain my problem. I have ubuntu hardy installed on my pc,and it never do problems to me.Yesterday when i was opening package manager it displayed this problem

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Il tipo '“deb' non è riconosciuto alla linea 1 nella lista sorgenti /etc/apt/sources.list.d/vlc.list, E:La lista dei sorgenti non può essere letta.' "

I can't do update  and i don't know why,can you help me please?
Thank you for your disponibility and your help

---

### Post by Pro-reason on 2008-09-13
It's complaining about an extra repository that you added.  

Please tell me the output of this command:

```

cat /etc/apt/sources.list.d/vlc.list

```

That will allow me to know what to do to fix it.

---

### Post by Ariuk on 2008-09-13
first of all thanks for your help

when i digit that line,it appears:

“deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) hardy universe”

---

### Post by quibbler on 2008-09-13
> **Ariuk said:**
> Hi all,i'm a linux's beginner and i 'll explain my problem. I have ubuntu hardy installed on my pc,and it never do problems to me.Yesterday when i was opening package manager it displayed this problem

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Il tipo '“deb' non è riconosciuto alla linea 1 nella lista sorgenti /etc/apt/sources.list.d/vlc.list, E:La lista dei sorgenti non può essere letta.' "

I can't do update  and i don't know why,can you help me please?
Thank you for your disponibility and your help
Go to System-Administration-Software Sources
click on third party software
and look for entries that have vlc in them and uncheck those.
Try update again and see if that helps.

Regards quibbler

---

### Post by Ariuk on 2008-09-13
> **quibbler said:**
> Go to System-Administration-Software Sources
click on third party software
and look for entries that have vlc in them and uncheck those.
Try update again and see if that helps.

Regards quibbler

There are 3 marked 
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)               free non free
[http://ppa.launchpad.net/thielmann/ubuntu](http://ppa.launchpad.net/thielmann/ubuntu)   main
[http://ppa.launchpad.net/thielmann/ubuntu](http://ppa.launchpad.net/thielmann/ubuntu)   main(source code)

i'm very sorry but i'm newbie and i don't know much about it..

---

### Post by Pro-reason on 2008-09-13
> **Ariuk said:**
> first of all thanks for your help

when i digit that line,it appears:

“deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) hardy universe”

I suspect that the problem is that you included the quotation marks around that text.

Go to the command line, and type “*gksu gedit /etc/apt/sources.list.d/vlc.list*” (without the quotation marks, obviously).

Check that the file contains no quotation marks.  Save and close.

---

### Post by Ariuk on 2008-09-13
YEs,there were quotation mark,i leave them and i have resolved the problem,thank you very much!

---

### Post by Pro-reason on 2008-09-13
> **Ariuk said:**
> YEs,there were quotation mark,i leave them and i have resolved the problem,thank you very much!

*Lieto di aver potuto aiutarti.*

Perhaps you could click on the “Thread Tools” menu to mark this as “Solved”.

---

