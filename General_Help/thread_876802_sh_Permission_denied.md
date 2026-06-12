---
title: "sh: Permission denied"
date: 2008-08-01
forum: General Help
---

### Post by AkiraBergman on 2008-08-01
I am trying to learn a music program called athenaCL. It creates audio, midi and graphics files and it can apparently also play/show them by invoking the shell. But the shell gives Permission denied.

I installed the package on 8.04 by using the python setup install command and it had no installation problems. Many things also work well apart from the play and show functions.

How do you get the shell give execution permission to an application for playing/showing files that itself creates?

---

### Post by iaculallad on 2008-08-01
Try to insert gksudo before the command when in terminal:

```
gksudo athenaCL
```

---

### Post by AkiraBergman on 2008-08-01
The terminal hangs with gksudo. With sudo it still denies permission.

---

### Post by iaculallad on 2008-08-01
> **AkiraBergman said:**
> The terminal hangs with gksudo. With sudo it still denies permission.

Had you tried using gksu?

---

### Post by ilrudie on 2008-08-01
Try ```
chmod u+x <file you are trying to execute>
```Sometimes file permissions like that get lost during unpacking or perhaps the people who wrote the install script overlooked it.

---

### Post by caljohnsmith on 2008-08-01
> **iaculallad said:**
> Had you tried using gksu?
```
john@TECH5321:~$ ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2008-06-10 12:12 /usr/bin/gksudo -> gksu
```
gksudo and gksu are actually identical--gksudo is merely a symbolic link to gksu. :)

---

### Post by AkiraBergman on 2008-08-01
But these files are created by the program itself. They do not exist before execution. Maybe I have to look at the scripts to see if it creates them alright. But this program has been around for a while. Such a mistake is not probable.

---

### Post by AkiraBergman on 2008-08-01
I found a link;

[http://sourceforge.net/mailarchive/message.php?msg_name=1154315545.5137.4.camel%40localhost](http://sourceforge.net/mailarchive/message.php?msg_name=1154315545.5137.4.camel%40localhost)

The author replies a related question;

"if you still cant get this to work, it might be a windowing/non-
windowing issue. this happens sometimes on macos x; not sure if its
the same on ubuntu. the problem happens when a command-line app tries
to open a windowed app; the python 'pythonw' command takes care of
this. if you have a pythonw command, try this:

1. redo the setup.py procedure: cd into the athenaCL dir, and enter
this at the prompt:

% pythonw setup.py tool

2. then retry the athenacl command and see if that helps."

Then the problem seems to be between command line and windowing environment. Is there a corresponding command in Ubuntu to pythonw mentioned above? I tried "python setup.py tool" to install only the command line facilities, but it did not solve the permission problem.

---

### Post by iaculallad on 2008-08-04
> **caljohnsmith said:**
> ```
john@TECH5321:~$ ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2008-06-10 12:12 /usr/bin/gksudo -> gksu
```
gksudo and gksu are actually identical--gksudo is merely a symbolic link to gksu. :)

My error :) Both command could perform the same task as getting a privilege.

---

