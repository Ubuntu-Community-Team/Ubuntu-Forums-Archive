---
title: "error: no acceptable cc found in $PATH"
date: 2005-12-05
forum: General Help
---

### Post by omme on 2005-12-05
i got that error when i was installing tintin++v1.86b.tar.gz

i hope you guys could help me

---

### Post by Sutekh on 2005-12-05
It may help to be a little more explicit.  Still...

I assume that you are trying to configure and build tintin++v1.86b...

You will need to install the following package
```

sudo apt-get install build-essential

```
This will install the stuff you need for compiling programs.

---

### Post by omme on 2005-12-05
i downloaded tintin++ it is a mud client, sort of like telnet, it is used in playing online textbased mud.

i compiled it and it worked well.

but when i tried to configure it an error like this came out.

loading cache ./config.cache
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

---

### Post by Bachstelze on 2005-12-05
did you install the build-essentials package ? Also, you might need to install the gcc package.

---

### Post by omme on 2005-12-05
hmm how do you do that?

---

### Post by Bachstelze on 2005-12-05
open a terminal and run

```
sudo apt-get install build-essentials
```

---

### Post by omme on 2005-12-05
it says

E:couldn't find build essentials

---

### Post by Sutekh on 2005-12-05
```

sudo apt-get install build-essential

```

No "s"

---

### Post by mherring on 2005-12-05
First, check in synaptic to see if you have gcc installed.  If not, get it. ( thru synaptic)

If so, then search where it is installed (/usr/bin on my RHEL box)

Then, see if that directory is in your PATH:
     echo $PATH

If not, add it:
  export PATH=$PATH:<directory>      (<> = insert the pathname where you found gcc---eg:  /usr/bin

---

### Post by omme on 2005-12-05
ok thanks

---

