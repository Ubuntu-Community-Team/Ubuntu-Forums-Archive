---
title: "Linux Header"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by Word on 2006-07-07
I read everywhere and cant find the answer. I am trying to get VM ware install on my compaq r3000. Im using this sites instructions.
[http://www.abbeyworkshop.com/2006/06/04/ubuntu-vmware-install.html](http://www.abbeyworkshop.com/2006/06/04/ubuntu-vmware-install.html)

This the error I get. I tryed looking in synaptic. What am I doing wrong. Its a clean install everything else seems to word besides esd.
Couldn't find package linux-headers-2.6.15-25-386

---

### Post by mlind on 2006-07-07
try
```

sudo aptitude install linux-headers-$(uname -r)

```

This package is located in **main** repository.

---

### Post by Word on 2006-07-07
Couldn't find any package whose name or description matched "linux-headers-2.6.15-25-386"

i guess i dont have the repository listed can you give me the address

---

### Post by mlind on 2006-07-07
> **Word said:**
> Couldn't find any package whose name or description matched "linux-headers-2.6.15-25-386"

i guess i dont have the repository listed can you give me the address

Did you execute aptitude update first?

You should have main repository enabled by default.. Make sure your */etc/apt/sources.list* contains
```

deb http://archive.ubuntu.com/ubuntu dapper **main**
deb http://archive.ubuntu.com/ubuntu dapper-updates **main**
deb http://security.ubuntu.com/ubuntu dapper-security **main**

```

---

### Post by Word on 2006-07-07
thanks I got it.

---

