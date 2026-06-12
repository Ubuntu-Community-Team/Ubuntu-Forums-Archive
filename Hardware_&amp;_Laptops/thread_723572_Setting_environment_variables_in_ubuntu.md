---
title: "Setting environment variables in ubuntu"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by ubuntoexpert on 2008-03-13
I'm trying to permanently set some environment variables in ubuntu.  I want to set CPATH and LD_LIBRARY_PATH.  So, I go to /etc/profile and add in the following commands:

export CPATH="/mypath"
export LD_LIBRARY_PATH = "/mypath"

I restart Linux, and when I type echo $CPATH on the bash terminal, my specified path does not appear.  The variable is empty.

So, I have to keep typing export CPATH="/mypath" everytime I open up a bash window.  How do I set these variables permanently? 

Thanks.

---

### Post by Rocket2DMn on 2008-03-13
Try add those lines to your .bashrc file in your home directory - this will set them for your specific user and are activated when you open a terminal (for that session).  After you make the change run
```
source .bashrc
```

---

### Post by ubuntoexpert on 2008-03-15
> **Rocket2DMn said:**
> Try add those lines to your .bashrc file in your home directory - this will set them for your specific user and are activated when you open a terminal (for that session).  After you make the change run
```
source .bashrc
```
thank u very much
it works :)

---

