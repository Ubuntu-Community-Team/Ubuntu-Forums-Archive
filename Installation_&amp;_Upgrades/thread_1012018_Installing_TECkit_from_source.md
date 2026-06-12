---
title: "Installing TECkit from source"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by wilson47 on 2008-12-15
Hello Everyone,
I am trying to install TECkit (again) and I am getting the same problem that I got last time. This is even on a clean install of 8.10, so something might be wrong on TECkit's side. 

The problem is very simple (and I haven't ever compiled from source before, so sorry): when I go to do 
```
./compile
```
it tells me 
```
bash: ./compile: Permission denied

```.

Here are the permissions on the file:
```
-rw-r--r--  1 glen glen 723254 2008-04-07 16:21 configure

```.
Shouldn't it look like:
```
-rwxr-xr-x 1 glen glen 521 2008-09-11 20:00 playlist_function

```?

As I wasn't able to do this last time even when I changed the permissions, I just want to double check everything. 

Thanks for your help!

Glen

---

### Post by wilson47 on 2008-12-15
Well, I gave in and changed the permissions of the configure file. It actually worked this time, but I am pretty sure one should not have to mess with the permissions!

---

