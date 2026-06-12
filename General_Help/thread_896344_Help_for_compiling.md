---
title: "Help for compiling"
date: 2008-08-21
forum: General Help
---

### Post by JUMmi on 2008-08-21
Hi everyone,

would You kindly give advice for this general question...

Which packages are needed to be (at least) installed for compiling from source code?
What is the difference between g++ and g++-4.2?

(KUbuntu 8.04)

Thank's already!

---

### Post by fahadsadah on 2008-08-21
Hi JUMmi, and welcome to the forums!

gcc points to the latest gcc, g++ points to the latest g++

Usually, you don't install these packages directly. Instead, you install build-essential, which contains these packages and more neccessary for compiling ```
sudo aptitude install build-essential
```

---

### Post by iaculallad on 2008-08-21
> **JUMmi said:**
> Hi everyone,

would You kindly give advice for this general question...

Which packages are needed to be (at least) installed for compiling from source code?
What is the difference between g++ and g++-4.2?

(KUbuntu 8.04)

Thank's already!

You will be needing the essential files:

```
sudo apt-get install build-essential
```

For the difference of the two: Try reading it at [http://gcc.gnu.org/](http://gcc.gnu.org/)

---

