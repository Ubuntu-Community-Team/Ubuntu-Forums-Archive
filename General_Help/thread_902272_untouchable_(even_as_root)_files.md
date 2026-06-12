---
title: "untouchable (even as root) files"
date: 2008-08-27
forum: General Help
---

### Post by onlythetim on 2008-08-27
last night my laptop would not shut down, so I forced it off by holding the power button.  This morning, there were 5 files that I could not do anything with, even as root.
```

/home/_tim$ ls -la
ls: cannot access .dmrc: Permission denied
ls: cannot access .gtkpod: Permission denied
ls: cannot access .gtk-bookmarks: Permission denied
ls: cannot access .ICEauthority: Permission denied
ls: cannot access .recently-used.xbel: Permission denied
total 0
drwxr-xr-x 3 tim  tim  200 2008-08-27 06:50 .
drwxr-xr-x 8 root root 208 2008-08-27 07:00 ..
?????????? ? ?    ?      ?                ? .dmrc
?????????? ? ?    ?      ?                ? .gtk-bookmarks
?????????? ? ?    ?      ?                ? .gtkpod
?????????? ? ?    ?      ?                ? .ICEauthority
?????????? ? ?    ?      ?                ? .recently-used.xbel

```

Does anyone know what's going on here?  Is this the result of a corrupted filesystem?  And if so, how do I fix it?

---

### Post by iaculallad on 2008-08-27
Fix it with:

```
sudo chmod 644 /home/your_user_name/.dmrc
sudo chown your_user_name /home/your_user_name/.dmrc
sudo chmod -R 700 /home/your_user_name
sudo chown -R your_user_name /home/your_user_name
```

---

### Post by sameerds on 2008-08-27
But you don't seem to be logged in as root when trying those commands ... your prompt shows a dollar ($) sign ... default settings turn it into a hash (#) sign.

Anyway, with the kind of output you see, it would be a good idea to boot into single mode and run fsck on your filesystem.

---

### Post by onlythetim on 2008-08-27
even as root, none of those commands work.  Neither will rm or mv.

---

### Post by sameerds on 2008-08-27
> **iaculallad said:**
> Fix it with:

```
sudo chmod 644 /home/your_user_name/.dmrc
sudo chown your_user_name /home/your_user_name/.dmrc
sudo chmod -R 700 /home/your_user_name
sudo chown -R your_user_name /home/your_user_name
```

Using numerical codes for permissions is generally a bad idea. They don't accomplish exactly what you wanted. Take a look at the third command for example. "-R 700" means "give read, write and execute" permissions to *every* file and directory for the owner". That is definitely not the intended change. The command should instead be replaced by the following (note the upper-case X in the first command):

```

sudo chmod -R u+rwX ~username
sudo chmod -R og-rwx ~username

```

---

### Post by justleen on 2008-08-27
> **sameerds said:**
> Using numerical codes for permissions is generally a bad idea. They don't accomplish exactly what you wanted. Take a look at the third command for example. "-R 700" means "give read, write and execute" permissions to *every* file and directory for the owner". That is definitely not the intended change. The command should instead be replaced by the following (note the upper-case X in the first command):

```

sudo chmod -R u+rwX ~username
sudo chmod -R og-rwx ~username

```

errr.... your command are doing exactly the same!
the advantage of numrical over the letters is that you can specify verything in one line.. if "other" rights needs to be different then "group" rights, you need to issue two command / flags...

---

### Post by iaculallad on 2008-08-27
> **sameerds said:**
> Using numerical codes for permissions is generally a bad idea. They don't accomplish exactly what you wanted. Take a look at the third command for example. "-R 700" means "give read, write and execute" permissions to *every* file and directory for the owner". That is definitely not the intended change. The command should instead be replaced by the following (note the upper-case X in the first command):

```

sudo chmod -R u+rwX ~username
sudo chmod -R og-rwx ~username

```

The numerical value of 700 would just be a suggestion. The OP could change it to a value which could fit him/her best. And that could accomplish what the OP wanted. Using numeric is a flexible style for me, my choice. Anyways, using what you posted against using numeric codes would only do the same purpose.

---

### Post by sameerds on 2008-08-27
> **justleen said:**
> errr.... your command are doing exactly the same!
the advantage of numrical over the letters is that you can specify verything in one line.. if "other" rights needs to be different then "group" rights, you need to issue two command / flags...

> **iaculallad said:**
> The numerical value of 700 would just be a suggestion. The OP could change it to a value which could fit him/her best. And that could accomplish what the OP wanted. Using numeric is a flexible style for me, my choice. Anyways, using what you posted against using numeric codes would only do the same purpose.

It's not that simple. Like I said before, note the upper-case "X" in the commands I posted here. It's important. As in, don't-shoot-yourself-in-the-foot important. RTFM. That means "man chmod", which says the following about "X":

[INDENT]*execute/search only if the file is a directory or already has execute permission for some user*[/INDENT]

I hope it is clear why this is important. Using those ever-so-convenient numerical code would give execution rights to *every file*. And also, "chmod -R 700 /some/directory" will not work in a border case, which is when you have write permission because you belong to the owning group, but you are not the owner. It won't be able to descend into the directory, since it will first remove group execute permissions on that directory. Try it and see.

About doing everything in a single command, I can rewrite those earlier commands like so:

```
sudo chmod -R u+rwX,og-rwx ~username
```

But it is still *not* the same as using numeric permissions. Numeric permissions are bad, because they can do more than what was *intended*. Symbolic permissions ensure that you type exactly what you wanted, and nothing else.

---

### Post by sameerds on 2008-08-27
> **sameerds said:**
> And also, "chmod -R 700 /some/directory" will not work in a border case, which is when you have write permission because you belong to the owning group, but you are not the owner. It won't be able to descend into the directory, since it will first remove group execute permissions on that directory. Try it and see.

In fact here's a better border case:

```
sameerds@gajanan:~$ mkdir test
sameerds@gajanan:~$ touch test/inner
sameerds@gajanan:~$ chmod -R 600 test
chmod: cannot access `test/inner': Permission denied
sameerds@gajanan:~$ ls -l test/inner 
ls: cannot access test/inner: Permission denied
sameerds@gajanan:~$ ls -l test/
ls: cannot access test/inner: Permission denied
total 0
-????????? ? ? ? ?                ? inner
sameerds@gajanan:~$ ls -ld test/
drw------- 2 sameerds users 4096 2008-08-27 18:31 test/
sameerds@gajanan:~$ 

```

Now I think that maybe, just possibly, the original poster got into trouble because numeric permissions were used in some earlier session!

---

### Post by sameerds on 2008-08-27
> **onlythetim said:**
> even as root, none of those commands work.  Neither will rm or mv.

I assume that when you say "even as root", you mean "sudo whatever". Anyway, the output that you have pasted doesn't make any sense. Maybe I am missing something, but I think you should reboot into recovery mode and fsck that filesystem. Find the device name for that partition. It could either be a separate partition for /home, or the one for /. In either case, if /dev/sda2 is the device name, you need to run the following at the recovery prompt:

```
fsck /dev/sda2
```

Note that you won't need sudo, since the recovery prompt automatically logs you in as root.

---

