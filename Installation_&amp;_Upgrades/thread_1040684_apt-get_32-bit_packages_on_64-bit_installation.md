---
title: "apt-get 32-bit packages on 64-bit installation?"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by ejain on 2009-01-15
In order to make use of more than (or equal to?) 4GB of physical memory, a 64-bit Ubuntu install seems to be required. But having done so, is it still possible to get the 32-bit versions of certain packages when installing them via apt-get? For example, if you don't intend to give more than 4GB of memory to any single Java process, it makes sense to install a 32-bit JVM (given that Sun hasn't implemented pointer compression yet). Suggestions (apart from bypassing Ubuntu's package management system)?

---

### Post by Lennon V C on 2010-04-19
Bump/Necro
I also want to know.

---

### Post by wafflemelon on 2010-06-19
An Corp.

I also need this.

---

### Post by oldos2er on 2010-06-19
You can download the 32-bit packages you need from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Then install them with ```
sudo dpkg -i --force-architecture <package> 
```
You might need to install ia32-libs too, if you haven't yet.

---

### Post by darondem on 2011-03-09
I have 64-bit 10.10 Ubuntu and also running 64-bit JDK. There's a option in java to run it in 32 bit mode *"java -d32*" but every time i try to use it, I get the message that says:

"This Java instance does not support a 32-bit JVM.
Please install the desired version."

I have installed all the ia32 libraries and also 32-bit jre (ia32-sun-java6.bin), but it didn't help. I still get the same message. How can I run my java programs in 32-bit mode?

---

