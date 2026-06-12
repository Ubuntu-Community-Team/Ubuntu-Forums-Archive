---
title: "I'm having the sun-java6.doc prob."
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by missbliss on 2009-03-12
I was trying to install Java and I don't really know what I did but now it keeps telling me that I need to install the jdk6.doc, but I do and then I can't seem to figure out what else to do with it.  I have unzipped it and copied in to the /tmp file, and done restarts.


Anyway, now whenever I do updates of any sort I get that error message along with "press no + return" to abort which I do and most of programs install fine anyway (actually, I think all of them).  However I still want Java.  

I get this message after I abort:

```
E: sun-java6-doc: subprocess post-installation script returned error exit status 1
```


Here is what I get when I do the -f install command:
```
sarah@sarah-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
```

That's what prompted me to download jdk6.doc and copy it in to the /tmp folder.




Help?

---

### Post by missbliss on 2009-03-12
Nuttin'?

---

### Post by Neo_The_User on 2009-03-12
Install the docs via java website. Use the sun download manager. it unpacks everything for you. theres a simple guide on how to do it.

---

