---
title: "error wrong architecture....and two other questions"
date: 2008-11-07
forum: General Help
---

### Post by jimi_hendrix on 2008-11-07
i keep having this problem fixing, and forgeting it...how do i install a 32 bit package on 64 bit ubuntu

also how do i know if i upgraded to ibex (i uses sys upgrade) and i am having trouble with installing mupen64....i unpacked it but i cd to the folder and do ./configure and there is no script...

---

### Post by drs305 on 2008-11-07
You can see your current version and kernel with:
```

lsb_release -a && uname -r

```

To install a 32-bit app on a 64-bit system:
Force install the application (**note it should have the .deb extension**):
```

sudo dpkg -i --force-all *packagename*.deb

```
Ensure you have the following library installed:
```

sudo aptitude install ia32-libs 

```
Try running the app. If it doesn't run because it needs a library/dependency, install an app called *getlibs*.
Here is a link about getlibs:
[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

---

### Post by jimi_hendrix on 2008-11-07
im getting ```
dpkg: operation requires read/write access to dpkg status area
```

---

### Post by Yellow Pasque on 2008-11-07
> mupen64....i unpacked it but i cd to the folder and do ./configure and there is no script...
The mupen site's package has a pre-compiled binary. You can execute it by changing to that directory and:
```
./mupen64
```

Use sudo dpkg

---

