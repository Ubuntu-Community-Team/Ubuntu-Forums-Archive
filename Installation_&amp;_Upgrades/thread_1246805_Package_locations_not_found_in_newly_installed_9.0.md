---
title: "Package locations not found in newly installed 9.04"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by Arndt on 2009-08-22
I have just installed Jaunty Jackalope (9.04) on my laptop, from a CD which I burned on another computer. This works fine, as far as it goes, it's what I'm using right now. Now I'd like to install Java, but the synaptic package manager doesn't find any such package. /etc/apt/sources.list doesn't seem to miss anything, but I'm not an expert. The update manager has already detected and successfully installed new updates for existing software, so it does find some repositories.

How do I make the package manager find Java?

---

### Post by Partyboi2 on 2009-08-22
Hi, open a terminal (Applications>Accessories>Terminal) and try installing it with
```
sudo apt-get install openjdk-6-jre 
``` or
```
sudo apt-get install sun-java6-bin
``` depending on which one you want. If it can not install the package, could you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by Arndt on 2009-08-22
> **Partyboi2 said:**
> Hi, open a terminal (Applications>Accessories>Terminal) and try installing it with
```
sudo apt-get install openjdk-6-jre 
``` or
```
sudo apt-get install sun-java6-bin
``` depending on which one you want. If it can not install the package, could you post your sources.list
```
cat /etc/apt/sources.list
```

Thank you, this worked. And now synaptic shows me a whole lot of packages if I query it for "java", not just the ones I fetched. Strange, but problem solved.

---

