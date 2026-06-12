---
title: "&quot;apt-get install gcc-c++&quot; won't work in terminal"
date: 2008-11-29
forum: General Help
---

### Post by apease11 on 2008-11-29
I believe I have a configuration error with my terminal on my Debian x86_64 system.  When I try running "apt-get install gcc-c++" (without the quotes) the screen puts out:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-c

-------
It looks like the terminal isn't taking the ++ of c++, I'm pretty sure that is a configuration error.  Any help would be thanked, so thanks.

---

### Post by HoppingWombat on 2008-11-29
That's because the package name is g++ instead of gcc-c++

*sudo apt-get install g++*

:)

---

### Post by taurus on 2008-11-29
Wouldn't the build-essential package take care all of that?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by DGortze380 on 2008-11-29
g++ is included in gcc

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install gcc

or

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential

---

### Post by apease11 on 2008-11-30
Thanks, you all helped.

---

