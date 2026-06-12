---
title: "How to edit .jar Manifest file?"
date: 2008-09-16
forum: General Help
---

### Post by dror_trieman on 2008-09-16
Hi all,

How can I edit a jar Manifest file?

If I uses the archive manager I can't edit the file only read it.

Anyone?


Good Day :)

---

### Post by quibbler on 2008-09-16
> **dror_trieman said:**
> Hi all,

How can I edit a jar Manifest file?

If I uses the archive manager I can't edit the file only read it.

Anyone?


Good Day :)
winrar with wine?? should work.

Regards quibbler

---

### Post by jespdj on 2008-09-16
1. Make sure you have a JDK (Java Development Kit) installed:
```
sudo apt-get install sun-java6-jdk
```

2. Use the [JAR tool](http://java.sun.com/javase/6/docs/technotes/tools/solaris/jar.html) to extract the manifest file:
```
jar xf myfile.jar META-INF/MANIFEST.MF
```

3. Edit the manifest file with your favourite text editor.

4. Put the modified manifest file back:
```
jar uf myfile.jar META-INF/MANIFEST.MF
```

---

