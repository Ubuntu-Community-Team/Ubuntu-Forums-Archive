---
title: "Mono References Needed!"
date: 2008-10-15
forum: General Help
---

### Post by LeonBlade on 2008-10-15
Hello everyone,

I'm trying to make an Instant Messenger program with C++ and Mono.
Everything is working fine except I don't have the references for the following:

```

System.Net.Sockets
System.ComponentModel

```

Can anyone tell me how I can get these?

Thanks,
--LeonBlade

---

### Post by directhex on 2008-10-16
> **LeonBlade said:**
> Hello everyone,

I'm trying to make an Instant Messenger program with C++ and Mono.
Everything is working fine except I don't have the references for the following:

```

System.Net.Sockets
System.ComponentModel

```

Can anyone tell me how I can get these?

Thanks,
--LeonBlade

You have monodoc installed? If those bits are missing, then it sounds like you just need a newer monodoc (I see them here with 1.9)

Consider also taking a peek at the source for [http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

---

### Post by LeonBlade on 2008-10-16
Thanks, I'm installing monodoc now.

I used:
```
sudo apt-get install monodoc
```
That's correct right?

---

### Post by directhex on 2008-10-17
> **LeonBlade said:**
> Thanks, I'm installing monodoc now.

I used:
```
sudo apt-get install monodoc
```
That's correct right?

Right. That should pull in the documentation viewer, and the package with actual docs (monodoc-manual)

---

