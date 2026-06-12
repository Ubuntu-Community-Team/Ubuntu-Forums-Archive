---
title: "Gcc"
date: 2008-07-25
forum: General Help
---

### Post by meatrun on 2008-07-25
I was wondering if the most updated form of GCC comes with Ubuntu 8.4?

---

### Post by cprofitt on 2008-07-25
The GCC I have installed (by default) is 4.2.3 - I am not sure if that is the most recent.

---

### Post by ibutho on 2008-07-25
The most recent release of gcc is 4.3.1.

---

### Post by meatrun on 2008-07-25
i wonder if that is why i get checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

---

### Post by oldos2er on 2008-07-25
> **meatrun said:**
> i wonder if that is why i get checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

 You need to install the package "build-essential"

---

### Post by ibutho on 2008-07-25
> **meatrun said:**
> i wonder if that is why i get checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

That error means that you do not have all the necessary libraries required for gcc to work correctly. Install the build-essential package as suggested above.

---

