---
title: "why can't i compile anything!"
date: 2008-11-23
forum: General Help
---

### Post by coolethan on 2008-11-23
i don't have problems compiling specific programs at all but compiling anything in general. recently i tried compiling audacity from source and this happens.

ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ethan@Nertwab:~/Desktop/audacity-src-1.3.6$ 

this or something similar happens every single time.

---

### Post by ju2wheels on 2008-11-24
Do you have build-essential installed? The following should do it for most C/C++ compiling needs:

```

sudo apt-get install build-essential gcc libc6 g++ libstdc++6

```

---

### Post by vijay s on 2008-11-24
i too have the same problem.i don't have Internet Connection to my Home PC to use the above command.can we download it as a package and install them.

Vijay S

---

### Post by Yellow Pasque on 2008-11-24
Vijay, you can get build-essential and the dependencies as individual packages, but the easiest way to install it on a computer without an internet connection is to use the Ubuntu install CD.

---

### Post by coolethan on 2008-11-24
yes! thank god it is finally working but why aren't those things installed automatically when you install the OS in the first place?

---

### Post by oldos2er on 2008-11-24
> **coolethan said:**
> yes! thank god it is finally working but why aren't those things installed automatically when you install the OS in the first place?

 I'd love to know the answer to this question too; only the Ubuntu devs would know.

---

