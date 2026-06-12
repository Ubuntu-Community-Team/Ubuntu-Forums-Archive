---
title: "[SOLVED] searching recursively with ls"
date: 2008-10-02
forum: General Help
---

### Post by motoperpetuo on 2008-10-02
is there a way to search through the file system recursively with ls and see the directory in which the results reside?

for example, if i type the following command:

    ls -lhR

i get a list of all the files in my present working directory and below it, with a separate header for each subdirectory.

if i try:

    ls -lhR|grep ubuntu

i get a list of every file in my present working directory and below that has "ubuntu" in its filename, i just don't have any indication of what subdirectory the files are in. if i could get that, it would be perfect.

also, when i'm pasting shell commands into posts in this forum, how do i get those neat little boxes around the commands so that my posts look better than this one?

---

### Post by Muflon on 2008-10-02
Try find

```

find . -name *ubuntu* -print
```

or locate

```

locate ubuntu
```

Muflon

---

### Post by Yuki_Nagato on 2008-10-02
Those neat little boxes are as follows, without the period in them.

[.CODE] System commands and such [./CODE]

or

[.PHP] Your bugged up code that we will debug for free [./PHP]

The PHP one colorizes it, making it easy for debuggers to read.  But CODE just makes it nice and neat if all you are posting are familiar commands and such.

---

### Post by motoperpetuo on 2008-10-02
sweet. i'm at work now, with only windows available, but i'll try the find option when i get home.

i actually knew about find from a short "introduction to linux" type training i had at another job, but i always used it like this:

```
find / -name 'ubuntu'
```

which always seemed to search from root. i'm guessing that using the dot instead of the forward slash means "search from the present working directory"?

---

### Post by OffAxis on 2008-10-02
> i'm guessing that using the dot instead of the forward slash means "search from the present working directory"? 

you'd be correct.

---

### Post by Muflon on 2008-10-02
> **motoperpetuo said:**
> i always used it like this:

```
find / -name 'ubuntu'
```

which always seemed to search from root. i'm guessing that using the dot instead of the forward slash means "search from the present working directory"?

Spot on!

try 

```
man find
```

to get the manual page for find, with all the options explained.

Muflon

---

### Post by OffAxis on 2008-10-20
I think the community docs are a little easier to understand.


[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

---

