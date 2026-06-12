---
title: "[SOLVED] Uninstalling a program not recognized by termanal or synaptic"
date: 2008-12-01
forum: General Help
---

### Post by lyceum on 2008-12-01
I installed NetBeans 6.5, but terminal does not see it and neither does SPM, I am guessing it is because it was not deb install? How do I get rid of it? Any ideas?

Thanks!

---

### Post by taurus on 2008-12-01
How did you install it (what method)?

---

### Post by sujoy on 2008-12-01
i am guessing it installed wrongly or the installed location is outside of the $PATH

---

### Post by drs305 on 2008-12-01
What taurus was asking was did you install it by compiling it yourself (extracting a folder from a from a .tar.gz file), etc. You may have executed a .bin file, a .run file or something else.

If you compiled it yourself you may/should still have a folder that was created when you extracted the files from the compressed file (tar.gz). Inside that folder you may find a "postinst" folder. Within may be a "postinst.sh" file which will run a removal script or perhaps a readme file on how to remove the application.

If possible you don't want to just delete individual files. Try to find the removal instructions as noted above or visit the maintainer's site. If all that fails, you may get an idea of where the files reside by running the following command (although this information may come from apt/dpkg and might not be available for a self-installed program):
```
whereis *appname*
```

---

### Post by lyceum on 2008-12-03
Sorry, I was taken away from my computer for a few days, but I installed it with:

chmod +x netbeans-6.5-ml-java-linux.sh

./netbeans-6.5-ml-java-linux.sh


The odd thing is that the first time I installed Netbeans I could add rubygems, but it did not recognise gem 1.3.1. I tried to re-install it, and I thought it worked, but then I could no longer install new gems w/out root password, which I do not have and my normal password did not work, so I though I would re-install again, but now it just says that it is installed, so I do not know if I installed to twice or what. I would like to know how to do this, but maybe the question I should be asking is how do I set my root password so I can add gems through NetBeans?

---

### Post by lyceum on 2008-12-03
> **drs305 said:**
> What taurus was asking was did you install it by compiling it yourself (extracting a folder from a from a .tar.gz file), etc. You may have executed a .bin file, a .run file or something else.

If you compiled it yourself you may/should still have a folder that was created when you extracted the files from the compressed file (tar.gz). Inside that folder you may find a "postinst" folder. Within may be a "postinst.sh" file which will run a removal script or perhaps a readme file on how to remove the application.

If possible you don't want to just delete individual files. Try to find the removal instructions as noted above or visit the maintainer's site. If all that fails, you may get an idea of where the files reside by running the following command (although this information may come from apt/dpkg and might not be available for a self-installed program):
```
whereis *appname*
```

Found it, but sadly I did not find uninstall instructions. I checked Google again, the best I found was my own thread :)

Thanks though!

---

### Post by lyceum on 2008-12-04
* bump

---

### Post by taurus on 2008-12-04
I believe there is an uninstall.sh in the newly created directory.  You can run that program to uninstall it.  Do you know where it's installed?

```
sudo find / -name netbeans* -print
-or-
sudo find / -name *netbean* -print
```

---

### Post by lyceum on 2008-12-04
> **taurus said:**
> I believe there is an uninstall.sh in the newly created directory.  You can run that program to uninstall it.  Do you know where it's installed?

```
sudo find / -name netbeans* -print
-or-
sudo find / -name *netbean* -print
```

That worked, I found it: 

/usr/local/netbeans-6.5/uninstall.sh

how do I run it? ./netbean-6.5-uninstall.sh?

-edit- 

I tried that and it did not work :(

---

### Post by taurus on 2008-12-04
Don't forget the sudo.

```
sudo /usr/local/netbeans-6.5/uninstall.sh
-or-
cd /usr/local/netbeans-6.5
sudo ./uninstall.sh
```

---

### Post by lyceum on 2008-12-04
> **taurus said:**
> Don't forget the sudo.

```
sudo /usr/local/netbeans-6.5/uninstall.sh
-or-
cd /usr/local/netbeans-6.5
sudo ./uninstall.sh
```

duh! Thanks!!

:guitar:

---

