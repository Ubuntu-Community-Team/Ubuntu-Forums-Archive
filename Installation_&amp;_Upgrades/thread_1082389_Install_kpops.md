---
title: "Install kpops"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by maGot on 2009-02-27
Hi, i dont know how to install kpops on gnome ubuntu 8.10 64-bit. I have read the readme file but that didn't do it for me. =)

Please help.

---

### Post by cariboo on 2009-02-27
Extract the file somewhere, preferably create a directory in your home directory. Open an Applications-->Accessories-->Terminal and cd into the directory you just extracted the files to. Make  sure you have the depends mentioned in the README. Then make inst.sh executeable:

```
chmod +x inst.sh
```

then run the file:

```
sudo ./inst.sh
```

Jim

---

### Post by maGot on 2009-02-28
Hello, thanks for the answer!

When i do the:
```
sudo ./inst.sh
```

I get a error message popin upp "Error making copstation"

What is that?

In the kpops folder there is a folder named "kpops/psptools/copstation-2.21"

---

### Post by maGot on 2009-03-05
Yes? No one? :(

---

### Post by martrn on 2009-03-05
Ensure you install all the dependincies etc.. etc.. eg 

sudo apt-get install kommander
sudo apt-get install pdftk
sudo apt-get install cdrdao

Make sure the make file builds ok eg.  Lokk at the inst.sh file and ensure the $1 variable makes sense.   Look at particular the directories and ensure you input a correct $1 or $2 depending on the file.  The $1 and $2 are the first argument after entering ./inst.sh

eg typeing     ./inst.sh first second

then $1 would be first 
and $2 would be second.

If you get an error number the error on the console should point to a line number.  And you need the line (number and code of it).

type ```
sudo gedit inst.sh
```
to view the install script.

---

