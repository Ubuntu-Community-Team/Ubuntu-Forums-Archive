---
title: "can't install nvidia drivers"
date: 2008-08-01
forum: Hardware
---

### Post by aznduk on 2008-08-01
I recently installed ubuntu 8.04.
I tried installing nvidia drivers for my 6800 go.
In my hardware drivers, it shows something called nvidia_new (which I assume is my card) and it says it's enabled but not in use.
I tried installing the drivers by disabling and renabling, but it gives me a 404 when it tries to get the driver.

So I tried get the EnvyNG.  I have enabled all the repositories that it requires, and i run sudo apt-get install envyng-gtk, but it can't find the package at all.

any ideas?

---

### Post by overdrank on 2008-08-01
> **aznduk said:**
> I recently installed ubuntu 8.04.
I tried installing nvidia drivers for my 6800 go.
In my hardware drivers, it shows something called nvidia_new (which I assume is my card) and it says it's enabled but not in use.
I tried installing the drivers by disabling and renabling, but it gives me a 404 when it tries to get the driver.

So I tried get the EnvyNG.  I have enabled all the repositories that it requires, and i run sudo apt-get install envyng-gtk, but it can't find the package at all.

any ideas?

Hi and it is sounding like your repos are not enabled. Did you install via the alternate cd? Anyway under system, administration, software sources there you can make sure you repos are added.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by aznduk on 2008-08-01
the repositories are checked off and enabled.
does ne1 have the URI so I can check them off?

i installed ubuntu 8.04 from the iso file I downloaded from the main ubuntu website, which included the live version.

---

