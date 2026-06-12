---
title: "Need source code for &quot;beep&quot; program"
date: 2008-08-06
forum: General Help
---

### Post by diamond on 2008-08-06
There is a little program called "beep" in the repositories that, as the name suggests, makes the PC speaker beep.

I'm trying to replicate this functionality in a C++ program, and I can't seem to do it. I've tried

```
printf("%c",7)
```

And

```
printf("\a")
```

But nothing happens. However, "beep" works just fine on the same system. I'd like to look at the program's source code to figure out how they do it, but I can't seem to find it anywhere.

Anybody have any idea where I might look to find the source code for "beep"?

---

### Post by FakeOutdoorsman on 2008-08-06
I got the source code with:
```
sudo apt-get source beep
```
I had souce code enabled in my repo.

---

### Post by geirha on 2008-08-06
Odd. This works for me ...
```
gcc -x c - <<< "main(){putchar('\a');}" && ./a.out
```

---

### Post by Dr Small on 2008-08-06
This should be the source code:
[http://ftp.debian.org/debian/pool/main/b/beep/beep_1.2.2.orig.tar.gz](http://ftp.debian.org/debian/pool/main/b/beep/beep_1.2.2.orig.tar.gz)

---

