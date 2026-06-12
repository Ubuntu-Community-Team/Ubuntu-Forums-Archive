---
title: "why my java  version doesn't change after I installed java6?"
date: 2008-09-01
forum: General Help
---

### Post by usfish on 2008-09-01
I use 

sudo apt-get install sun-java6-jdk 

but after that when I check java version by java -version, it is still 1.5.0; why is that?

when I try to install java6 again it returns the package has already be installed. 

Thank you!

---

### Post by S.A.A on 2008-09-01
You should remove java5 from your system..

---

### Post by porchrat on 2008-09-01
you need to type this:

```
sudo update-alternatives --config java
```

to change the JRE

and then:

```
sudo update-alternatives --config javac
```

to change the javac

Just select 1.6 using the numbers when you're shown the selection menu

hope that helps

---

