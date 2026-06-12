---
title: "Max Ram supported by Ubuntu 8.04 32bits"
date: 2008-09-18
forum: General Help
---

### Post by hal1984 on 2008-09-18
Hello, how much is the size of the ram supported by Ubuntu 32 bits. It's 4 GB or 3 GB? I read that exits an compilation option in the kernel for allow to support larger size of RAMs...

Sorry my english.

---

### Post by ajmorris on 2008-09-18
hi there,
it is 4gb max on 32bit architecture. However, remember, some of that address space is reserved for other purposes, such as your video card memory, and so on. After all this, your OS will give you something around 3.25gb although it depends on your hardware.

AJ

---

### Post by iaculallad on 2008-09-18
For a complete technical detail explanation, try browsing this Ubuntu launchpad [thread]("https://answers.launchpad.net/ubuntu/+question/40205").

HTH.

---

### Post by starcannon on 2008-09-18
With a custom kernel 64gb of ram is possible on 32bit Linux; however, on a standard 32bit install of Ubuntu the limit is around 3.2gb. The 64bit version allows you to break the 4gb barrier without custom compiling a kernel.

GL and have fun.

---

### Post by ajmorris on 2008-09-18
> **starcannon said:**
> With a custom kernel 64gb of ram is possible on 32bit Linux; 

Only if you're running the 32bit Linux on 64bit hardware.

---

### Post by hal1984 on 2008-09-18
The hardware I plan to buy is a notebook with 4 GB of main RAM and a GPU up to 1024 MB via TurboCache (512 dedicated). Other option I have is the same notebook but with 3 GB of main RAM. In a default instalation of a 32 bits Linux OS perhaps it's a best buy the 3 GB of main RAM. Not?

The option of the Ubuntu 64 bits is recommendable by a notebook for desktop purposes ? Hardware drivers compatibility, desktop applications (not only free sofware) ...

---

### Post by ajmorris on 2008-09-18
> **hal1984 said:**
> The hardware I plan to buy is a notebook with 4 GB of main RAM and a GPU up to 1024 MB via TurboCache (512 dedicated). Other option I have is the same notebook but with 3 GB of main RAM. In a default instalation of a 32 bits Linux OS perhaps it's a best buy the 3 GB of main RAM. Not?

The option of the Ubuntu 64 bits is recommendable by a notebook for desktop purposes ? Hardware drivers compatibility, desktop applications (not only free sofware) ...

either would be fine... just depends on your price range ;)

---

### Post by mcduck on 2008-09-18
> **ajmorris said:**
> Only if you're running the 32bit Linux on 64bit hardware.
Not really true. Pretty much every x86-compatible CPU since Pentium Pro supports PAE.

---

### Post by ajmorris on 2008-09-18
> **mcduck said:**
> Not really true. Pretty much every x86-compatible CPU since Pentium Pro supports PAE.

oh kewl... im still living in the past it seems :P

---

### Post by iaculallad on 2008-09-18
Additional info excerpt from [Wiki]("http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux").

> The Linux kernel includes full PAE support starting with version 2.6, enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE.

---

