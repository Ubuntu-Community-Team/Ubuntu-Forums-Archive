---
title: "[SOLVED] ./configure"
date: 2008-08-13
forum: General Help
---

### Post by mike941 on 2008-08-13
What does ./configure do or /configure? Lately i've been trying to learn the basics of all the bash install commands and this one shows up from time to time but i don't think it's used anymore, am i right?

---

### Post by lisati on 2008-08-13
./configure is used when you're setting up a package. Whether or not it's there depends on the package. The "./" tells bash to look in the current directory (usually skipped as a security precaution)

---

### Post by fwre01 on 2008-08-13
Its still used when compiling from source. As far as i understand it checks to make sure you have all the correct files and libraries you need to run the application.

....someone may correct me on this

---

### Post by ibutho on 2008-08-13
> **fwre01 said:**
> Its still used when compiling from source. As far as i understand it checks to make sure you have all the correct files and libraries you need to run the application.

....someone may correct me on this

You are correct. It also checks to see if you have the libraries required to build the application from source.

---

### Post by mcduck on 2008-08-13
It simply runs a script called "configure" in the current directory.

Programs distributed as source code often have this script and use it to, like the name suggests, do some configurations based on your system before you actually start compiling the source.

"./" tells bash to look for the file to run in the current directory. This is needed as th directory where you have dowloaded/extracted the source code usually isn't in your path, so bash wouldn't find it if you wouldn't specificly tell it that it's in the current dir.

---

