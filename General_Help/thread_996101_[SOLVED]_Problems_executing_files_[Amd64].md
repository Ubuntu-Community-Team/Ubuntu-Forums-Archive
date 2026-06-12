---
title: "[SOLVED] Problems executing files [Amd64]"
date: 2008-11-28
forum: General Help
---

### Post by GSMX on 2008-11-28
hey,

I have really strange problems with executing files.
For example: I downloaded the Adobe Air installer, chmod +x'd it and ran (while in the right dir) sudo ./adobeair.bin.
Then I get the following error message:
```
sudo: unable to execute ./adobeair.bin: File or directory doesn't exist

```

I tried the same with another executable file and that gave the same message.

Any ideas?

---

### Post by taurus on 2008-11-28
While you are in that directory, what's the output of this command?

```
ls -la
```

---

### Post by GSMX on 2008-11-28
what it is suppost to show :) : 
```

-rwxr-xr-x  1 user user 11080688 2008-11-26 21:17 adobeair.bin

```

---

### Post by taurus on 2008-11-28
```
file adobeair.bin
```

---

### Post by GSMX on 2008-11-28
```
$ file adobeair.bin 
adobeair.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
```

I see it says 32-bit, could that be the problem, if so, how could I install it anyway?

---

### Post by taurus on 2008-11-28
You need to install 32bit libraries first before you can run 32bit in 64bit environment.  

```
ldd adobeair.bin
```

---

### Post by GSMX on 2008-11-28
```
$ ldd adobeair.bin
 Not a dynamical executable file
```

But if I try a 64-bit app (realflow in this case), it doesn't work either:
```
sudo: unable to execute ./realflow: File or directory doesn't exist
```
```
$ file realflow
realflow: C shell script text executable
```
```
$ ldd realflow
 Not a dynamical executable file
```

---

### Post by taurus on 2008-11-28
If realflow is a C program, you first need to compile it and then run the binary a.out.

```
sudo apt-get update
sudo apt-get install build-essential
gcc realflow
./a.out
```

---

### Post by GSMX on 2008-11-28
ok, the realflow issue is solved, i looked over a realflow.bin in another dir
And Adobe Air issue solved, too

Thanks for that :)

But why the error "file doesn't exist" in both adobeair and realflow, while it was actually a case of dependencies?

---

