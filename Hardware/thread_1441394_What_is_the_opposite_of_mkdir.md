---
title: "What is the opposite of mkdir?"
date: 2010-03-28
forum: Hardware
---

### Post by hihihi100 on 2010-03-28
Hi there:

I recently created, via terminal, a new folder named "old", but now is not needed anymore. If I created it with:

```
hihihi100@hihihi100-laptop:/media/Volume 1$ sudo mkdir ./old
```what do I have to type to delete the folder?

Cheers

---

### Post by techstop on 2010-03-28
I believe 'rmdir' will do what you want.

---

### Post by roger_1960 on 2010-03-28
Hi

Use rmdir.  Have a look at > man rmdir before you use it.

---

### Post by hihihi100 on 2010-03-29
That seems to work, but Im gonna need more help:

```
hihihi100@hihihi100-laptop:~$ cd /media/Volume\ 1
hihihi100@hihihi100-laptop:/media/Volume 1$ sudo rmdir ./old
[sudo] password for hihihi100: 
rmdir: failed to remove `./old': _Directory not empty_
hihihi100@hihihi100-laptop:/media/Volume 1$ 

```Directory not empty: I have accessed the Volume \1 as I would access any external hard drive (mount, click on the icon), and tried to delete all the content of the folder, even right clicking on it to change its permissions, to not avail I always get:

```
Cannot move file to trash, do you want to delete immediately?
The file "hihihi100" cannot be moved to the trash.
details:
Unable to trash file: Permission denied
```Help please

OK, it seems my question has to do with ```
--ignore-fail-on-non-empty

              ignore each failure that is solely because a directory

              is non-empty

```

But I dont know what to type

So, help please...

cheers

---

### Post by IcarusR on 2010-03-29
> OK, it seems my question has to do with

```
--ignore-fail-on-non-empty

              ignore each failure that is solely because a directory

              is non-empty
```


But I dont know what to type

Try this

```
sudo rmdir --ignore-fail-on-non-empty ./old
```

---

### Post by hihihi100 on 2010-03-29
I think that didnt work either:

```
hihihi100@hihihi100-laptop:~$ cd /media/Volume\ 1
hihihi100@hihihi100-laptop:/media/Volume 1$ sudo rmdir --ignore-fail-on-non-empty ./old
[sudo] password for hihihi100: 
hihihi100@hihihi100-laptop:
```

I was prompted to type my password, but nothing happened, I can still see the non needed folder..

---

### Post by hihihi100 on 2010-03-29
Well, it wasnt that difficult after all, but not via terminal:

I just opened the folder as administrator and deleted it

Cya

---

