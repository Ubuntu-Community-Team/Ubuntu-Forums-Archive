---
title: "Changing root's $PATH variable"
date: 2008-11-02
forum: General Help
---

### Post by LordKelvan on 2008-11-02
Hi:

I have a program that I wanted to add to the $PATH environment variable.  Now, I've done it successfully for regular users, but unfortunately when I prepend sudo in front of it (to run it as root), I get 
```
"sudo: myapp: command not found"
```
where myapp is the name of the program.  I have read around and tried various solutions, but nothing seems to work:

[LIST=1]
[*]Adding "export PATH=$PATH:path_to_myapp" to /root/.bashrc
[*]Adding "export PATH=$PATH:path_to_myapp" to /root/bash_profile
[*]Appending path_to_myapp to both ENV_SUPATH and ENV_PATH in /etc/login.defs
[/LIST]

I tried each solution in isolation (i.e., I tried approach #1, then reversed my changes and tried approach #2, etc.), and also logged-out/logged-back-in after each approach.  

I know they don't work because when I type
```
sudo env
```
the $PATH variable does not reflect my changes.

I would appreciate any help on this matter.

Cheers,
LK

---

### Post by taurus on 2008-11-02
After you add it to /root/.bashrc, you need to rehash it with

```
sudo source /root/.bashrc
```

---

### Post by LordKelvan on 2008-11-14
As I pointed out in my original post, I logged out, then logged back in after adding it to /root/.bashrc.  Is this not sufficient?

And I assume you are also saying that adding "export PATH=$PATH:path_to_myapp" to /root/.bashrc is the proper way to accomplish what I want?

************EDIT*******************

I tried the following steps again:

1) Added the line "export PATH=$PATH:path_to_myapp" to /root/.bashrc.
2) Logged out
3) Logged back in

And still it fails with "command not found" when I prepend sudo.

---

### Post by LordKelvan on 2008-11-21
Hi:

I've solved the problem - the solution is here [http://stackoverflow.com/questions/257616/sudo-changes-path-why]("http://stackoverflow.com/questions/257616/sudo-changes-path-why").

Basically, it appears there is a bug with sudo.  In Ubuntu, sudo is compiled with the flag "--with-secure-path", and the bug prevents you from stopping sudo from resetting $PATH.  The solution is to add
```
alias sudo='sudo env PATH=$PATH'

```
to ~/.bashrc.

If you would like further details, and some other possible solutions, please visit the above link.  Although I'm not affiliated with the site, I've increasingly found [http://www.stackoverflow.com]("http://www.stackoverflow.com") to be very useful in solving programming/computer-related problems.

Cheers,
LK

---

