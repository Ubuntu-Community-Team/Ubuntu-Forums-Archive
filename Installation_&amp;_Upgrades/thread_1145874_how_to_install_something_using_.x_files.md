---
title: "how to install something using .x files"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by DeusExM1 on 2009-05-02
Hey everyone,

I was trying to install a program and the main file is "executable (application/x-executable)" as described when i right clicked it. I was wondering how to open such files? I have tried without success several options as i saw on the net but nothing worked so far.

Dom

---

### Post by RedSingularity on 2009-05-02
Is it a windows type .exe file?  If so you cant open it in linux without using something like WINE.

---

### Post by DeusExM1 on 2009-05-02
it is a .x executable file, not exe. the line that i wrote in parentheses is exactly what ubuntu says when i view properties of that file.

---

### Post by DeusExM1 on 2009-05-02
bump =]

---

### Post by taurus on 2009-05-02
Where is that file located?  Open a terminal and change to that directory.  Then, post the output of this command, replacing filename with the actual name of that file.

Applications -> Accessories -> Terminal
```
file filename
```

---

### Post by DeusExM1 on 2009-05-02
The output says:

inst.linux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.0.0, not stripped
domce@V1500:~/Desktop/Theocracy/linux$

---

### Post by taurus on 2009-05-02
Make sure it has an executable permission first before you run it.

```
chmod 755 filename.x
./filename.x
-or-
sudo ./filename.x  [COLOR="Blue"]<-- If you need root privilege.[/COLOR]
```

---

### Post by DeusExM1 on 2009-05-02
that seems to have worked. The program installed, but the terminal then asked this:


Where is your sound card ? [/dev/dsp]

---

