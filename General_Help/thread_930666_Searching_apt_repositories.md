---
title: "Searching apt repositories"
date: 2008-09-26
forum: General Help
---

### Post by slacker9876 on 2008-09-26
Hello! I am trying to search the apt repositories configured on my desktop for a specific package. Since it may solve the problem to know the name, I am looking to install perl-DBI. I am running the x86_64 kernel. I reviewed the man file for apt-get and sis not see a search function or cli parameter listed in the man file or the referenced man docs.

Thanks in advance.

---

### Post by russlar on 2008-09-26
Have you tried to use the Synaptic Package Manager GUI? Or is this on a GUI-less system?

---

### Post by aloshbennett on 2008-09-26
Are you looking for "apt-cache search perl dbi" ?

---

### Post by Nepherte on 2008-09-26
```
apt-cache search <yoursearchtermhere>
```
or
```
aptitude search <yoursearchtermhere>
```

---

### Post by slacker9876 on 2008-09-26
I am looking to search for the package with a wildcard variable.  I was not aware of the apt-cache command ... I'll look into this.

I have used synaptic ask my package manager, but I am logged in over ssh, so I cannot use it from this location.

---

