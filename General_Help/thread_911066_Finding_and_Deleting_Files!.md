---
title: "Finding and Deleting Files!"
date: 2008-09-05
forum: General Help
---

### Post by tsoul on 2008-09-05
Could anybody please help me I have this file been created when a none privileged user tries to delete a file this file have no extension I can not handle going through so many files daily cleaning them manually. Is there a way where I can search for this files and remove them automatically..  file names are somewhat of this format.. 0E059100 no extension..

Thank you..

---

### Post by Crafty Kisses on 2008-09-05
Have you tried the search option in Ubuntu, go to the home folder and it should be there.

---

### Post by tsoul on 2008-09-05
> **Codename said:**
> Have you tried the search option in Ubuntu, go to the home folder and it should be there.

No I need to to be done by bash, I do not have any GUI! its a FILE SHARING SERVER!

---

### Post by orpheus07 on 2008-09-05
you can try using find.

find / -name 0E059100

---

### Post by tsoul on 2008-09-05
> **orpheus07 said:**
> you can try using find.

find / -name 0E059100

That will not work as I only gave an example as to what format the file names are created in but they are all random generated!

---

### Post by orpheus07 on 2008-09-05
tsoul, if you know the user name, you can use find's *-user* option

---

### Post by tsoul on 2008-09-05
> **orpheus07 said:**
> tsoul, if you know the user name, you can use find's *-user* option

No unfortunately we have many users and allot of them use the file server so that would not work.. is there a way to execute a bash or construct command to look for files without extension.

---

### Post by orpheus07 on 2008-09-05
hmmmm.... you can try this:

find your/path/ -type f | grep -v "\."

---

### Post by tsoul on 2008-09-05
> **orpheus07 said:**
> hmmmm.... you can try this:

find your/path/ -type f | grep -v "\."

ok that seems to work now how do I add rm -ri to this ?

---

### Post by orpheus07 on 2008-09-05
> **tsoul said:**
> ok that seems to work now how do I add rm -ri to this ?

you can use xargs, followed by rm. 

```
find your/path/ -type f | grep -v "\." | xargs rm
```

note that this will delete the files and there's no way to recover it. maybe you can move it to a temporary directory?

---

### Post by kpkeerthi on 2008-09-05
-- never mind. bad post. sorry --

---

### Post by tsoul on 2008-09-05
> **orpheus07 said:**
> you can use xargs, followed by rm. 

```
find your/path/ -type f | grep -v "\." | xargs rm
```

note that this will delete the files and there's no way to recover it. maybe you can move it to a temporary directory?

it says unterminated quote! ?

---

### Post by CrusaderAD on 2008-09-05
I find it easier to have a GUI installed:

sudo apt-get install ubuntu-desktop

Then run 

sudo nautilus

and delete whatever you want.

---

### Post by tsoul on 2008-09-05
> **raptormanad said:**
> I find it easier to have a GUI installed:

sudo apt-get install ubuntu-desktop

Then run 

sudo nautilus

and delete whatever you want.

Thank you for sharing that with me but I would not install Gnome just so I can do this.. any ideas would be greatly appreciated.

---

### Post by orpheus07 on 2008-09-05
tsoul, can you post the exact commands that you used, and the exact error also.

---

### Post by tsoul on 2008-09-06
> **orpheus07 said:**
> tsoul, can you post the exact commands that you used, and the exact error also.

find /Groups/* -type f | grep -v "\." | xargs rm
is the command I used

and it returns
unterminated quote

---

### Post by orpheus07 on 2008-09-06
> **tsoul said:**
> find /Groups/* -type f | grep -v "\." | xargs rm
is the command I used

and it returns
unterminated quote

it could be one of the files have a quote, you can try this:

```
find /Groups/* -type f -print0 | grep -v "\." | xargs rm
```

---

### Post by ghostdog74 on 2008-09-06
```

find . -type f ! -name "*.*" -exec  rm -f {} \;

```

---

### Post by tsoul on 2008-09-09
> **ghostdog74 said:**
> ```

find . -type f ! -name "*.*" -exec  rm -f {} \;

```

Thank you so much. I have been around this command for so long and it was as simple as *.*, what dose the ! after file type do ?

Thank you again!

---

### Post by ghostdog74 on 2008-09-09
> **tsoul said:**
> Thank you so much. I have been around this command for so long and it was as simple as *.*, what dose the ! after file type do ?

Thank you again!

! = negation. ! -name "*.*" means any file not with extension.

---

### Post by tsoul on 2008-09-09
> **ghostdog74 said:**
> ! = negation. ! -name "*.*" means any file not with extension.

ohh ok cheers for that m8,,,, saved my life right there..

Thank you

---

