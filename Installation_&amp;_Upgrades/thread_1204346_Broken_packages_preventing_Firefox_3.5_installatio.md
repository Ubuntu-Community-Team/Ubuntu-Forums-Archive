---
title: "Broken packages preventing Firefox 3.5 installation"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by ihendley on 2009-07-04
Hi,

I am running Ubuntu 9.04 64-bit, and I am having trouble installing Firefox 3.5. 

When I run:

```
$ sudo apt-get install firefox-3.5
```

I get the following error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  firefox-3.5: Depends: xulrunner-1.9.1 (>= 1.9.1) but it is not going to be installed
               Depends: libgtk2.0-0 (>= 2.17.0) but 2.16.1-0ubuntu2 is to be installed
E: Broken packages
```

I am not sure how to proceed. Any help in fixing this problem would be appreciated!

---

### Post by mikewhatever on 2009-07-04
Try running **sudo apt-get install -f**, there is also a gui way.
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by JoeNZ on 2009-07-04
I have just used Ubuntuzilla to install Firefox 3.5 and that worked good as gold.

[http://ubuntuzilla.wiki.sourceforge.net]("http://ubuntuzilla.wiki.sourceforge.net/#tochome6")

---

### Post by ihendley on 2009-07-05
> **mikewhatever said:**
> Try running **sudo apt-get install -f**, there is also a gui way.
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

Awesome. I didn't know it was that easy!

---

